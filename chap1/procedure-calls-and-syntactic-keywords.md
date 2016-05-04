`(+ 23 42)`、 `(f 23)` 和 `((lambda (x) (+ x 42)) 23)` 都是 *procedure* 调用的实例， *lambda* 表达式和 *let* 表达式不是。这是因为尽管 *let* 是一个标识符， 但它不是变量，而是一个 *syntactic keyword*。第一个子表达式为*syntactic keyword* 的 *form* 遵守该关键字对应的特殊规则。 *Definition* 中的 *define* 标识符也是一个 *syntactic keyword*。 因此， *definitions* 不是 *procedure* 调用。

*lambda* 关键字定义的 *form* 其规则为：第一个 *subform* 是参数列表，剩余的 *subforms* 是 *procedure* 的 *body*。 在 *let* 表达式中，第一个 *subform* 是一个指定绑定的列表， 剩余 *subforms* 是 *body*。

*procedure* 调用和这些 *special forms* 可以通过查看一个 *form* 的第一个位置上的关键字来区分： 如果第一个位置上不是一个 *syntactic keyword*， 该表达式是一个 *procedure* 调用（被称为 *identifier macros* 的东西也可以创建其它类型的 *special forms*， 但是它们相对来说并不常见）。 Scheme 的 *syntactic keywords* 数量是比较少的， 这也使得区分这两者没那么困难。事实上，Scheme 中是可以创建新 *syntactic keywords* 的。