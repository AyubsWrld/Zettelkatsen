```cpp
enum class Status 
{
  S_ERROR,
  S_OK 
};

using request_handler = Status (*)( /* Some types */ ) ; 


Status routine_one(); 
Status routine_two(); 

enum class Opcode : uint8_t // I intend on using this for indexing array
{
  ROUTINE_ONE,    // 0000 0000 
  ROUTINE_TWO,    // 0000 0001
  ROUTINE_FOUR,   // 0000 0002
  OPCODE_END,     // 0000 0003
};

// This captures sizeof routine_handler_array through casting it to hold the number of opcodes directly. 
// This expands to OPCODE_END * size_t ( which = sizeof * ) 
static constexpr request_handler request_handler_array[ ( size_t ) Opcode::OPCODE_END ] = {
  &routine_one,
  &routine_two, 
}; 

```

Can static_assert against OP_CODE later.

___
Tags: #cpp #idioms