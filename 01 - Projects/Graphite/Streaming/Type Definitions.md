```typescript
type Image = {
  fileName      : string        ; // files name
  filePath      : string ?      ; // 
  size          : number        ; // files size
  assetID       : string        ; // idk what this is or whether we should add it 
  dimensions    : Dimensions    ;
  type          : string        ;
  fileExtension : string        ; // File type  idk if this is worth storing tho 
}

```

```typescript
type Dimensions = {
  height : number ,  
  width  : number ,  
}
```
