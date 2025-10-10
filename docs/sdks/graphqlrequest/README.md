# GraphQLRequest
(*GraphQLRequest*)

## Overview

### Available Operations

* [SubmitGraphQlBulkQueryJob](#submitgraphqlbulkqueryjob) - Submit a valid bulk GraphQL query job

## SubmitGraphQlBulkQueryJob

This generic operation can be used to execute any valid bulk GraphQL query. To determine the job's
status, completion percentage, and URL for download (once the job results are ready), query the
[GraphQL Bulk Job Status](https://ttd-workflows.apidocumentation.com/reference#tag/job-status/get/graphqlbulkqueryjob/{id})
endpoint. For information on bulk GraphQL query syntax, see
[GraphQL API Bulk Operations](https://partner.thetradedesk.com/v3/portal/api/doc/GqlBulkOperations).

### Example Usage

<!-- UsageSnippet language="go" operationID="submitGraphQlBulkQueryJob" method="post" path="/graphqlbulkqueryjob" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.GraphQLRequest.SubmitGraphQlBulkQueryJob(ctx, &components.GraphQlQueryJobInput{
        Query: "<value>",
        CallbackInput: &components.GraphQlBulkJobCallbackInput{
            CallbackURL: "https://sociable-quinoa.info/",
            CallbackHeaders: nil,
        },
        BetaFeatures: ttdworkflows.Pointer("<value>"),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.GraphQlBulkJobResponse != nil {
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

**[*operations.SubmitGraphQlBulkQueryJobResponse](../../models/operations/submitgraphqlbulkqueryjobresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 401, 403, 404            | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |