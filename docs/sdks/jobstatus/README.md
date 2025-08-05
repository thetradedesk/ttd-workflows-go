# JobStatus
(*JobStatus*)

## Overview

### Available Operations

* [Get](#get) - Get the status of a previously submitted job

## Get

Use this operation to get a previously submitted job's status and completion percentage.
Once a job is complete, this operation will return the URL from which to download the job results.
            
Job results expire after 24 hours, at which point you will need to submit a new job.

### Example Usage

<!-- UsageSnippet language="go" operationID="getJobStatus" method="get" path="/standardjob/{id}/status" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.JobStatus.Get(ctx, 412651)
    if err != nil {
        log.Fatal(err)
    }
    if res.StandardJobStatusResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *int64*                                                  | :heavy_check_mark:                                       | N/A                                                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetJobStatusResponse](../../models/operations/getjobstatusresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 401, 403, 404            | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |