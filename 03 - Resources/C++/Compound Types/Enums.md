#### What is an Enumerated type?
___
Constexpr program defined type which holds a discrete set of values. 

```cpp
enum Colors 
{
	blue,
	red,
	green,
	yellow
};
```

Used to add readability to your code. 

#### Common use cases
____
We usually want to use an enumeration when we have an object that can only take on a discrete number of possible values eg..

**Item types within a video game**: 
```cpp
enum ItemType
{
	sword,
	torch,
	potion,
};

int main()
{
	ItemType holding{ torch };

	return 0;
}
```

**Return codes for errors:**

```cpp
enum FileReadResult
{
    readResultSuccess,
    readResultErrorFileOpen,
    readResultErrorFileRead,
    readResultErrorFileParse,
};

FileReadResult readFileContents()
{
    if (!openFile())
        return readResultErrorFileOpen;
    if (!readFile())
        return readResultErrorFileRead;
    if (!parseFile())
        return readResultErrorFileParse;

    return readResultSuccess;
}
```

**Parameters for functions**

```cpp
enum SortOrder
{
    alphabetical,
    alphabeticalReverse,
    numerical,
};

void sortData(SortOrder order)
{
    switch (order)
    {
        case alphabetical:
            // sort data in forwards alphabetical order
            break;
        case alphabeticalReverse:
            // sort data in backwards alphabetical order
            break;
        case numerical:
            // sort data numerically
            break;
    }
}
```

___
Tags : #programming #cpp 