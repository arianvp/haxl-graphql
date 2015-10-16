We could create a type-level DSL similar to https://github.com/haskell-servant  for checking if user-supplied query is according to our schema

For a simplified version of graphql it would look something like this:

```
data Type fields 
data Field name typ arguments fields 
data  name := typ
data Value typ
data Fields fields

type User =
  Fields
   '[ "id"  := String
    , "name" := String
    , "friends" := User
    ]
```

We could then very similarly to servant traverse a query just like servant traverses a route

The problem of course is that we cant have cyclic type synonyms. So this might not be the correct direction.


The other solution is to have an AST for graphql schemas and write a type checker that uses this schema to validate queries.

