# New dataset

```
GET news/_mapping



GET news/_search
{
  "query": {
    "match": {
      "headline": "Google"
    }
  }
}

GET news/_search
{
  "query": {
    "match": {
      "headline": {
        "query": "Tech Wold",
        "operator": "and",    // default; or
        "fuzziness": "AUTO"   // default; 0
      }
    }
  }
}

GET news/_search
{
  "query": {
    "multi_match": {
      "type": "best_fields", 
      "query": "Tech World",
      "fields": ["headline^3", "short_description"],
      "fuzziness": "AUTO"       
    }
  }
}



GET news/_search
{
  "query": {
    "multi_match": {
      "type": "best_fields", 
      "query": "Tech Word",
      "fields": ["headline^3", "short_description"],
      "fuzziness": "AUTO"
    }
  },
  "size": 3
}

GET news/_search
{
  "query": {
    "combined_fields": {
      "query": "Tech World",
      "fields": ["headline^3", "short_description"],
      "minimum_should_match": "75%"
    }
  }
}
```