*Definitions* 也可用来定义 *procedures*：

> `(define (f x) (+ x 42))`
>
> `(f 23)` ==> `65`

一个 *procedure* 是一个表达式， 在对象上面的一个简单抽象。 例如， 上面的 *definition* 定义了一个名为 `f` 的 *procedure*（注意 `f` `x` 两边的括号， 它指明了这是一个 *procedure* 定义）。表达式 `(f 23)` 是一个 `procedure` 调用， 意为， “在 `x` 绑定到 `23` 的情况下计算 `(+ x 42)`”。

由于 *procedures* 是对象， 它们可以作为参数传给其它 *procedures*：

> `(define (f x) (+ x 42))`
>
> `(define (g p x) (p x))`
>
> `(g f 23)` ==> 65

在这个例子中， `g` 的 body 部分计算过程中将 `p` 绑定到 `f` 同时将 `x` 绑定到 `23`， 它等同于计算 `(f 23)`， 结果为 `65`。

事实上， Scheme 很多预定义的操作符不是通过句法而是通过变量绑定的形式实现的。 如 `+` 这个操作符， 在 Scheme 中只是一个普通的标识符， 它被绑定到一个对数对象进行求和的 *procedure* 上， 同样的 `*` 等运算符也是这样：

> `(define (h op x y) (op x y))`
>
> `(h + 23 42)` ==> `65`<br/>
> `(h * 23 42)` ==> `966`

*procedure* 定义不是创建 *procedure* 的唯一方法。 一个 *lambda* 表达式会创建一个新的匿名 *procedure* 对象：

> `((lambda (x) (+ x 42)) 23)` ==> `65`

上面的表达式为一个 *procedure* 调用； `(lambda (x) (+ x 42))` 被求值得到一个接受一个参数的 *procedure*， 该*procedure* 接受一个数参数， 返回该数加上`42`的值。