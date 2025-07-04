# GraphQlRequests
(*GraphQlRequests*)

## Overview

### Available Operations

* [Submit](#submit) - Submit a valid GraphQL query or mutation
* [SubmitBulkQueryJob](#submitbulkqueryjob) - Submit a valid bulk GraphQL query

## Submit

This generic operation can be used to execute any valid GraphQL request.
To explore the available GraphQL operations, see the [GraphQL Schema Explorer](https://partner.thetradedesk.com/v3/portal/api/graphql-schema).

### Example Usage

```go
package main

import(
	"context"
	"os"
	ttdworkflows "ttd-workflows"
	"ttd-workflows/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.GraphQlRequests.Submit(ctx, &components.GraphQLRequestInput{
        Request: "<value>",
        Variables: &components.Variables{},
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                        | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `ctx`                                                                            | [context.Context](https://pkg.go.dev/context#Context)                            | :heavy_check_mark:                                                               | The context to use for the request.                                              |
| `request`                                                                        | [components.GraphQLRequestInput](../../models/components/graphqlrequestinput.md) | :heavy_check_mark:                                                               | The request object to use for the request.                                       |
| `opts`                                                                           | [][operations.Option](../../models/operations/option.md)                         | :heavy_minus_sign:                                                               | The options for this request.                                                    |

### Response

**[*operations.SubmitGraphQlRequestResponse](../../models/operations/submitgraphqlrequestresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 401, 403, 404            | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## SubmitBulkQueryJob

This generic operation can be used to execute any valid bulk GraphQL query.
For information on bulk GraphQL query syntax, see [GraphQL API Bulk Operations](https://partner.thetradedesk.com/v3/portal/api/doc/GqlBulkOperations).

### Example Usage

```go
package main

import(
	"context"
	"os"
	ttdworkflows "ttd-workflows"
	"ttd-workflows/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.GraphQlRequests.SubmitBulkQueryJob(ctx, &components.GraphQlQueryJobInput{
        Query: "<value>",
        CallbackInput: &components.GraphQlJobCallbackInput{
            CallbackURL: "https://wilted-cork.net/",
            CallbackHeaders: []components.KeyValuePairOfStringAndStringInput{
                components.KeyValuePairOfStringAndStringInput{
                    Key: ttdworkflows.String("<key>"),
                    Value: ttdworkflows.String("<value>"),
                },
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.GraphQlQueryJobResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `ctx`                                                                              | [context.Context](https://pkg.go.dev/context#Context)                              | :heavy_check_mark:                                                                 | The context to use for the request.                                                |
| `request`                                                                          | [components.GraphQlQueryJobInput](../../models/components/graphqlqueryjobinput.md) | :heavy_check_mark:                                                                 | The request object to use for the request.                                         |
| `opts`                                                                             | [][operations.Option](../../models/operations/option.md)                           | :heavy_minus_sign:                                                                 | The options for this request.                                                      |

### Response

**[*operations.SubmitGraphQlQueryJobResponse](../../models/operations/submitgraphqlqueryjobresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 401, 403, 404            | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |