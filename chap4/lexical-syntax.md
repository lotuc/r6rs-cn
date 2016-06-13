lexical语法定义字符序列如何被分割成词素，忽略了一些如注释和空字符(whitespace)这种不重要的部分。假设自字符序列为 Unicode 文本。一些在 lexical语法中的词素，诸如标识符、数对象的表示、字符串等，在datum语法中是**词法数据(syntactic data)**，即表示了对象。除了语法的正式定义之外，这一节还描述了这些词法数据表示的是什么数据值(datum value)。

lexical语法中描述注释的部分包含一些对 <datum> 的引用，它们在 datum语法中进行描述。这些注释中的 <datum> 在lexical语法中不是重头部分。

大小写是被区分的，除了这些情况：表示 boolean 值、数对象和使用十六进制数表示 unicode标量值时。例如 `#x1A` 和 `#X1a` 是等价的。而标识符 `Foo` 则区别于 `FOO`。

# 形式化描述

`<Interlexeme space>` 可以出现在词素的任意一侧，但是不可以出现在词素内部。

`<Identifier>`、`.`、`<character>`、`<boolean>` 必须以 `<delimiter>` 结尾或者结束于输入结束处。

下面这两个字符保留，用于语言未来的扩展：`{`，`}`。

```
<lexeme>
    −→ <identifier> | <boolean> | <number>
        | <character> | <string>
        | ( | ) | [ | ] | #( | #vu8( | ’ | ` | , | ,@ | . 
        | #’ | #` | #, | #,@

<delimiter>
    −→ ( | ) | [ | ] | " | ; | # | <whitespace>

<whitespace>
    −→ <character tabulation>
        | <linefeed> | <line tabulation> | <form feed>
        | <carriage return> | <next line>
        | <any character whose category is Zs, Zl, or Zp>

<line ending>
    −→ <linefeed> | <carriage return>
        | <carriage return> <linefeed> | <next line>
        | <carriage return> <next line> | <line separator>

<comment>
    −→ ; <all subsequent characters up to a <line ending> or <paragraph separator>>
        | <nested comment>
        | #; <interlexeme space> <datum> | #!r6rs

<nested comment>
    −→ #| <comment text> <comment cont>* |#

<comment text>
    −→ <character sequence not containing #| or |#>

<comment cont>
    −→ <nested comment> <comment text>

<atmosphere>
    −→ <whitespace> | <comment>

<interlexeme space>
    −→ <atmosphere>*

<identifier>
    −→ <initial> <subsequent>* | <peculiar identifier>

<initial>
    −→ <constituent> | <special initial> | <inline hex escape>

<letter>
    −→ a | b | c | ... | z | A | B | C | ... | Z

<constituent>
    −→ <letter>
        | <any character whose Unicode scalar value is greater than
            127, and whose category is Lu, Ll, Lt, Lm, Lo, Mn, Nl, No,
            Pd, Pc, Po, Sc, Sm, Sk, So, or Co>

<specialinitial>
    −→!|$|%|&|*|/|:|<|= |>|?|^|_|~

<subsequent> 
    −→ <initial> | <digit>
        | <any character whose category is Nd, Mc, or Me> | <special subsequent>

<digit> 
    −→ 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 

<hex digit> 
    −→ <digit>
        |a|A|b|B|c|C|d|D|e|E|f|F 

<special subsequent> 
    −→ + | - | . | @

<inline hex escape> 
    −→ \x<hex scalar value>;

<hex scalar value> 
    −→ <hex digit>+

<peculiar identifier> 
    −→ + | - | ... | -> <subsequent>* 

<boolean> 
    −→ #t | #T | #f | #F

<character> 
    −→ #\<any character>
        | #\<character name>
        | #\x<hex scalar value>

<character name> 
    −→ nul | alarm | backspace | tab
        | linefeed | newline | vtab | page | return
        | esc | space | delete

<string> 
    −→ " <string element>* "

<string element> 
    −→ <any character other than " or \>
        | \a | \b | \t | \n | \v | \f | \r | \" | \\
        | \<intraline whitespace><line ending>
            <intraline whitespace> 
        | <inline hex escape>

<intraline whitespace> 
    −→ <character tabulation> 
        | <any character whose category is Zs>
```

`<hex scalar value>` 表示一个 `0` 到 `#x10FFFF` 之间除去区间 `[#xD800,#xDFFF]` 的 Unicode 标量值。

下面的规则 `<num R>`、`<complex R>`、`<real R>`、`<ureal R>`、`<uinteger R>`和`<prefix R>` 对于 `R=2,8,10和16` 相同。按下面定义规则 `<decimal 2>`、`<decimal 8>`、`<decimal 16>`是不存在的，即包含指数部分的数的表示只能是基于十进制表示。

```
<number> 
    −→ <num 2> | <num 8> | <num 10> | <num 16>
<num R> 
    −→ <prefix R> <complex R>
<complex R> 
    −→ <real R> | <real R> @ <real R>
        | <realR> + <urealR> i | <realR> - <urealR> i 
        | <real R> + <naninf> i | <real R> - <naninf> i
        | <real R> + i | <real R> - i
        | + <urealR> i | - <urealR> i
        | + <naninf> i | - <naninf> i
        |+i|-i
<real R> 
    −→ <sign> <ureal R>
        | + <naninf> | - <naninf> <naninf> −→ nan.0 
        | inf.0 <ureal R> −→ <uinteger R>
        | <uinteger R> / <uinteger R>
        | <decimal R> <mantissa width> 
<decimal 10>
    −→ <uinteger 10> <suffix>
        |.<digit10>+ <suffix> |<digit10>+ .<digit10>*<suffix> 
        | <digit 10>+ . <suffix>
<uinteger R> 
    −→ <digit R>+
<prefix R> 
    −→ <radix R> <exactness>
        | <exactness> <radix R>
<suffix> 
    −→ <empty>
        | <exponent marker> <sign> <digit 10>+
<exponentmarker>
    −→ e|E|s|S|f|F |d|D|l|L
<mantissa width> 
    −→ <empty> | | <digit 10>+
<sign> 
    −→ <empty> | + | - <exactness> −→ <empty>
        | #i | #I | #e | #E
<radix 2> 
    −→ #b | #B
<radix 8>
    −→ #o | #O
<radix 10> 
    −→ <empty> | #d | #D
<radix 16> 
    −→ #x | #X
<digit 2> 
    −→ 0 | 1
<digit 8>
    −→ 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7
<digit 10>
    −→ <digit>
<digit 16>
    −→ <hex digit>
```

# 行尾

行尾对于单行注释和字符串字面值很重要。在 Scheme 源代码中，任何 `<line ending>` 中的行尾标记均作为行结束标记。另外，连字符 `<carriage return> <linefeed>` 和 `<carriage return> <next line>` 被认作一个行结束标记。

在字符串字面值中，一个不以 `\` 作为前缀的 `<line ending>` 标记表示一个换行符。

# 空字符(whitespace)和注释

空字符用于分割词素以增加代码可读性。空字符可以出现在任意两个词素之间，但不可以出现在一个词素中。空字符可以出现在字符串字面值中，这些空字符是字符串中有意义的字符。

lexical 语法包含若干注释形式。所有的注释对于 Scheme 来说都是不可见的，除非它们被用作分隔符号，例如出现在标识符中间或一个数的表示中间。

一个分号(;) 表示行注释的开始。注释内容从分号开始到行尾。

另一种表示注释的方式是给一个 `<datum>` 加上 `#;` 前缀，在该前缀和`<datum>`之间可能出现 `<interlexeme space>`。该种注释由 `#;` 前缀和对应的`<datum>`部分组成。这种表示法常用于"注释掉"一部分代码。

块注释可以使用合适嵌套的 `#|` 和 `#|` 对表示。

> ```
> #|
>     The FACT procedure computes the factorial
>     of a non-negative integer.
> |#
> (define fact
>     (lambda (n)
>         ;; base case
>         (if (= n 0)
>             #;(= n 1)
>             1          ; identity of *
>             (* n (fact (- n 1))))))
> ```

词素 `#!r6rs` 用于指明程序文本遵守本报告中的lexical语法和datum语法，也可被认为是注释。

# 标识符

大部分其它程序语言中合法的标识符在Scheme中也是合法的。一般来说，不能被解释成数字的由letters、数字和"extended alpabetic characters"组成的序列是合法的标识符。除此之外，`+`、`-`和`...`以及以`-->`开头的的由letters、数字和"extended alphabetic characters"组成的序列也是合法的标识符。下面是一些标识符的例子：

```
    lambda           q              soup
    list->vector     +              V17a
    <=               a34kTMNs       ->-
    the-word-recursion-has-many-meanings
```

"Extended alphabetic characters" 可以被当成letters一样使用。下面为"extended alphabetic characters"：

> `! $ % & * + - . / : < = > ? @ ^ _ ~`

