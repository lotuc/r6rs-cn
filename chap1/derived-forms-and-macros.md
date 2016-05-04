这份报告中指出的很多 *special forms* 可以被转化为其它的更为基础的 *special forms*。例如，一个 *let* 表达式可以为被转化为一个 *procedure* 调用和一个 *lambda* 表达式。下面两个表达式等价：

> ```
> (let ((x 23)
>       (y 42))
>   (+ x y))                         ==> 65
> ```
>
> ```
> ((lambda (x y) (+ x y)) 23 42)     ==> 65
> ```

类似 *let* 表达式的这种 *forms* 被称为 *derived forms*，因为它们的语义可以通过其它的 *forms* 通过语义转化而来。一些 *procedure* 定义也是 *derived forms*。 如下面的两个 *definitions* 等价：

> ```
> (define (f x)
>   (+ x 42))
> ```
>
> ```
> (define f
>   (lambda (x)
>     (+ x 42)))
> ```

在 Scheme 中，可以通过将 *syntactic keywords* 绑定到 *macros* 上的方式创建新的 *derived forms* ：

> ```
> (define-syntax def
>   (syntax-rules ()
>     ((def f (p ...) body)
>       (define (f p ...)
>         body))))
> ```
>
> ```
> (def f (x) (+ x 42))
> ```

上面的 *define-syntax* 定义匹配了结构 `(def f (p ...) body)` 的表达式被转化为 `(define (f p ...) body)`。因此，上面的 *def* 表达式被转化为了：

> ```
> (define (f x) (+ x 42))
> ```

可以创建新的 *syntactic keywords* 的能力使得 Scheme 特别灵活和富于表现，它允许你通过自定义的方式给 Scheme 添加其它语言的特性。