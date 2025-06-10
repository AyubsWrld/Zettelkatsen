Multi-tenant Architectures can be built either through having all the users share a database or through having giving all the users their own unique databases. The pros with the former are that it is relatively cost effective and implementation is relatively easy as well. The cons being of course risk of a single user utilizing a bunch of resources and the chance of data leakage ( Must included a UUID with every query ). This can be alleviated through the introduction of separate databases with the caveat of costliness and increased complexity. 

The third option is a hybrid approach wherein some users are given their own database and some users are share databases between themselves. 
___
Tags : #programming #system-design #interview