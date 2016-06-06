lexical语法定义字符序列如何被分割成词素，忽略了一些如注释和空字符(whitespace)这种不重要的部分。假设自字符序列为 Unicode 文本。一些在 lexical语法中的词素，诸如标识符、数对象的表示、字符串等，在datum语法中是**词法数据(syntactic data)**，即表示了对象。除了语法的正式定义之外，这一节还描述了这些词法数据表示的是什么数据值(datum value)。

lexical语法中描述注释的部分包含一些对 <datum> 的引用，它们在 datum语法中进行描述。这些注释中的 <datum> 在lexical语法中不是重头部分。

大小写是被区分的，除了这些情况：表示 boolean 值、数对象和使用十六进制数表示 unicode标量值时。例如 `#x1A` 和 `#X1a` 是等价的。而标识符 `Foo` 则区别于 `FOO`。