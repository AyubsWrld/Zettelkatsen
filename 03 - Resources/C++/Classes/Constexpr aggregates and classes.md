Recall 

```cpp

constexpr int greater( int x , int y )
{
	return x > y ? x : y ; 
}

int main()
{
	int x = greater( 5 , 4 ) ; // May be compile time or runtime 
	constexpr int y = greater( 5 , 4 ) ; // compiletime 
}
```


Same goes for aggregates 

```cpp

struct X
{
	int m_x {} ; 
	int m_y {} ; 
	constexpr int greater() const
	{
		return m_x > m_y ? m_x : m_y ; 
	}
}

int main()
{
	constexpr X aggregate{} ;  // Must be constexpr. 
	int x = aggregate.greater() ; // May be compile time or runtime 
	constexpr int y = greater( 5 , 4 ) ; // compiletime 
}
```

Since our class isn't a literal type we cannot conduct the same ( aggregates can be constexpr implicitly ). We must supplement a constexpr constructor. 

```cpp
#include <iostream>

class Pair
{
private:
    int m_x {};
    int m_y {};

public:
    constexpr Pair(int x, int y): m_x { x }, m_y { y } {} 

    constexpr int greater() const
    {
        return (m_x > m_y  ? m_x : m_y);
    }
};

int main()
{
    constexpr Pair p { 5, 6 };
    std::cout << p.greater() << '\n';

    constexpr int g { p.greater() };
    std::cout << g << '\n';

    return 0;
}
```


___
Tags: #cpp #programming