Scheme 对象的一个子集是 *datum values*。它们包括 *booleans*，数，字符，符号，字符串以及由这些数据组成的列表或者向量。每个 *datum value* 都可以字面的表示形式：*syntactic datum*，可以不丢失信息对它进行写出与读入。一个 *datum value* 可能有不止一种 *syntactic data* 的写法。每个 *datum value* 都可以通过在程序中加上一个前缀`'`很容易的被转化为一个对应 *syntactic datum* 的字面表达式（literal expression）：

> ```
> '23                      ==> 23
> '#t                      ==> #t
> 'foo                     ==> foo
> '(1 2 3)                 ==> (1 2 3)
> '#(1 2 3)                ==> #(1 2 3)
> ```

在表示数或者 boolean 对象时不需要添加 `'` 前缀。*Syntactic datum* `foo` 表示一个名为 “foo” 的符号， `'foo` 是使用该符号的值表示的该符号的字面值。 `(1 2 3)` 是一个列表元素为 `1`, `2`, `3` 的 `syntactic datum`，`'(1 2 3)` 是使用这个列表的值表示的这个列表的字面值。同理，`#(1 2 3)` 一个元素为 `1`, `2`, `3` 的 `syntactic datum`，`'#(1 2 3)` 是对应的字面值。

*syntactic data* 是 Scheme *forms* 的超集。因此 Scheme *forms* 可以使用 *syntactic data* 对象来表示。特别的，一个符号可以用来表示标识符。

> ```
> '(+ 23 42)                   => (+ 23 42)
> '(define (f x) (+ x 42)      => (define (f x) (+ x 42))
> ```

这使得写操纵 Scheme 源代码的程序变得很容易，如写一个解释器或者 *program transformers*。
