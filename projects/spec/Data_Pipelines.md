# Data Pipelines

Pulling in data from sources will allow user's to ease their manual contribution recording.


## Twitter

1. Query user's tweets
2. Filter to tweets with tags `@` and `#`
   - Check for specific tags
3. Show tweets in interface for minting

### API Endpoint


GET `https://twitter.com/api/tweets`

```json
{
    "name": "aarons",
}
```

## Github

### API Endpoint

GET `https://github.com/api/issues`

```json
{
    "name": "aarons",
}
```

