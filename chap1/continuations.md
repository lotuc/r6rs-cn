在任何 Scheme 表达式被计算的过程中总是有一个 *continuation* 等着该表达式的结果。 *Continuation* 表示了计算的整个（默认）未来。例如，非正式地说，表达式 `3` 在表达式

> `(+ 1 3)`

中的 *continuation* 是将 `1` 加到它上面。通常来说，这种无处不在的 *continuations* 是隐藏在幕后，对程序员不可见的，程序员也不会过多考虑它。但是在很少的一些情况下，程序员需要显式的处理 *continuations*。Scheme 中 名叫 `call-with-current-continuation` 的 *procedure* 允许程序员从当前 *contination* 处创建一个 *procedure*，之后还可以恢复。`call-with-continuation` 接受一个 *procedure*，然后立即传入一个参数调用该 *procedure*——传入的参数为 *escape procedure*。这个 *escape procedure* 之后可以接受一个参数被调用，其结果为 `call-with-continuation` 调用的结果。*escape procedure* 丢弃其自己的 *continuation*，然后重启了在调用 `call-with-continuation` 时挂起的那个 *continuation*。

在下面的例子中，*escape procedure* 表示 “加 `1` 到参数的*continutaion*” 被绑定到 `escape`，然后传入参数 `3`调用它。该调用 `escape` 的 *continuation* 被丢弃了，结果是 `3` 被传给了该 “加 `1` 到参数的*continuation*”：

> ```
> (+ 1 (call-with-current-continuation
>       (lambda (escape)
>         (+ 2 (escape 3)))))                   ==> 4
> ```
