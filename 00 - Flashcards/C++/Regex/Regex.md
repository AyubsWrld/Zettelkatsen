___
Tags: #cpp #programming
___

What is a regular expression ? ;;  a sequence of symbols and characters expressing a string or pattern to be searched for within a longer piece of text.

What is the Target Sequence ? ;; he character sequence that is searched for a pattern. This may be a range specified by two iterators, a null-terminated character string or a [std::string](https://en.cppreference.com/w/cpp/string/basic_string "cpp/string/basic string").

What is the Pattern ? ;; The regular expression itself, it determines what constitutes a match . It is an object of type `std::basic_regex` . 

What is the Matched Array ? ;; the information about matches that are retrieved and stored as an object of type `std::match_results`.

What is the replacement string ? The string that determines how to replace the matches . 

What preprocessor directive do we need for regex ? ;; we have to `#include` regex header file . 

What is the `<regex>` library in C++? ;; The `<regex>` library provides support for regular expressions, allowing pattern matching and text manipulation.  
How do you include the regex library in C++? ;; Use `#include <regex>` to access regex functionality.  
What are the main components of the `<regex>` library? ;; The key components are `std::regex` (pattern), `std::smatch` (match results), `std::regex_match` (full match), `std::regex_search` (partial match), and `std::regex_replace` (text replacement).  
What is `std::regex_match` used for? ;; `std::regex_match` checks if an entire string exactly matches a given regular expression.  
What is `std::regex_search` used for? ;; `std::regex_search` looks for a partial match of a pattern within a string.  
How do you replace text using regex in C++? ;; Use `std::regex_replace(string, std::regex, replacement)` to replace matched patterns with a new string.  
What is `std::smatch` in regex? ;; `std::smatch` is used to store match results when searching a `std::string`.  
How do you check if a string contains a pattern using regex? ;; Use `std::regex_search` with `std::smatch` to find occurrences of a pattern within a string.  
How do you define a regex pattern in C++? ;; Use `std::regex pattern("your_pattern");` to define a regular expression.  
What are regex flags in C++? ;; Regex flags like `std::regex_constants::icase` (case-insensitive) modify how patterns are interpreted.  
What is the difference between `std::regex_match` and `std::regex_search`? ;; `std::regex_match` checks if the entire string matches the pattern, while `std::regex_search` finds partial matches within the string.  
How do you create a case-insensitive regex in C++? ;; Use `std::regex pattern("your_pattern", std::regex_constants::icase);` to ignore case.  
What is the purpose of `std::regex_constants`? ;; `std::regex_constants` provides flags like `icase`, `multiline`, and `nosubs` to modify regex behavior.  
How do you validate an email using regex in C++? ;; Use `std::regex email_pattern(R"([a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,})");` and `std::regex_match(email, email_pattern)`.  
What is the purpose of `std::cmatch`? ;; `std::cmatch` is similar to `std::smatch` but works with C-style strings (`const char*`).