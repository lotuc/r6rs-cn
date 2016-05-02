Scheme 程序对象操纵*对象*， 也就是*值*。 Scheme 对象被组织成一组值的结构被称为*类型*。 这一小节介绍 Scheme 语言中最基本的和最重要的类型。 后续章节中会介绍更多的类型。

> 注意： 由于 Scheme 的为 latent 类型的， 此报告中*类型*的使用和其它语言语境中的使用并不相同， 特别是和 manifest 类型的语言。

**Booleans**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 一个 boolean 为 true 或者 false。 在 Scheme 中对应 “false” 的对象记为 **#f**， 对应 “true” 的对象记为 **#t**。 然而， 在大部分要使用 true 值的地方， 任何不为 **#f** 的对象被视为 true。

**Numbers**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Scheme 支持种类繁多的数类型， 包括用于表示任意精度整数、 有理数、 复数安定各种非精确数的对象。 

**Characters**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Scheme characters 对应于文本字符。 更精确的说， 它们与 Unicode 标准中*标量*的同构。

**Strings**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Strings 是 characters 组成的定长序列， 因此可以表示任意的 Unicode 文本。

**Symbols**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 一个 symbol 是一个对象， 它用于表示 symbol 的名字字符串。 和 string 不同， 两个名字拼写一样的 symbol 是不可区分的。 Symbols 在很多地方非常有用， 如可以像其它语言中的枚举值那样使用。

**Pairs 和 lists**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 一个 pair 是一个包含两个部分的数据结构。 pairs 最常用来表示（单链）lists， 其第一个部分（ “car” 部分）表示一个 list 的第一个元素， 第二个部分（ “cdr” 部分）表示该 list 的剩余部分。 Scheme 中区分出了一个空 list， 它是使用 pair 构成的 list 的 cdr 链的最后一个 cdr。

**Vectors**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 和 list 类似， 是一个线性的数据结构， 用于表示有限的任意对象序列。 但是其中的对象通过整数的顺序索引引用。因此更适合用于需要对组成元素进行通过位置随机取值的情形。

**Procedures**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 在 Scheme 中 procedures 也是值。

