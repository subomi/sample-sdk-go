# Events
(*Events*)

## Overview

Event related APIs

### Available Operations

* [CreateEndpointEvent](#createendpointevent) - Create an event

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
	"github.com/frain-dev/convoy/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := convoy.New(
        convoy.WithSecurity(os.Getenv("CONVOY_API_KEY_AUTH")),
    )

    res, err := s.Events.CreateEndpointEvent(ctx, "<id>", components.ModelsCreateEvent{})
    if err != nil {
        log.Fatal(err)
    }
    if res.Object != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                    | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `ctx`                                                                        | [context.Context](https://pkg.go.dev/context#Context)                        | :heavy_check_mark:                                                           | The context to use for the request.                                          |
| `projectID`                                                                  | *string*                                                                     | :heavy_check_mark:                                                           | Project ID                                                                   |
| `modelsCreateEvent`                                                          | [components.ModelsCreateEvent](../../models/components/modelscreateevent.md) | :heavy_check_mark:                                                           | Event Details                                                                |
| `opts`                                                                       | [][operations.Option](../../models/operations/option.md)                     | :heavy_minus_sign:                                                           | The options for this request.                                                |

### Response

**[*operations.CreateEndpointEventResponse](../../models/operations/createendpointeventresponse.md), error**

### Errors

| Error Type                  | Status Code                 | Content Type                |
| --------------------------- | --------------------------- | --------------------------- |
| apierrors.BadRequestError   | 400                         | application/json            |
| apierrors.UnauthorizedError | 401                         | application/json            |
| apierrors.NotFoundError     | 404                         | application/json            |
| apierrors.APIError          | 4XX, 5XX                    | \*/\*                       |