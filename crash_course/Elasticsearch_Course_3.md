# Part 3: Running full text queries and combined queries with Elasticsearch and Kibana
```
GET news_headlines/_search

GET news_headlines/_search
{
  "aggregations": {
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
      "headline": {
        "query": "Shape of you"
      }
    }
  }
}

GET news_headlines/_search
{
  "query": {
    "match_phrase": {
      "headline": {
        "query": "Shape of You"
      }
    }
  }
}

GET news_headlines/_search
{
  "query": {
    "multi_match": {
      "query": "Michelle Obama",
      "fields": [
          "headline",
          "short_description",
          "authors"
        ]
    }
  }
}

GET news_headlines/_search
{
  "query": {
    "multi_match": {
      "query": "Michelle Obama",
      "fields": [
          "headline^2",
          "short_description",
          "authors"
        ]
    }
  }
}


GET news_headlines/_search
{
  "query": {
    "multi_match": {
      "query": "party planning",
      "fields": [
          "headline^2",
          "short_description"
        ]
    }
  }
}

GET news_headlines/_search
{
  "query": {
    "multi_match": {
      "query": "party planning",
      "fields": [
          "headline^2",
          "short_description"
        ],
        "type": "phrase"
    }
  }
}

GET news_headlines/_search
{
  "query": {
    "match_phrase": {
      "headline": "Michelle Obama"
    }
  },
  "aggs": {
    "category_mentions": {
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
    "bool": {
      "must": [
        {
          "match_phrase": {
            "headline": "Michelle Obama"
          }
        },
        {
          "match": {
            "category": "POLITICS"
          }
        }
        ]
    }
  }
}

GET news_headlines/_search
{
  "query": {
    "bool": {
      "must": {
        "match_phrase": {
          "headline": "Michelle Obama"
        }
      },
      "must_not": [
        {
          "match": {
            "category": "WEDDINGS"
          }
        }
      ]
    }
  }
}

GET news_headlines/_search
{
  "query": {
    "bool": {
      "must": [
        {
          "match_phrase": {
            "headline": "Michelle Obama"
          }
        }
        ],
        "should": [
          {
            "match_phrase": {
              "category": "BLACK VOICE"
            }
          }
        ]
    }
  }
}

GET news_headlines/_search
{
  "query": {
    "bool": {
      "must": [
          {
            "match_phrase": {
              "headline": "Michelle Obama"
            }
          }
        ],
        "filter": {
          "range": {
            "date": {
              "gte": "2014-03-25",
              "lte": "2016-03-25"
            }
          }
        }
    }
  }
}


GET news_headlines/_search
{
  "query": {
    "bool": {
      "must": [
          {
            "match_phrase": {
              "headline": "Michelle Obama"
            }
          }
        ],
        "should": [
          { 
            "match": {
              "headline" : "Becoming"
            }
          },
          {
            "match": {
              "headline": "women"
            }
          },
          {
            "match": {
              "headline": "empower"
            }
          }
          ]
    }
  }
}
```