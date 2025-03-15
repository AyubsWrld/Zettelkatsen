___
Tags: #cpp #programming
___

What is a constant expression ? ;; means that the object can be used in a constant expression. The value of the initializer must be known at compile-time. The constexpr object can be evaluated at runtime or compile-time.
<!--SR:!2025-03-17,3,250-->

What does const mean ? ;; means that the value of an object cannot be changed after initialization. The value of the initializer may be known at compile-time or runtime. The const object can be evaluated at runtime.
<!--SR:!2025-03-18,4,270-->

What are some challenges when it comes to `const` variables ? ;; The `const` keyword does not always guarantee that a variable can be used in a constant expression.
<!--SR:!2025-03-15,1,230-->

Which of the following are const ![[code_20250311_224339_via_10015_io.png]] ;; C only , a is not const initialized and b is initialized using a .
<!--SR:!2025-03-17,3,250-->

What is a compile time constant ? ;; A variable whose value is known at compile time . This allows the compiler to optimize it during compilation as opposed to run time .
<!--SR:!2025-03-17,3,250-->

What is a run time constant ? ;; A variable whose value is made constant at run time as opposed to compile time. There values are not known until runtime.
<!--SR:!2025-03-17,3,250-->

Give an example of a Runtime constant ;; ![[Pasted image 20250311224820.png]]
<!--SR:!2025-03-15,1,230-->
When are these constants and what types of constants are they ? ![[Pasted image 20250311224929.png]] ;; d is constant *iff* someVar is constant , if so it is a compile time constant . a is a runtime constant if getValue returns a constant value .
<!--SR:!2025-03-17,3,250-->

What does `constexpr` do ? ;; Converts a variable to a compile time constant. This works with
<!--SR:!2025-03-15,1,230-->

Can non-integral types be const ? ;; No , unless we use constexpr.
<!--SR:!2025-03-17,3,250-->

