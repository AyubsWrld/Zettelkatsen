```cpp
std::size_t serialize(const address_book & book,
                      std::span<std::byte> data)
{
    archive archive{data, output{}};
    if (failure(archive(book))) {
        return 0;
    }
    return archive.position();
}
```
