flonum 是与实现无关的 exact整数对象的一个子集。同样，每个 Scheme 实现都必须定义其 inexact实数的一个子集为 flonum，将对应的外部表示转化为 flonum。注意，这并不是说实现中必须使用浮点数表示。

> 原文 :-(
>
> A fixnum is an exact integer object that lies within a certain implementation-dependent subrange of the exact integer objects. Likewise, every implementation must designate a subset of its inexact real number objects as flonums, and to convert certain external representations into flonums. Note that this does not imply that an implementation must use floating-point represen- tations.
