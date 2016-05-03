虽然*definitions* 不是表达式（expressions）， 但是它和复合表达式在句法结构上看起来一样：

> `(define x 23)` <br/>
> `(* x 2)`

上面第一行是 *definition*， 第二行是一个表达式， 其区别在于 `define` 和 `*` 的绑定方式。 从纯粹的句法角度来看，它们同属于 *forms* ， *form* 是 Scheme 程序句法组成部分的通用名称。 特别的， `23` 是 `(define x 23)` 这个 *form* 的 *subform*。