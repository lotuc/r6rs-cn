去区分一个数对象是精确表示一个数还是会存在一些舍入误差是非常有用的。例如 index operations into data structures may need to know the index exactly, as may some opera- tions on polynomial coefficients in a symbolic algebra system. 另一方面，测量的结果是内在不准确的。为了同时顾及准确数(exact)和已知非准确数(inexact)的使用，Scheme 特意区分了准确数对象(exact number object)和非准确数对象(inexact number object)。这种区分是和数类型纬度是正交的。

仅当值为一个准确数时或者由准确数对象通过准确运算得到的结果才是准确数。准确数和数学中的数有显而易见的对应关系。

相反的，一个数为非准确数，其值为非准确数，或者继承自非准确数，或者继承自非准确操作符。因此，非准确性是有传递性的。

准确算术运算符在下列意义下可靠：如果一个准确数传入任何在[小节-Propagation of exactness and inexactness]()中定义的算术 *procedure*，得到的仍是准确数，结果在数学上上是正确的。一般对于非准确数对象来说不是这样的，因为它们涉及到一些如浮点数的近似方法，但是实现过程中应该尽量保证得到的结果尽量和数学上的理想值接近。