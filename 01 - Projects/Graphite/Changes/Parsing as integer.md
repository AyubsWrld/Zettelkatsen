```c
    FileMetaData file ;

    cJSON *fileExtension = cJSON_GetObjectItem(root, "fileExtension");
    cJSON *filename = cJSON_GetObjectItem(root, "filename");
    cJSON *filepath = cJSON_GetObjectItem(root, "filePath");
    cJSON *createdOnInUTC = cJSON_GetObjectItem(root, "createdOnInUTC");
    cJSON *updatedInUTC = cJSON_GetObjectItem(root, "updatedInUTC");

    if (cJSON_IsString( filename ) && (filename->valuestring != NULL))
    {
        file.name = filename->valuestring ;
    }

    if (  fileExtension->valueint || fileExtension->valuestring )
    {
        int cvt = atoi(fileExtension->valuestring) ; // Bruh change this pls
        file.extension = ( FILE_TYPE ) cvt ;
    }

```
____
Tags : #programming #computer-architecture #graphite