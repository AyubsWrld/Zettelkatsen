```cpp
template <typename ByteView, typename Kind>
struct archive
{
    explicit archive(ByteView & data, Kind) :
        m_data(data) {}

    auto position() const { return m_position; }

    auto operator()(auto && ... objects)
    {
        return serialize_many(objects...);
    }

    auto serialize_many(auto & first,
                        auto && ... remains)
    {
        if (auto result = serialize_one(first); failure(result)) {
            return result;
        }

        return serialize_many(remains...);
    }

    ByteView & m_data;
    std::size_t m_position{};
};
```

`serialize` Function**

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

`deserialize` Function**

```cpp
std::size_t deserialize(address_book & book,
                        std::span<const std::byte> data)
{
    archive archive{data, input{}};
    if (failure(archive(book))) {
        return 0;
    }
    return archive.position();
}
```
