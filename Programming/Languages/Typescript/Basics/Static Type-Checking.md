Allows us to delineate the type of a variable so that once we pass it to the typescript compiler we know exactly what type we have and how to run it .

```typescript
const message = "Hello world!" ; // Implicit type, validated at runtime which means errors may be thrown
```

```typescript
const message : string = "Hello world!" ; // Explicit type, validated when running through transpiler 
```

