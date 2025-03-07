___
Tags: #cpp #progarmming 
___

What is a regular expression ? ;;  a sequence of symbols and characters expressing a string or pattern to be searched for within a longer piece of text.

What is the Target Sequence ? ;; he character sequence that is searched for a pattern. This may be a range specified by two iterators, a null-terminated character string or a [std::string](https://en.cppreference.com/w/cpp/string/basic_string "cpp/string/basic string").

What is the Pattern ? ;; The regular expression itself, it determines what constitutes a match . It is an object of type `std::basic_regex` . 

What is the Matched Array ? ;; the information about matches that are retrieved and stored as an object of type `std::match_results`.

What is the replacement string ? The string that determines how to replace the matches . 

What preprocessor directive do we need for regex ? ;; we have to `#include` regex header file . 
