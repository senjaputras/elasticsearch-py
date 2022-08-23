# ELASTICSEARCH-PYTHON

## Some functions that I used to query/search data on Elasticsearch using Python

#### VERSIONS
Elasticsearch : 7.3.1

Python        : 3.9.13 -> Elastic-py modules : 7.17.4

- ### Connection to Elasticsearch
  ```
  es = Elasticsearch (["https://x.x.x.x:x"],basic_auth=("username", "password"),verify_certs=False,ssl_show_warn=False)
  ```
  I this case the Elasticsearch use Self Signed Certificate, so I disable certificate verify function.

- ### Search all indices
  ```
  body = { "match_all" : {}}
  ```
