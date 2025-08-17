# MetaEvents
(*MetaEvents*)

## Overview

Meta Events related APIs

### Available Operations

* [GetMetaEventsPaged](#getmetaeventspaged) - List all meta events
* [GetMetaEvent](#getmetaevent) - Retrieve a meta event
* [ResendMetaEvent](#resendmetaevent) - Retry meta event

## GetMetaEventsPaged

This endpoint fetches meta events with pagination

### Example Usage

<!-- UsageSnippet language="go" operationID="GetMetaEventsPaged" method="get" path="/v1/projects/{projectID}/meta-events" -->
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

    res, err := s.MetaEvents.GetMetaEventsPaged(ctx, convoy.GetMetaEventsPagedRequest{
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

| Parameter                                                       | Type                                                            | Required                                                        | Description                                                     |
| --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------- |
| `ctx`                                                           | [context.Context](https://pkg.go.dev/context#Context)           | :heavy_check_mark:                                              | The context to use for the request.                             |
| `request`                                                       | [GetMetaEventsPagedRequest](../../getmetaeventspagedrequest.md) | :heavy_check_mark:                                              | The request object to use for the request.                      |
| `opts`                                                          | [][convoy.Option](../../option.md)                              | :heavy_minus_sign:                                              | The options for this request.                                   |

### Response

**[*GetMetaEventsPagedResponse](../../getmetaeventspagedresponse.md), error**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| convoy.GetMetaEventsPagedBadRequestError   | 400                                        | application/json                           |
| convoy.GetMetaEventsPagedUnauthorizedError | 401                                        | application/json                           |
| convoy.GetMetaEventsPagedNotFoundError     | 404                                        | application/json                           |
| convoy.APIError                            | 4XX, 5XX                                   | \*/\*                                      |

## GetMetaEvent

This endpoint retrieves a meta event

### Example Usage

<!-- UsageSnippet language="go" operationID="GetMetaEvent" method="get" path="/v1/projects/{projectID}/meta-events/{metaEventID}" -->
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

    res, err := s.MetaEvents.GetMetaEvent(ctx, "<id>", "<id>")
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
| `metaEventID`                                         | *string*                                              | :heavy_check_mark:                                    | meta event id                                         |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*GetMetaEventResponse](../../getmetaeventresponse.md), error**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| convoy.GetMetaEventBadRequestError   | 400                                  | application/json                     |
| convoy.GetMetaEventUnauthorizedError | 401                                  | application/json                     |
| convoy.GetMetaEventNotFoundError     | 404                                  | application/json                     |
| convoy.APIError                      | 4XX, 5XX                             | \*/\*                                |

## ResendMetaEvent

This endpoint retries a meta event

### Example Usage

<!-- UsageSnippet language="go" operationID="ResendMetaEvent" method="put" path="/v1/projects/{projectID}/meta-events/{metaEventID}/resend" -->
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

    res, err := s.MetaEvents.ResendMetaEvent(ctx, "<id>", "<id>")
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
| `metaEventID`                                         | *string*                                              | :heavy_check_mark:                                    | meta event id                                         |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*ResendMetaEventResponse](../../resendmetaeventresponse.md), error**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| convoy.ResendMetaEventBadRequestError   | 400                                     | application/json                        |
| convoy.ResendMetaEventUnauthorizedError | 401                                     | application/json                        |
| convoy.ResendMetaEventNotFoundError     | 404                                     | application/json                        |
| convoy.APIError                         | 4XX, 5XX                                | \*/\*                                   |