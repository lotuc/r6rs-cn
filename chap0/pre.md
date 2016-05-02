<center>
<h2><a href="http://www.r6rs.org/">Revised6 Report on the Algorithmic Language Scheme</a></h2><br/>
MICHAEL SPERBER <br/>
R. KENT DYBVIG, MATTHEW FLATT, ANTON VAN STRAATEN <br/>
(Editors ) <br/>
RICHARD KELSEY, WILLIAM CLINGER, JONATHAN REES (Editors, Revised5 Report on the Algorithmic Language Scheme) ROBERT BRUCE FINDLER, JACOB MATTHEWS <br/>
(Authors, formal semantics)
</center>

---

这份报告给 Scheme 编程语言一个定义性描述。 Scheme 是由 Guy Lewis Steele Jr. 和 Gerald Jay Sussman 发明的 Lisp 编程语言的一个有着静态作用域且对尾递归有很好支持的方言。 它被设计为拥有极为清晰和精简的语法及很少的用于组合表达式的方法。 大量的编程范式， 如函数式、命令式及消息传递式可以在 Scheme 中找到一种简洁的表达方式。

这份报告和一份描述标准库的报告一同发布[[24]]()；对该报告的引用使用如”库小节“或”库章节“的命名方式。 一同发布的还有一份包含非规范的附录的报告[[22]]()及一份有关语言和标准库各个方面的决策背景和缘由的报告[[23]]()。

上面（注：作者栏中）列举的人并不是报告所有的作者。 这些年， 以下各位也曾参与到对 Scheme 的讨论和语言的设计贡献中， 他（她）们曾在之前的报告中被列为作者：

Hal Abelson， Norman Adams， David Bartley， Gary Brooks， William Clinger， R. Kent Dybvig， Daniel Friedman， Robert Halstead， Chris Hanson， Christopher Haynes， Eugene Kohlbecker， Don Oxley， Kent Pitman， Jonathan Rees， Guillermo Rozas， Guy L. Steele Jr.， Gerald Jay Sussman， Mitchell Wand。

为了突出最新的贡献， 她（他）们没被列入这份报告的作者中。 但是他（她）们的贡献和服务是被牢记和感激的。

我们希望这份报告为整个 Scheme 社区所拥有， 所以我们授权所有人对文档进行全部或者部分进行免费拷贝的权利。 特别的， 我们鼓励 Scheme 的实现者使用这份报告作为其实现的手册和其它文档的起点， 根据需要进行修改。