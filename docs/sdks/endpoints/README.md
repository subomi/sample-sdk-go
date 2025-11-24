# Endpoints
(*Endpoints*)

## Overview

Endpoint related APIs

### Available Operations

* [ActivateEndpoint](#activateendpoint) - Activate endpoint
* [ExpireSecret](#expiresecret) - Roll endpoint secret
* [PauseEndpoint](#pauseendpoint) - Pause endpoint

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