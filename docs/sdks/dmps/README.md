# Dmps
(*Dmps*)

## Overview

### Available Operations

* [GetFirstPartyDataJob](#getfirstpartydatajob) - Submit a job for first-party data retrieval for an advertiser
* [GetThirdPartyDataJob](#getthirdpartydatajob) - Submit a job for third-party data retrieval for a partner

## GetFirstPartyDataJob

When a first-party data query is submitted, a job ID is returned.
This job ID can be used to poll for the job's status using the associated operation under "Job Status".

### Example Usage

<!-- UsageSnippet language="go" operationID="getFirstPartyDataJob" method="post" path="/standardjob/firstpartydata" -->
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

    res, err := s.Dmps.GetFirstPartyDataJob(ctx, &components.FirstPartyDataInput{
        AdvertiserID: "<id>",
        NameFilter: ttdworkflows.String("<value>"),
        QueryShape: ttdworkflows.String("<value>"),
        CallbackInput: &components.WorkflowCallbackInput{
            CallbackURL: "https://difficult-pocket-watch.com",
            CallbackHeaders: map[string]string{
                "key": "<value>",
                "key1": "<value>",
                "key2": "<value>",
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.StandardJobSubmitResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                        | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `ctx`                                                                            | [context.Context](https://pkg.go.dev/context#Context)                            | :heavy_check_mark:                                                               | The context to use for the request.                                              |
| `request`                                                                        | [components.FirstPartyDataInput](../../models/components/firstpartydatainput.md) | :heavy_check_mark:                                                               | The request object to use for the request.                                       |
| `opts`                                                                           | [][operations.Option](../../models/operations/option.md)                         | :heavy_minus_sign:                                                               | The options for this request.                                                    |

### Response

**[*operations.GetFirstPartyDataJobResponse](../../models/operations/getfirstpartydatajobresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 401, 403, 404            | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetThirdPartyDataJob

When a third-party data query is submitted, a job ID is returned.
This job ID can be used to poll for the job's status, and when complete, the results download link,
using the associated operation under "Job Status".

### Example Usage

<!-- UsageSnippet language="go" operationID="getThirdPartyDataJob" method="post" path="/standardjob/thirdpartydata" -->
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

    res, err := s.Dmps.GetThirdPartyDataJob(ctx, &components.ThirdPartyDataInput{
        PartnerID: "<id>",
        QueryShape: ttdworkflows.String("<value>"),
        CallbackInput: &components.WorkflowCallbackInput{
            CallbackURL: "https://extroverted-intent.net",
            CallbackHeaders: map[string]string{
                "key": "<value>",
                "key1": "<value>",
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.StandardJobSubmitResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                        | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `ctx`                                                                            | [context.Context](https://pkg.go.dev/context#Context)                            | :heavy_check_mark:                                                               | The context to use for the request.                                              |
| `request`                                                                        | [components.ThirdPartyDataInput](../../models/components/thirdpartydatainput.md) | :heavy_check_mark:                                                               | The request object to use for the request.                                       |
| `opts`                                                                           | [][operations.Option](../../models/operations/option.md)                         | :heavy_minus_sign:                                                               | The options for this request.                                                    |

### Response

**[*operations.GetThirdPartyDataJobResponse](../../models/operations/getthirdpartydatajobresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 401, 403, 404            | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |