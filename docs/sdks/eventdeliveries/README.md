# EventDeliveries
(*EventDeliveries*)

## Overview

EventDelivery related APIs

### Available Operations

* [GetEventDeliveriesPaged](#geteventdeliveriespaged) - List all event deliveries
* [GetEventDelivery](#geteventdelivery) - Retrieve an event delivery
* [ResendEventDelivery](#resendeventdelivery) - Retry event delivery
* [BatchRetryEventDelivery](#batchretryeventdelivery) - Batch retry event delivery
* [ForceResendEventDeliveries](#forceresendeventdeliveries) - Force retry event delivery

## GetEventDeliveriesPaged

This endpoint retrieves all event deliveries paginated.

### Example Usage

<!-- UsageSnippet language="go" operationID="GetEventDeliveriesPaged" method="get" path="/v1/projects/{projectID}/eventdeliveries" -->
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

    res, err := s.EventDeliveries.GetEventDeliveriesPaged(ctx, convoy.GetEventDeliveriesPagedRequest{
        ProjectID: "<id>",
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

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `ctx`                                                                     | [context.Context](https://pkg.go.dev/context#Context)                     | :heavy_check_mark:                                                        | The context to use for the request.                                       |
| `request`                                                                 | [GetEventDeliveriesPagedRequest](../../geteventdeliveriespagedrequest.md) | :heavy_check_mark:                                                        | The request object to use for the request.                                |
| `opts`                                                                    | [][convoy.Option](../../option.md)                                        | :heavy_minus_sign:                                                        | The options for this request.                                             |

### Response

**[*GetEventDeliveriesPagedResponse](../../geteventdeliveriespagedresponse.md), error**

### Errors

| Error Type                                      | Status Code                                     | Content Type                                    |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| convoy.GetEventDeliveriesPagedBadRequestError   | 400                                             | application/json                                |
| convoy.GetEventDeliveriesPagedUnauthorizedError | 401                                             | application/json                                |
| convoy.GetEventDeliveriesPagedNotFoundError     | 404                                             | application/json                                |
| convoy.APIError                                 | 4XX, 5XX                                        | \*/\*                                           |

## GetEventDelivery

This endpoint fetches an event delivery.

### Example Usage

<!-- UsageSnippet language="go" operationID="GetEventDelivery" method="get" path="/v1/projects/{projectID}/eventdeliveries/{eventDeliveryID}" -->
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

    res, err := s.EventDeliveries.GetEventDelivery(ctx, "<id>", "<id>")
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

**[*GetEventDeliveryResponse](../../geteventdeliveryresponse.md), error**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| convoy.GetEventDeliveryBadRequestError   | 400                                      | application/json                         |
| convoy.GetEventDeliveryUnauthorizedError | 401                                      | application/json                         |
| convoy.GetEventDeliveryNotFoundError     | 404                                      | application/json                         |
| convoy.APIError                          | 4XX, 5XX                                 | \*/\*                                    |

## ResendEventDelivery

This endpoint retries an event delivery.

### Example Usage

<!-- UsageSnippet language="go" operationID="ResendEventDelivery" method="put" path="/v1/projects/{projectID}/eventdeliveries/{eventDeliveryID}/resend" -->
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

    res, err := s.EventDeliveries.ResendEventDelivery(ctx, "<id>", "<id>")
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

**[*ResendEventDeliveryResponse](../../resendeventdeliveryresponse.md), error**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| convoy.ResendEventDeliveryBadRequestError   | 400                                         | application/json                            |
| convoy.ResendEventDeliveryUnauthorizedError | 401                                         | application/json                            |
| convoy.ResendEventDeliveryNotFoundError     | 404                                         | application/json                            |
| convoy.APIError                             | 4XX, 5XX                                    | \*/\*                                       |

## BatchRetryEventDelivery

This endpoint batch retries multiple event deliveries at once.

### Example Usage

<!-- UsageSnippet language="go" operationID="BatchRetryEventDelivery" method="post" path="/v1/projects/{projectID}/eventdeliveries/batchretry" -->
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

    res, err := s.EventDeliveries.BatchRetryEventDelivery(ctx, convoy.BatchRetryEventDeliveryRequest{
        ProjectID: "<id>",
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

| Parameter                                                                 | Type                                                                      | Required                                                                  | Description                                                               |
| ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| `ctx`                                                                     | [context.Context](https://pkg.go.dev/context#Context)                     | :heavy_check_mark:                                                        | The context to use for the request.                                       |
| `request`                                                                 | [BatchRetryEventDeliveryRequest](../../batchretryeventdeliveryrequest.md) | :heavy_check_mark:                                                        | The request object to use for the request.                                |
| `opts`                                                                    | [][convoy.Option](../../option.md)                                        | :heavy_minus_sign:                                                        | The options for this request.                                             |

### Response

**[*BatchRetryEventDeliveryResponse](../../batchretryeventdeliveryresponse.md), error**

### Errors

| Error Type                                      | Status Code                                     | Content Type                                    |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| convoy.BatchRetryEventDeliveryBadRequestError   | 400                                             | application/json                                |
| convoy.BatchRetryEventDeliveryUnauthorizedError | 401                                             | application/json                                |
| convoy.BatchRetryEventDeliveryNotFoundError     | 404                                             | application/json                                |
| convoy.APIError                                 | 4XX, 5XX                                        | \*/\*                                           |

## ForceResendEventDeliveries

This endpoint enables you retry a previously successful event delivery

### Example Usage

<!-- UsageSnippet language="go" operationID="ForceResendEventDeliveries" method="post" path="/v1/projects/{projectID}/eventdeliveries/forceresend" -->
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

    res, err := s.EventDeliveries.ForceResendEventDeliveries(ctx, "<id>", convoy.IDs{})
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
| `iDs`                                                 | [IDs](../../ids.md)                                   | :heavy_check_mark:                                    | event delivery ids                                    |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*ForceResendEventDeliveriesResponse](../../forceresendeventdeliveriesresponse.md), error**

### Errors

| Error Type                                         | Status Code                                        | Content Type                                       |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| convoy.ForceResendEventDeliveriesBadRequestError   | 400                                                | application/json                                   |
| convoy.ForceResendEventDeliveriesUnauthorizedError | 401                                                | application/json                                   |
| convoy.ForceResendEventDeliveriesNotFoundError     | 404                                                | application/json                                   |
| convoy.APIError                                    | 4XX, 5XX                                           | \*/\*                                              |