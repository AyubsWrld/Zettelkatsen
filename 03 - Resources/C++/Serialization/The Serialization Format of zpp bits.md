```cpp
struct address_book
{
	enum class phone_type : int 
	{
		mobile = 0, home = 1, work = 2;
	}

	struct phone_number
	{
		std::string_number ; 
		phone_type type ; 
	}
	
	struct person 
	{
		std::string name; 
		int id ; 
		std::string email; 
		std::vector<phone_number> phones ; 
	}
	std::vector<person> people; 
}

```

```cpp
address_book book = {{
    {.name = "David",
     .id = 1,
     .email = "david@something.com",
     .phones = {{.number = "11111",
                 .type = address_book::phone_type::mobile},
                {.number = "22222",
                 .type = address_book::phone_type::home}}},

    {.name = "Jane",
     .id = 2,
     .email = "jane@something.com",
     .phones = {{.number = "33333",
                 .type = address_book::phone_type::mobile},
                {.number = "44444",
                 .type = address_book::phone_type::work}}}
}};
```





Anytime there is something that isn't fixed size we will put the size in front. 

So in this case the `std::vector` is not fixed size so we prefix it with the 2. 