`<Interlexeme space>` 可以出现在词素的任意一侧，但是不可以出现在词素内部。

`<Identifier>`、`.`、`<character>`、`<boolean>` 必须以 `<delimiter>` 结尾或者结束于输入结束处。

下面这两个字符保留，用于语言未来的扩展：`{`，`}`。

```
<lexeme>
    −→ <identifier> | <boolean> | <number>
        | <character> | <string>
        | ( | ) | [ | ] | #( | #vu8( | ’ | ` | , | ,@ | . | #’ | #` | #, | #,@
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
⟨constituent⟩
    −→ ⟨letter⟩
        | ⟨any character whose Unicode scalar value is greater than
            127, and whose category is Lu, Ll, Lt, Lm, Lo, Mn, Nl, No,
            Pd, Pc, Po, Sc, Sm, Sk, So, or Co⟩
⟨specialinitial⟩
    −→!|$|%|&|*|/|:|<|= |>|?|^|_|~
⟨subsequent⟩ 
    −→ ⟨initial⟩ | ⟨digit⟩
| ⟨any character whose category is Nd, Mc, or Me⟩ | ⟨special subsequent⟩
⟨digit⟩ 
    −→ 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 ⟨hex digit⟩ −→ ⟨digit⟩
|a|A|b|B|c|C|d|D|e|E|f|F ⟨special subsequent⟩ 
    −→ + | - | . | @
⟨inline hex escape⟩ 
    −→ \x⟨hex scalar value⟩;
⟨hex scalar value⟩ 
    −→ ⟨hex digit⟩+
⟨peculiar identifier⟩ 
    −→ + | - | ... | -> ⟨subsequent⟩* 
⟨boolean⟩ 
    −→ #t | #T | #f | #F
⟨character⟩ 
    −→ #\⟨any character⟩
        | #\⟨character name⟩
        | #\x⟨hex scalar value⟩
⟨character name⟩ 
    −→ nul | alarm | backspace | tab
        | linefeed | newline | vtab | page | return
        | esc | space | delete
⟨string⟩ 
    −→ " ⟨string element⟩* "
⟨string element⟩ 
    −→ ⟨any character other than " or \⟩
        | \a | \b | \t | \n | \v | \f | \r | \" | \\
        | \⟨intraline whitespace⟩⟨line ending⟩
⟨intraline whitespace⟩ | ⟨inline hex escape⟩
⟨intraline whitespace⟩ 
    −→ ⟨character tabulation⟩ | ⟨any character whose category is Zs⟩
```