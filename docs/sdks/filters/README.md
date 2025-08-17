# Filters
(*Filters*)

## Overview

### Available Operations

* [GetFilters](#getfilters) - List all filters
* [CreateFilter](#createfilter) - Create a new filter
* [DeleteFilter](#deletefilter) - Delete a filter
* [GetFilter](#getfilter) - Get a filter
* [UpdateFilter](#updatefilter) - Update a filter
* [BulkCreateFilters](#bulkcreatefilters) - Create multiple subscription filters
* [BulkUpdateFilters](#bulkupdatefilters) - Update multiple subscription filters
* [TestFilter](#testfilter) - Test a filter

## GetFilters

This endpoint fetches all filters for a subscription

### Example Usage

<!-- UsageSnippet language="go" operationID="GetFilters" method="get" path="/v1/projects/{projectID}/subscriptions/{subscriptionID}/filters" -->
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

    res, err := s.Filters.GetFilters(ctx, "<id>", "<id>")
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
| `subscriptionID`                                      | *string*                                              | :heavy_check_mark:                                    | Subscription ID                                       |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*GetFiltersResponse](../../getfiltersresponse.md), error**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| convoy.GetFiltersBadRequestError   | 400                                | application/json                   |
| convoy.GetFiltersUnauthorizedError | 401                                | application/json                   |
| convoy.GetFiltersNotFoundError     | 404                                | application/json                   |
| convoy.APIError                    | 4XX, 5XX                           | \*/\*                              |

## CreateFilter

This endpoint creates a new filter for a subscription

### Example Usage

<!-- UsageSnippet language="go" operationID="CreateFilter" method="post" path="/v1/projects/{projectID}/subscriptions/{subscriptionID}/filters" -->
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

    res, err := s.Filters.CreateFilter(ctx, "<id>", "<id>", convoy.CreateFilterRequest{
        EventType: "<value>",
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

| Parameter                                             | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `ctx`                                                 | [context.Context](https://pkg.go.dev/context#Context) | :heavy_check_mark:                                    | The context to use for the request.                   |
| `projectID`                                           | *string*                                              | :heavy_check_mark:                                    | Project ID                                            |
| `subscriptionID`                                      | *string*                                              | :heavy_check_mark:                                    | Subscription ID                                       |
| `createFilterRequest`                                 | [CreateFilterRequest](../../createfilterrequest.md)   | :heavy_check_mark:                                    | Filter to create                                      |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*CreateFilterResponse](../../createfilterresponse.md), error**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| convoy.CreateFilterBadRequestError   | 400                                  | application/json                     |
| convoy.CreateFilterUnauthorizedError | 401                                  | application/json                     |
| convoy.CreateFilterNotFoundError     | 404                                  | application/json                     |
| convoy.APIError                      | 4XX, 5XX                             | \*/\*                                |

## DeleteFilter

This endpoint deletes a filter

### Example Usage

<!-- UsageSnippet language="go" operationID="DeleteFilter" method="delete" path="/v1/projects/{projectID}/subscriptions/{subscriptionID}/filters/{filterID}" -->
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

    res, err := s.Filters.DeleteFilter(ctx, "<id>", "<id>", "<id>")
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
| `subscriptionID`                                      | *string*                                              | :heavy_check_mark:                                    | Subscription ID                                       |
| `filterID`                                            | *string*                                              | :heavy_check_mark:                                    | Filter ID                                             |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*DeleteFilterResponse](../../deletefilterresponse.md), error**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| convoy.DeleteFilterBadRequestError   | 400                                  | application/json                     |
| convoy.DeleteFilterUnauthorizedError | 401                                  | application/json                     |
| convoy.DeleteFilterNotFoundError     | 404                                  | application/json                     |
| convoy.APIError                      | 4XX, 5XX                             | \*/\*                                |

## GetFilter

This endpoint retrieves a single filter

### Example Usage

<!-- UsageSnippet language="go" operationID="GetFilter" method="get" path="/v1/projects/{projectID}/subscriptions/{subscriptionID}/filters/{filterID}" -->
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

    res, err := s.Filters.GetFilter(ctx, "<id>", "<id>", "<id>")
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
| `subscriptionID`                                      | *string*                                              | :heavy_check_mark:                                    | Subscription ID                                       |
| `filterID`                                            | *string*                                              | :heavy_check_mark:                                    | Filter ID                                             |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*GetFilterResponse](../../getfilterresponse.md), error**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| convoy.GetFilterBadRequestError   | 400                               | application/json                  |
| convoy.GetFilterUnauthorizedError | 401                               | application/json                  |
| convoy.GetFilterNotFoundError     | 404                               | application/json                  |
| convoy.APIError                   | 4XX, 5XX                          | \*/\*                             |

## UpdateFilter

This endpoint updates an existing filter

### Example Usage

<!-- UsageSnippet language="go" operationID="UpdateFilter" method="put" path="/v1/projects/{projectID}/subscriptions/{subscriptionID}/filters/{filterID}" -->
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

    res, err := s.Filters.UpdateFilter(ctx, "<id>", "<id>", "<id>", convoy.UpdateFilterRequest{})
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
| `subscriptionID`                                      | *string*                                              | :heavy_check_mark:                                    | Subscription ID                                       |
| `filterID`                                            | *string*                                              | :heavy_check_mark:                                    | Filter ID                                             |
| `updateFilterRequest`                                 | [UpdateFilterRequest](../../updatefilterrequest.md)   | :heavy_check_mark:                                    | Updated filter                                        |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*UpdateFilterResponse](../../updatefilterresponse.md), error**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| convoy.UpdateFilterBadRequestError   | 400                                  | application/json                     |
| convoy.UpdateFilterUnauthorizedError | 401                                  | application/json                     |
| convoy.UpdateFilterNotFoundError     | 404                                  | application/json                     |
| convoy.APIError                      | 4XX, 5XX                             | \*/\*                                |

## BulkCreateFilters

This endpoint creates multiple filters for a subscription

### Example Usage

<!-- UsageSnippet language="go" operationID="BulkCreateFilters" method="post" path="/v1/projects/{projectID}/subscriptions/{subscriptionID}/filters/bulk" -->
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

    res, err := s.Filters.BulkCreateFilters(ctx, "<id>", "<id>", []convoy.CreateFilterRequest{
        convoy.CreateFilterRequest{
            EventType: "<value>",
        },
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

| Parameter                                             | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `ctx`                                                 | [context.Context](https://pkg.go.dev/context#Context) | :heavy_check_mark:                                    | The context to use for the request.                   |
| `projectID`                                           | *string*                                              | :heavy_check_mark:                                    | Project ID                                            |
| `subscriptionID`                                      | *string*                                              | :heavy_check_mark:                                    | Subscription ID                                       |
| `requestBody`                                         | [][CreateFilterRequest](../../createfilterrequest.md) | :heavy_check_mark:                                    | Filters to create                                     |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*BulkCreateFiltersResponse](../../bulkcreatefiltersresponse.md), error**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| convoy.BulkCreateFiltersBadRequestError   | 400                                       | application/json                          |
| convoy.BulkCreateFiltersUnauthorizedError | 401                                       | application/json                          |
| convoy.BulkCreateFiltersNotFoundError     | 404                                       | application/json                          |
| convoy.APIError                           | 4XX, 5XX                                  | \*/\*                                     |

## BulkUpdateFilters

This endpoint updates multiple filters for a subscription

### Example Usage

<!-- UsageSnippet language="go" operationID="BulkUpdateFilters" method="put" path="/v1/projects/{projectID}/subscriptions/{subscriptionID}/filters/bulk_update" -->
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

    res, err := s.Filters.BulkUpdateFilters(ctx, "<id>", "<id>", []convoy.BulkUpdateFilterRequest{})
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
| `projectID`                                                   | *string*                                                      | :heavy_check_mark:                                            | Project ID                                                    |
| `subscriptionID`                                              | *string*                                                      | :heavy_check_mark:                                            | Subscription ID                                               |
| `requestBody`                                                 | [][BulkUpdateFilterRequest](../../bulkupdatefilterrequest.md) | :heavy_check_mark:                                            | Filters to update                                             |
| `opts`                                                        | [][convoy.Option](../../option.md)                            | :heavy_minus_sign:                                            | The options for this request.                                 |

### Response

**[*BulkUpdateFiltersResponse](../../bulkupdatefiltersresponse.md), error**

### Errors

| Error Type                                | Status Code                               | Content Type                              |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| convoy.BulkUpdateFiltersBadRequestError   | 400                                       | application/json                          |
| convoy.BulkUpdateFiltersUnauthorizedError | 401                                       | application/json                          |
| convoy.BulkUpdateFiltersNotFoundError     | 404                                       | application/json                          |
| convoy.APIError                           | 4XX, 5XX                                  | \*/\*                                     |

## TestFilter

This endpoint tests a filter against a payload

### Example Usage

<!-- UsageSnippet language="go" operationID="TestFilter" method="post" path="/v1/projects/{projectID}/subscriptions/{subscriptionID}/filters/test/{eventType}" -->
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

    res, err := s.Filters.TestFilter(ctx, "<id>", "<id>", "<value>", convoy.TestFilterRequest{
        Payload: "<value>",
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

| Parameter                                             | Type                                                  | Required                                              | Description                                           |
| ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| `ctx`                                                 | [context.Context](https://pkg.go.dev/context#Context) | :heavy_check_mark:                                    | The context to use for the request.                   |
| `projectID`                                           | *string*                                              | :heavy_check_mark:                                    | Project ID                                            |
| `subscriptionID`                                      | *string*                                              | :heavy_check_mark:                                    | Subscription ID                                       |
| `eventType`                                           | *string*                                              | :heavy_check_mark:                                    | Event Type                                            |
| `testFilterRequest`                                   | [TestFilterRequest](../../testfilterrequest.md)       | :heavy_check_mark:                                    | Payload to test                                       |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*TestFilterResponseResponse](../../testfilterresponseresponse.md), error**

### Errors

| Error Type                         | Status Code                        | Content Type                       |
| ---------------------------------- | ---------------------------------- | ---------------------------------- |
| convoy.TestFilterBadRequestError   | 400                                | application/json                   |
| convoy.TestFilterUnauthorizedError | 401                                | application/json                   |
| convoy.TestFilterNotFoundError     | 404                                | application/json                   |
| convoy.APIError                    | 4XX, 5XX                           | \*/\*                              |