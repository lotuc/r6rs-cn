一个 Scheme 程序通过*top-level 程序*被调用。和*库* 一样，一个 *top-level 程序* 包含一些*import*、定义和表达式以及一个指定的执行入口。因此 *top-level 程序* 通过对其导入(import)的库通过传递闭包的方式定义一个 Scheme 程序。

下列 *top-level 程序* 通过 `command-line` *过程* `(rnrs program (6))` 库从命令行中获取参数，然后使用 `open-file-input-port` 打开文件，生成一个 *port*（如将文件作为数据源的一个连接），然后调用 `get-bytes-all` *过程* 获取文件二进制内容数据，然后使用 `put-bytes` 将文件内容输出至标准输出：

> ```
> #!r6rs
> (import (rnrs base)
>         (rnrs io ports)
>         (rnrs programs))
> 
> (put-bytes (standard-output-port)
>            (call-with-port
>             (open-file-input-port
>              (cadr (command-line)))
>             get-bytes-all))
> ```