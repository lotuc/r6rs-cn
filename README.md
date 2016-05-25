| 日期 | 要说的 |
|--|--|
| 2016.5.2 | 将是对 [Revised6 Report on the Algorithmic Language Scheme](http://www.r6rs.org/) 的一个非专业不负责任的一个粗糙翻译。 |

---

<center>
<h2><a href="http://www.r6rs.org/">Revised6 Report on the Algorithmic Language Scheme</a></h2>
MICHAEL SPERBER <br/>
R. KENT DYBVIG, MATTHEW FLATT, ANTON VAN STRAATEN <br/>
(Editors ) <br/>
RICHARD KELSEY, WILLIAM CLINGER, JONATHAN REES (Editors, Revised5 Report on the Algorithmic Language Scheme) ROBERT BRUCE FINDLER, JACOB MATTHEWS <br/>
(Authors, formal semantics)
</center>

<br/><br/>

这份报告给 Scheme 编程语言一个定义性描述。Scheme 是由 Guy Lewis Steele Jr. 和 Gerald Jay Sussman 发明的 Lisp 编程语言的一个有着静态作用域且对尾递归有很好支持的方言。它被设计为拥有极为清晰和精简的语法，及很少的几种用于组合表达式的方法。大量的编程范式，如函数式、命令式及消息传递式可以在 Scheme 中找到一种简洁的表达方式。

这份报告和一份[描述标准库的报告](http://www.r6rs.org/final/html/r6rs-lib/r6rs-lib.html)一同发布；对该报告的引用使用如”库小节“或”库章节“的命名方式。 一同发布的还有一份包含[非规范的附录的报告](http://www.r6rs.org/final/html/r6rs-app/r6rs-app.html)及一份有[关语言和标准库各个方面的决策背景和缘由的报告](http://www.r6rs.org/final/html/r6rs-rationale/r6rs-rationale.html)。

上面列举的人并不是报告所有的作者。这些年中，以下各位也曾参与到对 Scheme 的讨论和语言的设计贡献中，他（她）们曾在之前的报告中被列为作者：

Hal Abelson，Norman Adams，David Bartley，Gary Brooks，William Clinger，R. Kent Dybvig，Daniel Friedman，Robert Halstead，Chris Hanson，Christopher Haynes，Eugene Kohlbecker，Don Oxley，Kent Pitman，Jonathan Rees，Guillermo Rozas，Guy L. Steele Jr.，Gerald Jay Sussman，Mitchell Wand。

为了突出最新的贡献，她（他）们没被列入这份报告的作者中。但是他（她）们的贡献和服务是被牢记和感激的。

我们希望这份报告为整个Scheme社区所拥有，所以我们授权所有人对文档进行全部或者部分进行免费拷贝的权利。特别的，我们鼓励Scheme的实现者使用这份报告作为其实现的手册和其它文档的起点，根据需要进行修改。

编程语言的设计不应该是对各种特性的简单堆积，而应该是在移除各种缺陷及局限后使得那些新增的特性变得必要。Scheme证明了一个极小数量对表达式进行组合的规则——没有限制如何组合——足以构成一个实用高效的语言，且足够支持当今使用的主要编程范式。

---

# 导言

Scheme 是最早将使用 lambda算子 作为 first-class过程 的编程语言之一，也因此证明了静态作用域和动态语言中块结构的可用性。Scheme 是 Lisp 主要方言中第一个区分*过程*和 *lambda表达式与符号*的语言，对所有变量使用单一的词法环境，过程调用中操作符和操作数以同样的方式求值。迭代过程使用过程调用来表达，通过这种方式，Scheme 强化了这样一个事实，即尾递归调用实际上就是带了参数的 goto。Scheme 是第一个拥抱 first-class escape过程的语言，对应之前被广泛使用的控制结构(注：例如顺序控制语句、选择控制语句、循环控制语句等)。之后的Scheme版本中引入了 exact数 和 inexact数 对象，这是 Common Lisp 通用算术运算符的一个扩展。最近，Scheme 又成为了第一个支持 hygienic macros 的编程语言，它允许一个块结构语法的语言被一致和可靠的扩展。

#### 指导原则

编辑总结出一组原则来帮助帮助指导标准化工作，做以下总结。此报告中定义的 Scheme 语言是为了：

- 使得程序员可以无歧义的阅读彼此代码，在遵守规范的 Scheme 实现中，程序应该无差别的运行；
- 扎根血液的简洁性，很少的常用核心语法形式和过程，但对于它们如何组合构建程序的限制减至最低；
- 允许程序定义新的过程和 hygienic语法形式；
- 支持将源代码表示成数据；
- 让过程调用足够强大使其得以表示任何顺序控制过程，允许程序在不使用 global program transformation 的情况下执行非本地(non-local)操作；
- 允许有趣的纯函数在有限内存的机器上在不耗尽内存的情况下无休止的运行下；去
- 让研究者可以使用该语言来探索程序语言的设计、实现和语义。

除此之外，此报告还试图：

- 使得程序员创建的程序和库可以无需修改的情况下在各 Scheme 实现中运行；
- 通过增加对定义 hygiene-bending 和 hygiene-breaking 词法抽象、任意作用域中的过程和 hygienic macros 的支持和新的数据类型，提供了对于 procedural，syntactic，和数据抽象提供更全面的支持；
- 允许具体实现在无需程序员使用跟底层实现相关的运算符或定义的情况下就可以生成高效的代码

...
