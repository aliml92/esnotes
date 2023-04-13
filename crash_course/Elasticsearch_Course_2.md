# Part 2: Understanding the relevance of your search with Elasticsearch and Kibana

```bash
GET news_headlines/_search

GET news_headlines/_search
{
  "track_total_hits": true
}

GET news_headlines/_search
{
  "query": {
    "range": {
      "data": {
        "gte": "2015-06-20",
        "lte": "2015-09-22"
      }
    }
  }
}

GET news_headlines/_search
{
  "aggs": {
    "by_category": {
      "terms": {
        "field": "category",
        "size": 100
      }
    }
  }
}

GET news_headlines/_search
{
  "query": {
    "match": {
      "category": "ENTERTAINMENT"
    }
  },
  "aggs": {
    "popular_in_entertainment": {
      "significant_text": {
        "field": "headline"
      }
    }
  }
}

GET news_headlines/_search
{
  "query": {
    "match": {
      "headline": {
        "query": "Elon Tesla SpaceX",
        "operator": "and"
      }
    }
  }
}


GET news_headlines/_search
{
  "query": {
    "match": {
      "headline": {
        "query": "Elon Tesla SpaceX",
        "minimum_should_match": 2
      }
    }
  }
}
```