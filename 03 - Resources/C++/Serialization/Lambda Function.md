```cpp
std::size_t serialize(const address_book & book,
                      std::span<std::byte> data) {
    std::size_t position{};
    auto out = [&](auto && value) { /* ... */ };

    if (!out(book.people.size())) { return 0; }
    for (auto & entry : book.people) {
        if (!out(entry.name)) { return 0; }
        if (!out(entry.id)) { return 0; }
        if (!out(entry.email)) { return 0; }
        if (!out(entry.phones.size())) { return 0; }
        for (auto & phone : entry.phones) {
            if (!out(phone.number)) { return 0; }
            if (!out(phone.type)) { return 0; }
        }
    }
    return position;
}
```


```cpp
auto out = [&](auto && value) {
    if constexpr (requires { value.data(); value.size(); }) {
        auto size = value.size();
        if (sizeof(size) > data.size() - position) {
            return false;
        }
        std::memcpy(data.data() + position, &size, sizeof(size));
        position += sizeof(size);
        auto size_in_bytes = size * sizeof(*value.data());
        if (size_in_bytes > data.size() - position) {
            return false;
        }
        std::memcpy(data.data() + position, value.data(), size_in_bytes);
        position += size_in_bytes;
    } else {
        if (sizeof(value) > data.size() - position) {
            return false;
        }
        std::memcpy(data.data() + position, &value, sizeof(value));
        position += sizeof(value);
    }
    return true;
};
```