___
Tags: #cpp #progarmming 
___

What is a scope region ? ;; A scope region is an area of source code wherein all declared identifiers are considered to be distinct from identifiers within other scope regions . For example a function body .
<!--SR:!2025-03-07,1,230-->

What is a Namespace ? ;; A Namespace is a user defined scope region which allows you to declare functions and variables within it for the purpose of disambiguation .
<!--SR:!2025-03-09,3,250-->

True or False ? A name declared within a scope region (such as a namespace) is distinct from any identical name declared in another scope. ;; True
<!--SR:!2025-03-09,3,250-->

What is the Global Namespace ? ;; within C++ , any identifier not defined within a specific scope region is considered to part of the Global Scope/Namespace
<!--SR:!2025-03-09,3,250-->

What happens when you use an identifier defined inside a non-global namespace? ;; You need to tell the compiler that the identifier lives inside the namespace, typically by using the namespace's scope or a `using` directive.
<!--SR:!2025-03-07,1,230-->

What is the scope resolution operator ? :: , tells the compiler which definition to assign an identifier . 

What is a using directive ? ;; A using directive allows us to access identifiers within a namespace without prefixing it with the namespace + :: .
<!--SR:!2025-03-09,3,250-->

Why should we refrain from utilizing the using directive ? ;;
<!--SR:!2025-03-09,3,250-->