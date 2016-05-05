Scheme 的代码可以通过*库*的方式组织。每个*库*包含一些定义和表达式。它可以从其它库中引入定义，也可以导出定义给其它*库*使用。

下面的库 `(hello)` 导出了一个称为 `hello-world` 的定义，它同时引入了 *base 库* 和 *simple I/O 库*。`hello-world` 导出的是一个 *procedure*，它打印 `Hello World` 并换行：

> ```
> (library (hello)
>   (export hello-world)
>   (import (rnrs base)
>           (rnrs io simple))
>   (define (hello-world)
>     (display "Hello World")
>     (newline)))
> ```
