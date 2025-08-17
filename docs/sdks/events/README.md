# Events
(*Events*)

## Overview

Event related APIs

### Available Operations

* [GetEventsPaged](#geteventspaged) - List all events
* [CreateEndpointEvent](#createendpointevent) - Create an event
* [GetEndpointEvent](#getendpointevent) - Retrieve an event
* [ReplayEndpointEvent](#replayendpointevent) - Replay event
* [BatchReplayEvents](#batchreplayevents) - Batch replay events
* [CreateBroadcastEvent](#createbroadcastevent) - Create a broadcast event
* [CreateDynamicEvent](#createdynamicevent) - Dynamic Events
* [CreateEndpointFanoutEvent](#createendpointfanoutevent) - Fan out an event

## GetEventsPaged

This endpoint fetches app events with pagination

### Example Usage

<!-- UsageSnippet language="go" operationID="GetEventsPaged" method="get" path="/v1/projects/{projectID}/events" -->
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

    res, err := s.Events.GetEventsPaged(ctx, convoy.GetEventsPagedRequest{
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

| Parameter                                               | Type                                                    | Required                                                | Description                                             |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `ctx`                                                   | [context.Context](https://pkg.go.dev/context#Context)   | :heavy_check_mark:                                      | The context to use for the request.                     |
| `request`                                               | [GetEventsPagedRequest](../../geteventspagedrequest.md) | :heavy_check_mark:                                      | The request object to use for the request.              |
| `opts`                                                  | [][convoy.Option](../../option.md)                      | :heavy_minus_sign:                                      | The options for this request.                           |

### Response

**[*GetEventsPagedResponse](../../geteventspagedresponse.md), error**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| convoy.GetEventsPagedBadRequestError   | 400                                    | application/json                       |
| convoy.GetEventsPagedUnauthorizedError | 401                                    | application/json                       |
| convoy.GetEventsPagedNotFoundError     | 404                                    | application/json                       |
| convoy.APIError                        | 4XX, 5XX                               | \*/\*                                  |

## CreateEndpointEvent

This endpoint creates an endpoint event

### Example Usage

<!-- UsageSnippet language="go" operationID="CreateEndpointEvent" method="post" path="/v1/projects/{projectID}/events" -->
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

    res, err := s.Events.CreateEndpointEvent(ctx, "<id>", convoy.CreateEvent{})
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
| `createEvent`                                         | [CreateEvent](../../createevent.md)                   | :heavy_check_mark:                                    | Event Details                                         |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*CreateEndpointEventResponse](../../createendpointeventresponse.md), error**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| convoy.CreateEndpointEventBadRequestError   | 400                                         | application/json                            |
| convoy.CreateEndpointEventUnauthorizedError | 401                                         | application/json                            |
| convoy.CreateEndpointEventNotFoundError     | 404                                         | application/json                            |
| convoy.APIError                             | 4XX, 5XX                                    | \*/\*                                       |

## GetEndpointEvent

This endpoint retrieves an event

### Example Usage

<!-- UsageSnippet language="go" operationID="GetEndpointEvent" method="get" path="/v1/projects/{projectID}/events/{eventID}" -->
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

    res, err := s.Events.GetEndpointEvent(ctx, "<id>", "<id>")
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
| `eventID`                                             | *string*                                              | :heavy_check_mark:                                    | event id                                              |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*GetEndpointEventResponse](../../getendpointeventresponse.md), error**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| convoy.GetEndpointEventBadRequestError   | 400                                      | application/json                         |
| convoy.GetEndpointEventUnauthorizedError | 401                                      | application/json                         |
| convoy.GetEndpointEventNotFoundError     | 404                                      | application/json                         |
| convoy.APIError                          | 4XX, 5XX                                 | \*/\*                                    |

## ReplayEndpointEvent

This endpoint replays an event afresh assuming it is a new event.

### Example Usage

<!-- UsageSnippet language="go" operationID="ReplayEndpointEvent" method="put" path="/v1/projects/{projectID}/events/{eventID}/replay" -->
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

    res, err := s.Events.ReplayEndpointEvent(ctx, "<id>", "<id>")
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
| `eventID`                                             | *string*                                              | :heavy_check_mark:                                    | event id                                              |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*ReplayEndpointEventResponse](../../replayendpointeventresponse.md), error**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| convoy.ReplayEndpointEventBadRequestError   | 400                                         | application/json                            |
| convoy.ReplayEndpointEventUnauthorizedError | 401                                         | application/json                            |
| convoy.ReplayEndpointEventNotFoundError     | 404                                         | application/json                            |
| convoy.APIError                             | 4XX, 5XX                                    | \*/\*                                       |

## BatchReplayEvents

This endpoint replays multiple events at once.

### Example Usage

<!-- UsageSnippet language="go" operationID="BatchReplayEvents" method="post" path="/v1/projects/{projectID}/events/batchreplay" -->
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

    res, err := s.Events.BatchReplayEvents(ctx, convoy.BatchReplayEventsRequest{
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

| Parameter                                                     | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `ctx`                                                         | [context.Context](https://pkg.go.dev/context#Context)         | :heavy_check_mark:                                            | The context to use for the request.                           |
| `request`                                                     | [BatchReplayEventsRequest](../../batchreplayeventsrequest.md) | :heavy_check_mark:                                            | The request object to use for the request.                    |
| `opts`                                                        | [][convoy.Option](../../option.md)                            | :heavy_minus_sign:                                            | The options for this request.                                 |

### Response

**[*BatchReplayEventsResponse](../../batchreplayeventsresponse.md), error**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| convoy.BatchReplayEventsBadRequestError   | 400                                       | application/json                          |
| convoy.BatchReplayEventsUnauthorizedError | 401                                       | application/json                          |
| convoy.BatchReplayEventsNotFoundError     | 404                                       | application/json                          |
| convoy.APIError                           | 4XX, 5XX                                  | \*/\*                                     |

## CreateBroadcastEvent

This endpoint creates a event that is broadcast to every endpoint whose subscription matches the given event type.

### Example Usage

<!-- UsageSnippet language="go" operationID="CreateBroadcastEvent" method="post" path="/v1/projects/{projectID}/events/broadcast" -->
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

    res, err := s.Events.CreateBroadcastEvent(ctx, "<id>", convoy.BroadcastEvent{})
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
| `broadcastEvent`                                      | [BroadcastEvent](../../broadcastevent.md)             | :heavy_check_mark:                                    | Broadcast Event Details                               |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*CreateBroadcastEventResponse](../../createbroadcasteventresponse.md), error**

### Errors

| Error Type                                   | Status Code                                  | Content Type                                 |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| convoy.CreateBroadcastEventBadRequestError   | 400                                          | application/json                             |
| convoy.CreateBroadcastEventUnauthorizedError | 401                                          | application/json                             |
| convoy.CreateBroadcastEventNotFoundError     | 404                                          | application/json                             |
| convoy.APIError                              | 4XX, 5XX                                     | \*/\*                                        |

## CreateDynamicEvent

This endpoint does not require creating endpoint and subscriptions ahead of time. Instead, you supply the endpoint and the payload, and Convoy delivers the events

### Example Usage

<!-- UsageSnippet language="go" operationID="CreateDynamicEvent" method="post" path="/v1/projects/{projectID}/events/dynamic" -->
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

    res, err := s.Events.CreateDynamicEvent(ctx, "<id>", convoy.DynamicEvent{})
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
| `dynamicEvent`                                        | [DynamicEvent](../../dynamicevent.md)                 | :heavy_check_mark:                                    | Event Details                                         |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*CreateDynamicEventResponse](../../createdynamiceventresponse.md), error**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| convoy.CreateDynamicEventBadRequestError   | 400                                        | application/json                           |
| convoy.CreateDynamicEventUnauthorizedError | 401                                        | application/json                           |
| convoy.CreateDynamicEventNotFoundError     | 404                                        | application/json                           |
| convoy.APIError                            | 4XX, 5XX                                   | \*/\*                                      |

## CreateEndpointFanoutEvent

This endpoint uses the owner_id to fan out an event to multiple endpoints.

### Example Usage

<!-- UsageSnippet language="go" operationID="CreateEndpointFanoutEvent" method="post" path="/v1/projects/{projectID}/events/fanout" -->
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

    res, err := s.Events.CreateEndpointFanoutEvent(ctx, "<id>", convoy.FanoutEvent{})
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
| `fanoutEvent`                                         | [FanoutEvent](../../fanoutevent.md)                   | :heavy_check_mark:                                    | Event Details                                         |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*CreateEndpointFanoutEventResponse](../../createendpointfanouteventresponse.md), error**

### Errors

| Error Type                                        | Status Code                                       | Content Type                                      |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| convoy.CreateEndpointFanoutEventBadRequestError   | 400                                               | application/json                                  |
| convoy.CreateEndpointFanoutEventUnauthorizedError | 401                                               | application/json                                  |
| convoy.CreateEndpointFanoutEventNotFoundError     | 404                                               | application/json                                  |
| convoy.APIError                                   | 4XX, 5XX                                          | \*/\*                                             |