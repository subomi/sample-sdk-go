# DeliveryAttempts
(*DeliveryAttempts*)

## Overview

Delivery Attempt related APIs

### Available Operations

* [GetDeliveryAttempts](#getdeliveryattempts) - List delivery attempts
* [GetDeliveryAttempt](#getdeliveryattempt) - Retrieve a delivery attempt

## GetDeliveryAttempts

This endpoint fetches an app message's delivery attempts

### Example Usage

<!-- UsageSnippet language="go" operationID="GetDeliveryAttempts" method="get" path="/v1/projects/{projectID}/eventdeliveries/{eventDeliveryID}/deliveryattempts" -->
```go
package main

import(
	"context"
	"os"
	"github.com/frain-dev/convoy"
	"log"
)

func main() {
    ctx := context.Background()

    s := convoy.New(
        convoy.WithSecurity(os.Getenv("CONVOY_BEARER_AUTH")),
    )

    res, err := s.DeliveryAttempts.GetDeliveryAttempts(ctx, "<id>", "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                             | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `ctx`                                                 | [context.Context](https://pkg.go.dev/context#Context) | :heavy_check_mark:                                    | The context to use for the request.                   |
| `projectID`                                           | *string*                                              | :heavy_check_mark:                                    | Project ID                                            |
| `eventDeliveryID`                                     | *string*                                              | :heavy_check_mark:                                    | event delivery id                                     |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*GetDeliveryAttemptsResponse](../../getdeliveryattemptsresponse.md), error**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| convoy.GetDeliveryAttemptsBadRequestError   | 400                                         | application/json                            |
| convoy.GetDeliveryAttemptsUnauthorizedError | 401                                         | application/json                            |
| convoy.GetDeliveryAttemptsNotFoundError     | 404                                         | application/json                            |
| convoy.APIError                             | 4XX, 5XX                                    | \*/\*                                       |

## GetDeliveryAttempt

This endpoint fetches an app event delivery attempt

### Example Usage

<!-- UsageSnippet language="go" operationID="GetDeliveryAttempt" method="get" path="/v1/projects/{projectID}/eventdeliveries/{eventDeliveryID}/deliveryattempts/{deliveryAttemptID}" -->
```go
package main

import(
	"context"
	"os"
	"github.com/frain-dev/convoy"
	"log"
)

func main() {
    ctx := context.Background()

    s := convoy.New(
        convoy.WithSecurity(os.Getenv("CONVOY_BEARER_AUTH")),
    )

    res, err := s.DeliveryAttempts.GetDeliveryAttempt(ctx, "<id>", "<id>", "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                             | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `ctx`                                                 | [context.Context](https://pkg.go.dev/context#Context) | :heavy_check_mark:                                    | The context to use for the request.                   |
| `projectID`                                           | *string*                                              | :heavy_check_mark:                                    | Project ID                                            |
| `eventDeliveryID`                                     | *string*                                              | :heavy_check_mark:                                    | event delivery id                                     |
| `deliveryAttemptID`                                   | *string*                                              | :heavy_check_mark:                                    | delivery attempt id                                   |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*GetDeliveryAttemptResponse](../../getdeliveryattemptresponse.md), error**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| convoy.GetDeliveryAttemptBadRequestError   | 400                                        | application/json                           |
| convoy.GetDeliveryAttemptUnauthorizedError | 401                                        | application/json                           |
| convoy.GetDeliveryAttemptNotFoundError     | 404                                        | application/json                           |
| convoy.APIError                            | 4XX, 5XX                                   | \*/\*                                      |