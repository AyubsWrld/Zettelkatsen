- Prefer using scoped enumerations over un-scoped ones. 
- if an enumeration is utilized only within a class/function , we should define it within scope defined by the class/function. 
- Avoid assigning explicit values to your enumerators unless you have a compelling reason to do so.
- Make the enumerator representing 0 the one that is the best default meaning for your enumeration. If no good default meaning exists, consider adding an “invalid” or “unknown” enumerator that has value 0, so that state is explicitly documented and can be explicitly handled where appropriate.
- Specify the base type of an enumeration only when necessary.
___
Tags : #programming #cpp 