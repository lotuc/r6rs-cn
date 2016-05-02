这一章对 Scheme 的语义进行一个概述。 这个概述的目的是对语言的基本概念进行解释以便对于报告后续章节的理解， 这章将组织成引用的风格。 所以， 这一章并不是语言完整的介绍， 更不是精确或规范的介绍。

与 Algol 一样， Scheme 是一个静态作用域的编程语言。 每个被使用的变量都有一个词法透明（lexically apparent）的对于该变量的绑定。

Scheme has latent as opposed to manifest types [[28]]()。 类型和对象（也被称为值）而不是和变量绑定（一些作者将 latent type 的语言称为无类型、弱类型或者动态类型语言）。 其它为 latent 类型的语言有 Python、 Ruby、 Smalltalk 和 Lisp 的其它方言。 为 manifest 类型的语言（有时被称为强类型或静态类型语言）有 Algo 60、 C、 C#、 Java、 Hashkell 和 ML。

所有 Scheme 计算过程中创建的对象， 包括 procedures 和 continuations， 都有 unlimited extent。 所有的 Scheme 对象都不会被销毁。 Scheme 的实现不会（不常）耗尽内存的原因是它们实现了对于那些被证明在将来的计算过程不会被使用的对象的回收。 其它拥有类似特性的语言有 C#、 Java、 Hashkell、 大部分的 Lisp 方言、 ML、 Python、 Ruby 和 Smalltalk。

Scheme 的实现必须很好的实现尾递归。 它可以使得使用递归方式定义的迭代的计算过程可以在常数空间内运行。 这样就可以通过一般的 procedure 来实现迭代， 那些特殊的迭代结构则使用语法糖实现。

Scheme 是第一个支持 procedures 作为对象的语言。 Procedures 可以被动态的创建、存储、作为计算的返回值等等。 拥有这个特性的其它语言有 Common Lisp、 Hashkell、 ML、 Ruby 和 Smalltalk。

Scheme 一个特别的特性是 continuations， 在大多数语言中， 对它的操作都在背后进行， 可以称它为 “first-class” 状态。 first-class continuations 对于实现很多高级的控制流， 如非本地退出（non-local exit）、backtracking 和协程（coroutines）时非常有用。

在 Scheme 中， 参数表达式的计算先于 procedure 调用， 不管这些参数对于调用的结果是否必要。 有类似特性的语言有 C、 C#、 Common Lisp、Python、 Ruby 和 Smalltalk。 这和 Hashkell 的惰性求值或 Algol 60 的 call-by-name 方式不同， 它们只在一个 procedure 求值过程中实际用到一个表达式时才会对其进行求值。

Scheme 的算术模型提供了丰富的数字类型和对应的操作符。 另外，它还区分了精确（exact）和非精确（inexact）数：大致地说就是，精确数对象精确对应于一个数， 而非精确数对象的计算结果包含了一些舍入和其它误差。