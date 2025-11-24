# EventTypes
(*EventTypes*)

## Overview

### Available Operations

* [CreateEventType](#createeventtype) - Create an event type
* [UpdateEventType](#updateeventtype) - Updates an event type
* [DeprecateEventType](#deprecateeventtype) - Deprecates an event type
* [ImportOpenAPISpec](#importopenapispec) - Import event types from OpenAPI spec

## CreateEventType

This endpoint creates an event type

### Example Usage

<!-- UsageSnippet language="go" operationID="CreateEventType" method="post" path="/v1/projects/{projectID}/event-types" -->
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

    res, err := s.EventTypes.CreateEventType(ctx, "<id>", convoy.CreateEventType{})
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
| `createEventType`                                     | [CreateEventType](../../createeventtype.md)           | :heavy_check_mark:                                    | Event Type Details                                    |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*CreateEventTypeResponse](../../createeventtyperesponse.md), error**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| convoy.CreateEventTypeBadRequestError   | 400                                     | application/json                        |
| convoy.CreateEventTypeUnauthorizedError | 401                                     | application/json                        |
| convoy.CreateEventTypeNotFoundError     | 404                                     | application/json                        |
| convoy.APIError                         | 4XX, 5XX                                | \*/\*                                   |

## UpdateEventType

This endpoint updates an event type

### Example Usage

<!-- UsageSnippet language="go" operationID="UpdateEventType" method="put" path="/v1/projects/{projectID}/event-types/{eventTypeID}" -->
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

    res, err := s.EventTypes.UpdateEventType(ctx, "<id>", "<id>", convoy.UpdateEventType{})
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
| `eventTypeID`                                         | *string*                                              | :heavy_check_mark:                                    | Event Type ID                                         |
| `updateEventType`                                     | [UpdateEventType](../../updateeventtype.md)           | :heavy_check_mark:                                    | Event Type Details                                    |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*UpdateEventTypeResponse](../../updateeventtyperesponse.md), error**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| convoy.UpdateEventTypeBadRequestError   | 400                                     | application/json                        |
| convoy.UpdateEventTypeUnauthorizedError | 401                                     | application/json                        |
| convoy.UpdateEventTypeNotFoundError     | 404                                     | application/json                        |
| convoy.APIError                         | 4XX, 5XX                                | \*/\*                                   |

## DeprecateEventType

This endpoint deprecates an event type

### Example Usage

<!-- UsageSnippet language="go" operationID="DeprecateEventType" method="post" path="/v1/projects/{projectID}/event-types/{eventTypeId}/deprecate" -->
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

    res, err := s.EventTypes.DeprecateEventType(ctx, "<id>", "<id>")
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
| `eventTypeID`                                         | *string*                                              | :heavy_check_mark:                                    | Event Type ID                                         |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*DeprecateEventTypeResponse](../../deprecateeventtyperesponse.md), error**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| convoy.DeprecateEventTypeBadRequestError   | 400                                        | application/json                           |
| convoy.DeprecateEventTypeUnauthorizedError | 401                                        | application/json                           |
| convoy.DeprecateEventTypeNotFoundError     | 404                                        | application/json                           |
| convoy.APIError                            | 4XX, 5XX                                   | \*/\*                                      |

## ImportOpenAPISpec

This endpoint imports event types from an OpenAPI specification

### Example Usage

<!-- UsageSnippet language="go" operationID="ImportOpenApiSpec" method="post" path="/v1/projects/{projectID}/event-types/import" -->
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

    res, err := s.EventTypes.ImportOpenAPISpec(ctx, "<id>", convoy.ImportOpenAPISpec{})
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
| `importOpenAPISpec`                                   | [ImportOpenAPISpec](../../importopenapispec.md)       | :heavy_check_mark:                                    | OpenAPI specification                                 |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*ImportOpenAPISpecResponse](../../importopenapispecresponse.md), error**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| convoy.ImportOpenAPISpecBadRequestError   | 400                                       | application/json                          |
| convoy.ImportOpenAPISpecUnauthorizedError | 401                                       | application/json                          |
| convoy.ImportOpenAPISpecNotFoundError     | 404                                       | application/json                          |
| convoy.APIError                           | 4XX, 5XX                                  | \*/\*                                     |