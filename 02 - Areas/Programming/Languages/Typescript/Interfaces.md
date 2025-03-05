```typescript
interface fileHandler {
  bar : () => void ; 
}

const handleAdd : fileHandler = { 
  bar : () => {
    console.log("Handling Add File") ; 
  }
}

const handleProcess : fileHandler = { 
  bar : () => {
    console.log("Handling Process") ; 
  }
}
```



