___
Tags: #cpp #progarmming 
___
What is the ===Preprocessor=== Phase ? ;; 

When does the ===Preprocessor=== Phase occur ? ;; Prior to compilation . 

What does the ===Preprocessor=== do ? ;; Changes the text content of the source file without actually modifying the code . 

Give an example of what the ===Preprocessor=== does ;; Strips comments , replaces definitions , and processes `#include` directives . 

What is the file called after it is been processed by the ===Preprocessor=== ? ;; It is called a translation unit and it is then ran through the compiler . 

What is ===Translation=== ? The entire process of Preprocessing , Compiling , Linking . 

What is a ===Preprocessor=== Directive ? ;; 

What is `#include` and what does it do ? ;; Preprocessor directive which replaces itself with all the contents of the file listed within `<>` . 

Why is `#include` recursive ? ;; Because once it includes the listed file , the file included may also have `#include` therefore it must go through including that file as well . 

What does the preprocessor do when it encounters `#include<iostream>` ? ;; It replaces the preprocessor directive with the contents of the iostream.c file . 

What do ===Preprocessor Directives=== end with ? ;; and `\n` newline . 

What is a Macro ? ;; Preprocessor directive which tells the preprocessor how to replace certain text to a value . 


What is Conditional Compilation Directive ? ;; Conditional Compilation Directive allows you to specify what you want and don't want to be compiled ; 

What is an Object-like macro ? ;; Object-like macro swaps the text for the value next to it . 

What is an example of Conditional Compilation Directive? ;; `ifdef` , `#ifndef` , `#endif` . 

What is the output of this code ![[Pasted image 20250306165101.png]] ;; `Joe`

What is the output of this code ![[Pasted image 20250306165213.png]];; `Bob` , because the Object-like macro `PRINT_BOB` is not defined 


What is the output of this code and why ? ![[Pasted image 20250306165404.png]]
; ` Joe ` -  Because `#if` Conditional Compilation directive is set to 0 , therefore anything within that block is removed . 


What is the scope of defines ? ;; Global scope 


What does this code do and why ![[Pasted image 20250306165736.png]]? ;; Prints because Preprocessor directives do not conform to similar scope as Traditional C++ therefore this is the same as had we given it global scope . 

Are directives included within other files included aswell ? ;; Yes , if I have an Object-like Preprocessor directive defined within a file and `#include` said file into the file im currently working in the preprocessor will also recognize the Object-like macro defined within the other file . 

When do Preprocessor Directives discard identifiers ? ;; When the identifiers are not used anymore 

What is a transitive include ? ;; When you `#include` something into one file but that file contained `#include` to another file . 


What are header guards and how do they work ? ;; Header guards utilize Conditional Compilation directives to include class definitions so that they are not included within the same 


What is an alternative for basic header guards ? ;; `#pragma once` 