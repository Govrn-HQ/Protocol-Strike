# Subgraph


## Entities


```gql
Contribution {
    name # string, from event
    attestations # Attestation entity
}
```

```gql
User {
    address # string
}
```

```gql
Attestation {
    user # User entity
}
```
