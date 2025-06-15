Type casting can be done through the use of :: operator. This is especially useful when working with writing queries within source code. 

```go
sql := `
INSERT INTO tablename (user_id)
VALUES( ARRAY[Values]::UUID )  
`
```
___
Tags: #neovim #lsp
