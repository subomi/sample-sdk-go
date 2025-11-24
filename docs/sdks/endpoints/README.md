# Endpoints
(*Endpoints*)

## Overview

Endpoint related APIs

### Available Operations

* [DeleteEndpoint](#deleteendpoint) - Delete endpoint
* [GetEndpoint](#getendpoint) - Retrieve endpoint
* [UpdateEndpoint](#updateendpoint) - Update an endpoint
* [ActivateEndpoint](#activateendpoint) - Activate endpoint
* [ExpireSecret](#expiresecret) - Roll endpoint secret
* [PauseEndpoint](#pauseendpoint) - Pause endpoint

## DeleteEndpoint

This endpoint deletes an endpoint

### Example Usage

<!-- UsageSnippet language="go" operationID="DeleteEndpoint" method="delete" path="/v1/projects/{projectID}/endpoints/{endpointID}" -->
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

    res, err := s.Endpoints.DeleteEndpoint(ctx, "<id>", "<id>")
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
| `endpointID`                                          | *string*                                              | :heavy_check_mark:                                    | Endpoint ID                                           |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*DeleteEndpointResponse](../../deleteendpointresponse.md), error**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| convoy.DeleteEndpointBadRequestError   | 400                                    | application/json                       |
| convoy.DeleteEndpointUnauthorizedError | 401                                    | application/json                       |
| convoy.DeleteEndpointNotFoundError     | 404                                    | application/json                       |
| convoy.APIError                        | 4XX, 5XX                               | \*/\*                                  |

## GetEndpoint

This endpoint fetches an endpoint

### Example Usage

<!-- UsageSnippet language="go" operationID="GetEndpoint" method="get" path="/v1/projects/{projectID}/endpoints/{endpointID}" -->
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

    res, err := s.Endpoints.GetEndpoint(ctx, "<id>", "<id>")
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
| `endpointID`                                          | *string*                                              | :heavy_check_mark:                                    | Endpoint ID                                           |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*GetEndpointResponse](../../getendpointresponse.md), error**

### Errors

| Error Type                          | Status Code                         | Content Type                        |
| ----------------------------------- | ----------------------------------- | ----------------------------------- |
| convoy.GetEndpointBadRequestError   | 400                                 | application/json                    |
| convoy.GetEndpointUnauthorizedError | 401                                 | application/json                    |
| convoy.GetEndpointNotFoundError     | 404                                 | application/json                    |
| convoy.APIError                     | 4XX, 5XX                            | \*/\*                               |

## UpdateEndpoint

This endpoint updates an endpoint

### Example Usage

<!-- UsageSnippet language="go" operationID="UpdateEndpoint" method="put" path="/v1/projects/{projectID}/endpoints/{endpointID}" -->
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

    res, err := s.Endpoints.UpdateEndpoint(ctx, "<id>", "<id>", convoy.UpdateEndpoint{})
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
| `endpointID`                                          | *string*                                              | :heavy_check_mark:                                    | Endpoint ID                                           |
| `updateEndpoint`                                      | [UpdateEndpoint](../../updateendpoint.md)             | :heavy_check_mark:                                    | Endpoint Details                                      |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*UpdateEndpointResponse](../../updateendpointresponse.md), error**

### Errors

| Error Type                             | Status Code                            | Content Type                           |
| -------------------------------------- | -------------------------------------- | -------------------------------------- |
| convoy.UpdateEndpointBadRequestError   | 400                                    | application/json                       |
| convoy.UpdateEndpointUnauthorizedError | 401                                    | application/json                       |
| convoy.UpdateEndpointNotFoundError     | 404                                    | application/json                       |
| convoy.APIError                        | 4XX, 5XX                               | \*/\*                                  |

## ActivateEndpoint

Activated an inactive endpoint

### Example Usage

<!-- UsageSnippet language="go" operationID="ActivateEndpoint" method="post" path="/v1/projects/{projectID}/endpoints/{endpointID}/activate" -->
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

    res, err := s.Endpoints.ActivateEndpoint(ctx, "<id>", "<id>")
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
| `endpointID`                                          | *string*                                              | :heavy_check_mark:                                    | Endpoint ID                                           |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*ActivateEndpointResponse](../../activateendpointresponse.md), error**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| convoy.ActivateEndpointBadRequestError   | 400                                      | application/json                         |
| convoy.ActivateEndpointUnauthorizedError | 401                                      | application/json                         |
| convoy.ActivateEndpointNotFoundError     | 404                                      | application/json                         |
| convoy.APIError                          | 4XX, 5XX                                 | \*/\*                                    |

## ExpireSecret

This endpoint expires and re-generates the endpoint secret.

### Example Usage

<!-- UsageSnippet language="go" operationID="ExpireSecret" method="put" path="/v1/projects/{projectID}/endpoints/{endpointID}/expire_secret" -->
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

    res, err := s.Endpoints.ExpireSecret(ctx, "<id>", "<id>", convoy.ExpireSecret{})
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
| `endpointID`                                          | *string*                                              | :heavy_check_mark:                                    | Endpoint ID                                           |
| `expireSecret`                                        | [ExpireSecret](../../expiresecret.md)                 | :heavy_check_mark:                                    | Expire Secret Body Parameters                         |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*ExpireSecretResponse](../../expiresecretresponse.md), error**

### Errors

| Error Type                           | Status Code                          | Content Type                         |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
| convoy.ExpireSecretBadRequestError   | 400                                  | application/json                     |
| convoy.ExpireSecretUnauthorizedError | 401                                  | application/json                     |
| convoy.ExpireSecretNotFoundError     | 404                                  | application/json                     |
| convoy.APIError                      | 4XX, 5XX                             | \*/\*                                |

## PauseEndpoint

Toggles an endpoint's status between active and paused states

### Example Usage

<!-- UsageSnippet language="go" operationID="PauseEndpoint" method="put" path="/v1/projects/{projectID}/endpoints/{endpointID}/pause" -->
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

    res, err := s.Endpoints.PauseEndpoint(ctx, "<id>", "<id>")
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
| `endpointID`                                          | *string*                                              | :heavy_check_mark:                                    | Endpoint ID                                           |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*PauseEndpointResponse](../../pauseendpointresponse.md), error**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| convoy.PauseEndpointBadRequestError   | 400                                   | application/json                      |
| convoy.PauseEndpointUnauthorizedError | 401                                   | application/json                      |
| convoy.PauseEndpointNotFoundError     | 404                                   | application/json                      |
| convoy.APIError                       | 4XX, 5XX                              | \*/\*                                 |