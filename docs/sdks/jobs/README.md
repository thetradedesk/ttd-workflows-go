# Jobs
(*Jobs*)

## Overview

### Available Operations

* [GetStatus](#getstatus) - Get the status of a previously submitted GraphQL query job.

## GetStatus

Use this operation to get a previously submitted GraphQL query job's status and completion percentage.
Once a job is complete, this operation will return the URL from which to download the job results.

### Example Usage

```go
package main

import(
	"context"
	"os"
	ttdworkflows "ttd-workflows"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.Jobs.GetStatus(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.GraphQLQueryJobRetrievalResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | N/A                                                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetGraphQlQueryJobStatusResponse](../../models/operations/getgraphqlqueryjobstatusresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 401, 403, 404            | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |