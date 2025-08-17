# Sources
(*Sources*)

## Overview

Source related APIs

### Available Operations

* [LoadSourcesPaged](#loadsourcespaged) - List all sources
* [CreateSource](#createsource) - Create a source
* [DeleteSource](#deletesource) - Delete a source
* [GetSource](#getsource) - Retrieve a source
* [UpdateSource](#updatesource) - Update a source
* [TestSourceFunction](#testsourcefunction) - Validate source function

## LoadSourcesPaged

This endpoint fetches multiple sources

### Example Usage

<!-- UsageSnippet language="go" operationID="LoadSourcesPaged" method="get" path="/v1/projects/{projectID}/sources" -->
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

    res, err := s.Sources.LoadSourcesPaged(ctx, convoy.LoadSourcesPagedRequest{
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

| Parameter                                                   | Type                                                        | Required                                                    | Description                                                 |
| ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------- |
| `ctx`                                                       | [context.Context](https://pkg.go.dev/context#Context)       | :heavy_check_mark:                                          | The context to use for the request.                         |
| `request`                                                   | [LoadSourcesPagedRequest](../../loadsourcespagedrequest.md) | :heavy_check_mark:                                          | The request object to use for the request.                  |
| `opts`                                                      | [][convoy.Option](../../option.md)                          | :heavy_minus_sign:                                          | The options for this request.                               |

### Response

**[*LoadSourcesPagedResponse](../../loadsourcespagedresponse.md), error**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| convoy.LoadSourcesPagedBadRequestError   | 400                                      | application/json                         |
| convoy.LoadSourcesPagedUnauthorizedError | 401                                      | application/json                         |
| convoy.LoadSourcesPagedNotFoundError     | 404                                      | application/json                         |
| convoy.APIError                          | 4XX, 5XX                                 | \*/\*                                    |

## CreateSource

This endpoint creates a source

### Example Usage

<!-- UsageSnippet language="go" operationID="CreateSource" method="post" path="/v1/projects/{projectID}/sources" -->
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

    res, err := s.Sources.CreateSource(ctx, "<id>", convoy.CreateSource{})
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
| `createSource`                                        | [CreateSource](../../createsource.md)                 | :heavy_check_mark:                                    | Source Details                                        |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*CreateSourceResponse](../../createsourceresponse.md), error**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| convoy.CreateSourceBadRequestError   | 400                                  | application/json                     |
| convoy.CreateSourceUnauthorizedError | 401                                  | application/json                     |
| convoy.CreateSourceNotFoundError     | 404                                  | application/json                     |
| convoy.APIError                      | 4XX, 5XX                             | \*/\*                                |

## DeleteSource

This endpoint deletes a source

### Example Usage

<!-- UsageSnippet language="go" operationID="DeleteSource" method="delete" path="/v1/projects/{projectID}/sources/{sourceID}" -->
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

    res, err := s.Sources.DeleteSource(ctx, "<id>", "<id>")
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
| `sourceID`                                            | *string*                                              | :heavy_check_mark:                                    | source id                                             |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*DeleteSourceResponse](../../deletesourceresponse.md), error**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| convoy.DeleteSourceBadRequestError   | 400                                  | application/json                     |
| convoy.DeleteSourceUnauthorizedError | 401                                  | application/json                     |
| convoy.DeleteSourceNotFoundError     | 404                                  | application/json                     |
| convoy.APIError                      | 4XX, 5XX                             | \*/\*                                |

## GetSource

This endpoint retrieves a source by its id

### Example Usage

<!-- UsageSnippet language="go" operationID="GetSource" method="get" path="/v1/projects/{projectID}/sources/{sourceID}" -->
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

    res, err := s.Sources.GetSource(ctx, "<id>", "<id>")
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
| `sourceID`                                            | *string*                                              | :heavy_check_mark:                                    | Source ID                                             |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*GetSourceResponse](../../getsourceresponse.md), error**

### Errors

| Error Type                        | Status Code                       | Content Type                      |
| --------------------------------- | --------------------------------- | --------------------------------- |
| convoy.GetSourceBadRequestError   | 400                               | application/json                  |
| convoy.GetSourceUnauthorizedError | 401                               | application/json                  |
| convoy.GetSourceNotFoundError     | 404                               | application/json                  |
| convoy.APIError                   | 4XX, 5XX                          | \*/\*                             |

## UpdateSource

This endpoint updates a source

### Example Usage

<!-- UsageSnippet language="go" operationID="UpdateSource" method="put" path="/v1/projects/{projectID}/sources/{sourceID}" -->
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

    res, err := s.Sources.UpdateSource(ctx, "<id>", "<id>", convoy.UpdateSource{})
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
| `sourceID`                                            | *string*                                              | :heavy_check_mark:                                    | source id                                             |
| `updateSource`                                        | [UpdateSource](../../updatesource.md)                 | :heavy_check_mark:                                    | Source Details                                        |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*UpdateSourceResponse](../../updatesourceresponse.md), error**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| convoy.UpdateSourceBadRequestError   | 400                                  | application/json                     |
| convoy.UpdateSourceUnauthorizedError | 401                                  | application/json                     |
| convoy.UpdateSourceNotFoundError     | 404                                  | application/json                     |
| convoy.APIError                      | 4XX, 5XX                             | \*/\*                                |

## TestSourceFunction

This endpoint validates that a filter will match a certain payload structure.

### Example Usage

<!-- UsageSnippet language="go" operationID="TestSourceFunction" method="post" path="/v1/projects/{projectID}/sources/test_function" -->
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

    res, err := s.Sources.TestSourceFunction(ctx, "<id>", convoy.FunctionRequest{})
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
| `functionRequest`                                     | [FunctionRequest](../../functionrequest.md)           | :heavy_check_mark:                                    | Function Details                                      |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*TestSourceFunctionResponse](../../testsourcefunctionresponse.md), error**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| convoy.TestSourceFunctionBadRequestError   | 400                                        | application/json                           |
| convoy.TestSourceFunctionUnauthorizedError | 401                                        | application/json                           |
| convoy.TestSourceFunctionNotFoundError     | 404                                        | application/json                           |
| convoy.APIError                            | 4XX, 5XX                                   | \*/\*                                      |