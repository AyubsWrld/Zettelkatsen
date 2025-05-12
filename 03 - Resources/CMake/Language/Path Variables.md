When a variable is expanded using `${}` syntax, all the same rules about spaces apply. Be especially careful with paths; paths may contain a space at any time and should always be quoted when they are a variable (never write `${MY_PATH}`, always should be `"${MY_PATH}"`).
___
Tags : #programming #cmake