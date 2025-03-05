Model used within the data tier to distribute load across multiple servers . Data is replicated across Master and Slave databases so that data can be replicated . `Master Databases`  are responsible for any data modification operations ( Insert , Delete , Update ) . Whereas `Slave Databases` handle all the reads . When data is sent to the `Master Database` it is replicated and inserted into the `Slave Databases` . 

- Better performance: In the master-slave model, all writes and updates happen in master nodes; whereas, read operations are distributed across slave nodes. This model improves performance because it allows more queries to be processed in parallel.
- Reliability: If one of your database servers is destroyed by a natural disaster, such as a typhoon or an earthquake, data is still preserved. You do not need to worry about data loss because data is replicated across multiple locations.
- High availability: By replicating data across different locations, your website remains in operation even if a database is offline as you can access data stored in another database server.

___
Tags : #programming #system-design 