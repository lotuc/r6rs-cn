这一章描述 Scheme 中*数*的模型。区分数学上的数、Scheme 用于对其建模的对象和用于实现数的机器表示是很重要的。在这份报告中，术语 *number* 用于表示数学上的数，术语 *number object* 用于表示 Scheme 中表示数的对象。这份报告中实用的类型 *complex*, *real*, *rational* 和 *integer* 既用于表示数学上的数也用于表示数对象。*fixnum* 和 *flonum* 表示数对象的一个特殊子集，这是由于机器表达能力的限制，后面会提到。