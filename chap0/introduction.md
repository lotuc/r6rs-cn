编程语言的设计不应该是对各种特性的简单堆积， 而应该是在移除各种缺陷及局限后使得那些新增的特性变得必要。 Scheme 证明了一个极小数量对表达式进行组合的规则——没有限制如何组合——足以构成一个实用高效的语言， 且足够支持当今使用的主要编程范式。

Scheme 是最早将使用 lambda calculus 作为 first-class procedures 的编程语言之一， 也因此证明了动态类型语言中静态作用域和块结构的用途。 Scheme 为 Lisp 主要方言中 第一个区分 procedures 和 lambda 表达式与符号的语言， 对于 procedure 调用中操作符的计算和操作数的计算无差别对待。 通过对于 procedure 调用完全的依赖来表达迭代过程， Scheme 强化了这样一个事实，即尾递归调用实际上就是带了参数的 gotos 。 Scheme 是第一个拥抱 first-class escape procedures ， which all previously known sequential control structures can be synthesized。 之后的 Scheme 版本中引入了精确和非精确数对象的概念， 这是 Common Lisp 通用数学运算符的一个扩展。 最近， Scheme 又成为了第一个支持 hygienic macros 的编程语言， 它允许一个块结构语法的语言被一致和可靠的扩展。

#### 指导原则

...待翻译