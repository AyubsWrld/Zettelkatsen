Simply make a folder with the modules name you want and have any amount of files you need and mark them with the package name. Every file from then on out is served relatively from the top go module. 

```txt
module [ Module Name ] 

go [ version number ].
```


Within main we have:

```go

package main 

import(
 "[modulename]/[packagename]" // <- this is usually the main module
)
```


___
Tags : #golang #modules