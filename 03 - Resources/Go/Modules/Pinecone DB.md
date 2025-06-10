#### Indexes
___
We can run this code to generate an index. There are two types of indexes. 
- **Dense Indexes**
- **Sparse Indexes** 

#### Upserting Text
___



Pinecone is eventually consistent, so there can be a slight delay before new or changed records are visible to queries. You can [view index stats](https://docs.pinecone.io/guides/index-data/check-data-freshness) to check if the current vector count matches the number of vectors you upserted (50):

```go
// Add to the main function:
// View stats for the index
stats, err := idxConnection.DescribeIndexStats(ctx)
if err != nil {
    log.Fatalf("Failed to describe index \"%v\": %v", indexName, err)
} else {
    fmt.Printf("%+v", prettifyStruct(*stats))
}
```