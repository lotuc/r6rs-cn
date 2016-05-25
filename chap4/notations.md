Scheme 的正式语法使用 **BNF** 表述。非终结符使用尖括号表示。非终结符不区分大小写。

语法中所有的空字符只是为表述清晰而用。`<Empty>`表示空字符串。

使用了下列 **BNF** 扩展以使语法描述更为精炼：`<thing>*`表示`<thing>`出现零或多次，`<thing>+`表示`<thing>`至少出现一次。

一些非终结符使用名字指代对应的 Unicode标量值

| 名字表示 | Unicode标量值值表示 |
|-------------------------|------------|
|`<character tabulation>` | `<U+0009>` |
| `<linefeed>`            | `<U+000A>` |
| `<carriage return>`     | `<U+000D>` |
| `<line tabulation>`     | `<U+000B>` |
| `<form feed>`           | `<U+000C>` |
| `<carriage return>`     | `<U+000D>` |
| `<space>`               | `<U+0020>` |
| `<next line>`           | `<U+0085>` |
| `<line separator>`      | `<U+2028>` |
| `<paragraph separator>` | `<U+2029>` |