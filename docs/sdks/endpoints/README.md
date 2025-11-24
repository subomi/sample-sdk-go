# Endpoints
(*Endpoints*)

## Overview

Endpoint related APIs

### Available Operations

* [PauseEndpoint](#pauseendpoint) - Pause endpoint

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