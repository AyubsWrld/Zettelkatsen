#### Dependencies : `expo-image-picker`

#### TLDR Snippet 

```typescript
import * as ImagePicker from "expo-image-picker";

const pickMedia = async () => {
  const permission = await ImagePicker.requestMediaLibraryPermissionsAsync();
  if (!permission.granted) {
    alert("Permission to access media library is required!");
    return;
  }

  const result = await ImagePicker.launchImageLibraryAsync({
    mediaTypes: ImagePicker.MediaTypeOptions.All, // Images & Videos
    allowsEditing: true,
    quality: 1, // High quality
  });

  if (!result.canceled) {
    console.log("Picked file:", result.assets[0]);
    return result.assets[0]; // File object
  }
};

````

#### Return Object ...

```json
{
  "assetId": "F6F9AFD7-4373-4307-910A-F0BCE5FED50C/L0/001",
  "base64": null,
  "duration": null,
  "exif": null,
  "fileName": "IMG_4663.PNG",
  "fileSize": 1789453,
  "height": 1125,
  "mimeType": "image/png",
  "pairedVideoAsset": null,
  "type": "image",
  "uri": "file:///var/mobile/Containers/Data/Application/F24429FE-1B70-4AAD-8F57-D1D247C3202D/Library/Caches/ExponentExperienceData/@anonymous/GraphiteApp-ecbcb476-4904-4499-abb0-2d74727cc3c2/ImagePicker/B119EF0A-B2F5-407E-A405-60844A9973EE.png",
  "width": 1125
}

```

#### Uploading a file

`expo-image-picker` utilizes [[async await]] to fetch files the user wishes to upload .

The library requires two `async-await`queries , one for getting user permission , and the second for actually uploading the file . 

```typescript
const permission = await ImagePicker.requestMediaLibraryPermissionsAsync(); 
if(!permission.granted) return ;  // Logic for if the person doesn't want to oblige
const result = ImagePicker.launchImageLibraryAsync({
    mediaTypes: ImagePicker.MediaTypeOptions.All, // Images & Videos
    allowsEditing: true,
    quality: 1, // High quality
}); 

if(result.cancelled) return ; 
return result.assets[0] ; 


```


#### Upload file
