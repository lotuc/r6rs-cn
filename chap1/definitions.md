使用**let**表达式绑定的变量是*本地的*， 因为这些绑定只在**let**的 body 部分可见。 Scheme 允许通过以下方式创建 top-level 绑定：

> `(define x 23)` <br/>
> `(define y 42)` <br/>
> `(+ x y)` ==> `65`

最开始的两个式子为*definitions*； 它们创建了 top-level 绑定， 将 `x` 绑定到 `23`， 将 `y` 绑定到 `42`。 *Definitions* 不是表达式（expressions）， 不是所有的使用 expressions 的地方都可以使用 *definitions*。 除了上面这些，还有一点： *definition* 没有值。

绑定遵从程序的语法结构： 当对于一个名字的多个绑定存在时， 变量将指向距其最近的绑定值， 按照从引用的位置开始从内到外的顺序， 如果没有找到本地绑定（local binding）， 使用 top-level 绑定。

> `(define x 23)` <br/>
> `(define x 42)` <br/>
> `(let ((y 43)) (+ x y))` ==> `66` <br/>
> `(let ((y 43)) (let ((y 44)) (+ x y)))` ==> `67`