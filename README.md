# ELASTICSEARCH-PYTHON

## Some functions that I used to query/search data on Elasticsearch using Python

#### VERSIONS
Elasticsearch : 7.3.1

Python        : 3.9.13 -> Elastic-py modules : 7.17.4

  _**Each Elasticsearch version use different elastic-py modules version**_


## QUERY EXAMPLES

  ```
  es = Elasticsearch (["https://x.x.x.x:x"],basic_auth=("username", "password"),verify_certs=False,ssl_show_warn=False)
  body = { "match_all" : {}}
  source_index='index-test-*'
  batch_size='10000'
  data={
      "bool": {
        "must": [
          {
            "range": {
              "startTime": {
                "format": "strict_date_optional_time",
                "gte": "now-1m",
                "lte": "now"
              }
            }
          }
        ],
        "should": [],
        "must_not": []
      }
    }
  rs = es_src.search(index=[source_index],query=data,size=batch_size,_source_excludes=["dns.response","http.response"])
  ```

## EXPLAINATIONS

- ### Connecting to Elasticsearch
  ```
  es = Elasticsearch (["https://x.x.x.x:x"],basic_auth=("username", "password"),verify_certs=False,ssl_show_warn=False)
  ```
  In this case the Elasticsearch use Self Signed Certificate, so I disable certificate verify function.

- ### Query / Search to find all indices
  ```
  body = { "match_all" : {}}
  ```
- ### Parameter document/data size/line
  ```
  batch_size='10000'
  ```


- ### Query / Search with Time Range
  ```
  data={
    "bool": {
      "must": [
        {
          "range": {
            "startTime": {
              "format": "strict_date_optional_time",
              "gte": "now-1m",
              "lte": "now"
            }
          }
        }
      ],
      "should": [],
      "must_not": []
    }
  }
  ```
- ### Query / Search Executions
  ```
  rs = es_src.search(index=[source_index],query=data,size=batch_size,_source_excludes=["dns.response","http.response"])
  ```
  I added parameter __source_excludes__ , this parameter is used if we want to exclude some fields.
