As opposed to having three seperate categories we just make it a singular file table and then we can import the useref like that 


```typescript 
import { Entity, Column, PrimaryColumn } from "typeorm";

@Entity()
export class File{
    @PrimaryColumn({ type: "text" })
    abs_path: string;

    @Column({ type: "text" })
    filename: string;

    @Column({ type: "integer" })
    height: number;

    @Column({ type: "integer" })
    width: number;

    @Column({ type: "text" })
    extension: string;
    
    @Column({ type: "text" })
    filetype : string;

    @Column({ type: "text" })
    duration : string;
    
    @Column({ type: "text" })
    uri: string;
}

```


#### Saving the file 
___
```typescript
  async saveFile(): Promise<FILE_ERROR> {
    try {
      const ImageRepository = AppDataSource.getRepository(ImageTable);
      const imageEntity = new ImageTable();
      
      imageEntity.filename = this.fileName; // This might be cahnged within the homescreen.tsx 
      imageEntity.height = this.dimensions.height;
      imageEntity.width = this.dimensions.width;
      imageEntity.extension = this.extension;
      imageEntity.uri = this.uri;
      imageEntity.abs_path = `/sdcard/${this.fileName}`;

      await ImageRepository.save(imageEntity);  
      return FILE_ERROR.FILE_SUCCESS;
    } catch (error) {
      console.error("Error saving image:", error);
      return FILE_ERROR.RESP_ERROR;
    }
  }
}

```