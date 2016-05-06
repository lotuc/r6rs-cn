数可以按照包含关系排列成塔形，塔的每一层都是上面一层的子集：

> ```
>     number
>     complex
>     real
>     rational
>     integer
>     number
> ```

例如，`5` 是一个整数(integer)，因此 `5` 也是有理数、实数、复数。这对于用来对 `5` 进行建模的数对象也适用。

数对象按照上面一样的方法组织，塔每层及一下的类型分别通过判定表达式 `number?`, `complex?`, `real?`, `rational?`, `integer?` 来判定。*Integer number objects* 也被称为 *integer objects*。

计算机中数的表示不能简单的与上面的塔形结构对应。例如，*integer* `5` 就有几种表示方法。Scheme 中将数作为抽象数据类型进行数运算，尽量与其底层表示无关。尽管不同的 Scheme 的实现可能对数有不同的实现，但这些对于程序员应该是透明的。