# Part 1: Intro to Elasticsearch & Kibana
Youtube Crash Course at [1](https://github.com/LisaHJung/Part-1-Intro-to-Elasticsearch-and-Kibana)

```bash
GET _cluster/health

GET _nodes/stats

// create index
PUT favorite_candy

// index document (document _id is created by elastic)
POST favorite_candy/_doc
{
  "firstname": "Lisa",
  "candy": "Sour Skittles"
}

// index document (client must provide _id value)
PUT favorite_candy/_doc/1
{
  "first_name": "John",
  "candy": "Starbust"
}

// this gives an error, because doc with _id 1 is already created
PUT favorite_candy/_create/1
{
  "first_name": "Finn",
  "candy": "Jolly Ranchers"
}

GET favorite_candy/_doc/1


DELETE favorite_candy/_doc/1

// Task Home Assignment
PUT desctinations

PUT desctinations/_create/1
{
  "name": "Berlin"
}

PUT desctinations/_doc/2
{
  "name": "Stockholm"
}

PUT desctinations/_doc/3
{
  "name": "Sydney"
}

PUT desctinations/_doc/4
{
  "name": "Kuala Lumpur"
}

PUT desctinations/_doc/5
{
  "name": "Bukhara"
}

GET desctinations/_doc/2

PUT desctinations/_doc/2
{
  "name": "Helsenki"
}

GET desctinations/_doc/2

DELETE desctinations/_doc/2

GET desctinations/_search
{
  "query": {
    "match_all": {}
  }
}





```