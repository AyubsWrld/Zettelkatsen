> [!tldr] 
> Taking a step before the main calculation to make the main operation simpler . Tidying up your workspace before getting to work  

Tidying up the data before parsing it . Imagine for example you have a giant pile of clothes , and you wish to find a specific piece within the entire pile . A brute force approach would have you picking up every piece of clothe one by one , comparing it to your desired clothing piece , and then moving on . This could become computationally demanding . So instead of just going through the messy pile of clothing , you can first sort out the clothing and then try to find the garment you are looking for.  This is an example of **Presorting** . 

We invest some time upfront sorting everything , the rest of the operations become very easy . 


Sometimes however **Presorting** isn't the most optimal route we want to take . For example finding the smallest element within a list of *n-th* length . We would not want to **Presort** , rather we would want to use a [[Partition Algorithm]] . 

___

Tags : #programming #algorithms 