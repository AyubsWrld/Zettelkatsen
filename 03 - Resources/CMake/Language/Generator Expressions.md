[generator-expressions](https://cmake.org/cmake/help/latest/manual/cmake-generator-expressions.7.html) are really powerful, but a bit odd and specialized. Most CMake commands happen at configure time, include the if statements seen above. But what if you need logic to occur at build time or even install time? Generator expressions were added for this purpose.[[1]](https://cliutils.gitlab.io/modern-cmake/chapters/basics/functions.html#id3) They are evaluated in target properties.

The simplest generator expressions are informational expressions, and are of the form `$<KEYWORD>`; they evaluate to a piece of information relevant for the current configuration. The other form is `$<KEYWORD:value>`, where `KEYWORD` is a keyword that controls the evaluation, and value is the item to evaluate (an informational expression keyword is allowed here, too). If KEYWORD is a generator expression or variable that evaluates to 0 or 1, `value` is substituted if 1 and not if 0. You can nest generator expressions, and you can use variables to make reading nested variables bearable. Some expressions allow multiple values, separated by commas.[[2]](https://cliutils.gitlab.io/modern-cmake/chapters/basics/functions.html#id4)

If you want to put a compile flag only for the DEBUG configuration, for example, you could do:

`target_compile_options(MyTarget PRIVATE "$<$<CONFIG:Debug>:--my-flag>")`

This is a newer, better way to add things than using specialized `*_DEBUG` variables, and generalized to all the things generator expressions support. Note that you should never, never use the configure time value for the current configuration, because multi-configuration generators like IDEs do not have a “current” configuration at configure time, only at build time through generator expressions and custom `*_<CONFIG>` variables.
___
Tags : #programming #cmake