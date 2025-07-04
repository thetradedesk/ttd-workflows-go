# GraphQLRequestInput

Required fields for executing a GraphQL query


## Fields

| Field                                   | Type                                    | Required                                | Description                             |
| --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- |
| `Request`                               | *string*                                | :heavy_check_mark:                      | The GraphQL query to execute.           |
| `Variables`                             | map[string]*any*                        | :heavy_minus_sign:                      | Variables to substitute into the query. |