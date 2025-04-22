
| Declaration          | What’s const?   | Pointer changeable? | Pointee changeable? |
| -------------------- | --------------- | ------------------- | ------------------- |
| `const T* ptr`       | Pointee         | ✅ Yes               | ❌ No                |
| `T* const ptr`       | Pointer         | ❌ No                | ✅ Yes               |
| `const T* const ptr` | Both            | ❌ No                | ❌ No                |
| `const T*& ref`      | Pointee via ref | ✅ Yes               | ❌ No                |

___
Tags : #programming #cpp 