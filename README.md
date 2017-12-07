# graphql

Low-level GraphQL client for Go.

* Simple, familiar API
* Build and execute any kind of GraphQL request

```go
ctx := context.Background()
ctx = graphql.NewContext(ctx, "https://machinebox.io/graphql")
r := graphql.NewRequest(`
    query ($key: String!) {
        items (id:$key) {
            field1
            field2
            field3
        }
    }
`)
r.Var("key", "value")
var res ResponseStruct
if err := r.Run(ctx, &resp); err != nil {
    log.Fatalln(err)
}
```