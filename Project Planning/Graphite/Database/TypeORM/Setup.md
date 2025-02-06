#### Installation 
___
```bash
npm install sqlite3 --save
```
#### `tsconfig.json` alterations 
___
**set/add**  `experimentalDecorators` && `emitDecoratorMetaData` both to true . 
#### Making a connection and creating [[Data Source]] 
___
Holds all the details we need to connect to the database . 
```typescript
import { DataSource } from "typeorm" ; 

export const AppDataSource = new Datasource({
	type : "sqlite", // Database of choice 
	database : "my-blog.db", // name of database
	synchronize : true, // Database of choice 
	logging : true, // Database of choice 
	entities : [], // Database of choice 
	subscribers : [], // Database of choice 
	migrations : [], // Database of choice 
})
```
____
Tags : #programming #computer-architecture #graphite