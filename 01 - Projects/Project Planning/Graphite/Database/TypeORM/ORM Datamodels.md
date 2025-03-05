we define the data models as classes and the **ORM** creates the table representation of the data models for us .

```typescript 
export class BlogPostModel{
	PostTitle = DataTypes.STRING ; 
	published = DataTypes.DATE   ; 
	postText  = DataTypes.TEXT   ; 
}
```
____
Tags : #programming #computer-architecture #graphite