Scheme 对象的一个子集是*数据值(datum value)*。它们包括 *booleans*，数，字符，符号，字符串以及由这些数据组成的列表或者向量。每个*数据值*都可以使用文本形式表示为：*句法数据(syntactic data)*——它可以被不丢失信息的写出与读入。一个*数据值*可能有不止一种的*句法数据*表示方式。每个*数据值*都可以通过在其对应的*句法数据*前加上 `'` 前缀变为一个字面表达式：

> ```
> '23                      ==> 23
> '#t                      ==> #t
> 'foo                     ==> foo
> '(1 2 3)                 ==> (1 2 3)
> '#(1 2 3)                ==> #(1 2 3)
> ```

在表示数或者 boolean 对象时不需要添加 `'` 前缀。*句法数据* `foo` 表示一个名为 “foo” 的符号，`'foo` 是使用该符号的值表示的该符号的字面值。`(1 2 3)` 是一个列表元素为 `1`, `2`, `3` 的`句法数据`，`'(1 2 3)` 是使用这个列表的值表示的这个列表的字面值。同理，`#(1 2 3)` 一个元素为 `1`, `2`, `3` 的`句法数据`，`'#(1 2 3)` 是对应的字面值。

*句法数据*是 Scheme *句法形式*的超集。因此 Scheme *句法形式*可以使用*句法数据*对象来表示。特别的，符号可以用来表示标识符。

> ```
> '(+ 23 42)                   => (+ 23 42)
> '(define (f x) (+ x 42)      => (define (f x) (+ x 42))
> ```

这使得写操纵 Scheme 源代码的程序变得很容易，如写一个解释器或者*程序变换器(program transformers)*。
