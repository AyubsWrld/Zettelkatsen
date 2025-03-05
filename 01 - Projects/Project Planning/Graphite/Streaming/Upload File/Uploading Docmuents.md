#### `expo-av`
- **Expo Document Picker** : Allows user to choose a file  , Utilizes `async-await` to upload the files
```typescript
import * as DocumentPicker from "expo-document-picker";

const pickFile = async () => {
  try {
    const result = await DocumentPicker.getDocumentAsync({});
    if (result.canceled) return; // Is user prematurely exits
    console.log("File picked:", result.assets[0]);
    return result.assets[0]; // File object
  } catch (error) {
    console.error("Error picking file:", error);
  }
};
```


