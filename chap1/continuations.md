在任何 Scheme 表达式被计算的过程中总是有一个 *continuation* 等着该表达式的结果。*Continuation* 表示了计算的整个（默认）未来。例如，非正式地描述下面表达式中子表达式 `3`

> `(+ 1 3)`

的 *continuation* 是将 `1` 加到它上面。通常来说，这种无处不在的 *continuations* 是隐藏在幕后，对程序员不可见的，程序员也不会过多考虑它。但是在很少的一些情况下，程序员需要显式的处理 *continuations*。Scheme 中名叫 `call-with-current-continuation` 的*过程*允许程序员通过创建一个可以重启当前 *continuation* 的过程来显式地处理 *continuation*。`call-with-continuation` 接受一个*过程*，然后立即传入一个参数调用该*过程*——传入的参数为 *escape过程*。这个 *escape过程* 之后可以接受一个参数被调用，其结果为 `call-with-continuation` 调用的结果。*escape过程* 丢弃其自己的 *continuation*，然后重启了在调用 `call-with-continuation` 时挂起的那个 *continuation*。

在下面的例子中，*escape过程* 表示 “加 `1` 到参数的*continutaion*” 被绑定到 `escape`，然后传入参数 `3`调用它。调用 `escape` 的 *continuation* 被丢弃了，最终是 `3` 被传给了该 “加 `1` 到参数的*continuation*”（译者注：如果按正常流程，`(escape 3)`这个过程调用的 *continuation* 为将 “加`2`到参数的*continuation*”，但是 `escape` 是 `call-with-continuation`中的 *escape过程*，按照上面的描述，它的 *continuation* 被丢弃了，而传给它的参数被送给调用 `call-with-continuation` 时挂起的那个 *continuation* 了，及 “加`1`到参数的*continuation*” ，越描越黑，想了解的自己搜相关资料吧）：

> ```
> (+ 1 (call-with-current-continuation
>       (lambda (escape)
>         (+ 2 (escape 3)))))                   ==> 4
> ```
