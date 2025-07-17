# RestRequests
(*RestRequests*)

## Overview

### Available Operations

* [Submit](#submit) - Submit a valid REST request

## Submit

This generic operation can be used to execute any valid REST request.
To explore the available REST operations, see the [REST API Reference](https://partner.thetradedesk.com/v3/portal/api/doc/ApiReferencePlatform).

### Example Usage

```go
package main

import(
	"context"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflowsgo.New(
        ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.RestRequests.Submit(ctx, &components.CallRestAPIWorkflowInput{
        MethodType: components.RestAPIMethodTypeGet,
        Endpoint: ttdworkflowsgo.String("<value>"),
        DataBody: ttdworkflowsgo.String("<value>"),
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

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `ctx`                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                      | :heavy_check_mark:                                                                         | The context to use for the request.                                                        |
| `request`                                                                                  | [components.CallRestAPIWorkflowInput](../../models/components/callrestapiworkflowinput.md) | :heavy_check_mark:                                                                         | The request object to use for the request.                                                 |
| `opts`                                                                                     | [][operations.Option](../../models/operations/option.md)                                   | :heavy_minus_sign:                                                                         | The options for this request.                                                              |

### Response

**[*operations.SubmitRestRequestResponse](../../models/operations/submitrestrequestresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 401, 403, 404            | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |