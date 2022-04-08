# Data Pipelines

Pulling in data from sources will allow user's to ease their manual contribution recording.


## Linear

What do we need to mark as contributions from linear activities?
- Tasks moving status?
- Task completion
- Auto attribute to current org?

### API Endpoint

GET `https://linear.app/api/tasks`

```json
{
    "name": "task-1"
}
```

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

