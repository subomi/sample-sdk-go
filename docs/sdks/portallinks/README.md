# PortalLinks
(*PortalLinks*)

## Overview

Portal Links related APIs

### Available Operations

* [LoadPortalLinksPaged](#loadportallinkspaged) - List all portal links
* [CreatePortalLink](#createportallink) - Create a portal link
* [GetPortalLink](#getportallink) - Retrieve a portal link
* [GeneratePortalToken](#generateportaltoken) - Updates a portal link auth token
* [UpdatePortalLink](#updateportallink) - Update a portal link
* [RefreshPortalLinkAuthToken](#refreshportallinkauthtoken) - Get a portal link auth token
* [RevokePortalLink](#revokeportallink) - Revoke a portal link

## LoadPortalLinksPaged

This endpoint fetches multiple portal links

### Example Usage

<!-- UsageSnippet language="go" operationID="LoadPortalLinksPaged" method="get" path="/v1/projects/{projectID}/portal-links" -->
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

    res, err := s.PortalLinks.LoadPortalLinksPaged(ctx, convoy.LoadPortalLinksPagedRequest{
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

| Parameter                                                           | Type                                                                | Required                                                            | Description                                                         |
| ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------- |
| `ctx`                                                               | [context.Context](https://pkg.go.dev/context#Context)               | :heavy_check_mark:                                                  | The context to use for the request.                                 |
| `request`                                                           | [LoadPortalLinksPagedRequest](../../loadportallinkspagedrequest.md) | :heavy_check_mark:                                                  | The request object to use for the request.                          |
| `opts`                                                              | [][convoy.Option](../../option.md)                                  | :heavy_minus_sign:                                                  | The options for this request.                                       |

### Response

**[*LoadPortalLinksPagedResponse](../../loadportallinkspagedresponse.md), error**

### Errors

| Error Type                                   | Status Code                                  | Content Type                                 |
| -------------------------------------------- | -------------------------------------------- | -------------------------------------------- |
| convoy.LoadPortalLinksPagedBadRequestError   | 400                                          | application/json                             |
| convoy.LoadPortalLinksPagedUnauthorizedError | 401                                          | application/json                             |
| convoy.LoadPortalLinksPagedNotFoundError     | 404                                          | application/json                             |
| convoy.APIError                              | 4XX, 5XX                                     | \*/\*                                        |

## CreatePortalLink

This endpoint creates a portal link

### Example Usage

<!-- UsageSnippet language="go" operationID="CreatePortalLink" method="post" path="/v1/projects/{projectID}/portal-links" -->
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

    res, err := s.PortalLinks.CreatePortalLink(ctx, "<id>", convoy.PortalLink{})
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
| `portalLink`                                          | [PortalLink](../../portallink.md)                     | :heavy_check_mark:                                    | Portal Link Details                                   |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*CreatePortalLinkResponse](../../createportallinkresponse.md), error**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| convoy.CreatePortalLinkBadRequestError   | 400                                      | application/json                         |
| convoy.CreatePortalLinkUnauthorizedError | 401                                      | application/json                         |
| convoy.CreatePortalLinkNotFoundError     | 404                                      | application/json                         |
| convoy.APIError                          | 4XX, 5XX                                 | \*/\*                                    |

## GetPortalLink

This endpoint retrieves a portal link by its id.

### Example Usage

<!-- UsageSnippet language="go" operationID="GetPortalLink" method="get" path="/v1/projects/{projectID}/portal-links/{portalLinkID}" -->
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

    res, err := s.PortalLinks.GetPortalLink(ctx, "<id>", "<id>")
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
| `portalLinkID`                                        | *string*                                              | :heavy_check_mark:                                    | portal link id                                        |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*GetPortalLinkResponse](../../getportallinkresponse.md), error**

### Errors

| Error Type                            | Status Code                           | Content Type                          |
| ------------------------------------- | ------------------------------------- | ------------------------------------- |
| convoy.GetPortalLinkBadRequestError   | 400                                   | application/json                      |
| convoy.GetPortalLinkUnauthorizedError | 401                                   | application/json                      |
| convoy.GetPortalLinkNotFoundError     | 404                                   | application/json                      |
| convoy.APIError                       | 4XX, 5XX                              | \*/\*                                 |

## GeneratePortalToken

This endpoint retrieves a portal link by its id.

### Example Usage

<!-- UsageSnippet language="go" operationID="GeneratePortalToken" method="post" path="/v1/projects/{projectID}/portal-links/{portalLinkID}" -->
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

    res, err := s.PortalLinks.GeneratePortalToken(ctx, "<id>", "<id>")
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
| `portalLinkID`                                        | *string*                                              | :heavy_check_mark:                                    | portal link id                                        |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*GeneratePortalTokenResponse](../../generateportaltokenresponse.md), error**

### Errors

| Error Type                                  | Status Code                                 | Content Type                                |
| ------------------------------------------- | ------------------------------------------- | ------------------------------------------- |
| convoy.GeneratePortalTokenBadRequestError   | 400                                         | application/json                            |
| convoy.GeneratePortalTokenUnauthorizedError | 401                                         | application/json                            |
| convoy.GeneratePortalTokenNotFoundError     | 404                                         | application/json                            |
| convoy.APIError                             | 4XX, 5XX                                    | \*/\*                                       |

## UpdatePortalLink

This endpoint updates a portal link

### Example Usage

<!-- UsageSnippet language="go" operationID="UpdatePortalLink" method="put" path="/v1/projects/{projectID}/portal-links/{portalLinkID}" -->
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

    res, err := s.PortalLinks.UpdatePortalLink(ctx, "<id>", "<id>", convoy.PortalLink{})
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
| `portalLinkID`                                        | *string*                                              | :heavy_check_mark:                                    | portal link id                                        |
| `portalLink`                                          | [PortalLink](../../portallink.md)                     | :heavy_check_mark:                                    | Portal Link Details                                   |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*UpdatePortalLinkResponse](../../updateportallinkresponse.md), error**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| convoy.UpdatePortalLinkBadRequestError   | 400                                      | application/json                         |
| convoy.UpdatePortalLinkUnauthorizedError | 401                                      | application/json                         |
| convoy.UpdatePortalLinkNotFoundError     | 404                                      | application/json                         |
| convoy.APIError                          | 4XX, 5XX                                 | \*/\*                                    |

## RefreshPortalLinkAuthToken

This endpoint retrieves a portal link auth token

### Example Usage

<!-- UsageSnippet language="go" operationID="RefreshPortalLinkAuthToken" method="get" path="/v1/projects/{projectID}/portal-links/{portalLinkID}/refresh_token" -->
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

    res, err := s.PortalLinks.RefreshPortalLinkAuthToken(ctx, "<id>", "<id>")
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
| `portalLinkID`                                        | *string*                                              | :heavy_check_mark:                                    | portal link id                                        |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*RefreshPortalLinkAuthTokenResponse](../../refreshportallinkauthtokenresponse.md), error**

### Errors

| Error Type                                         | Status Code                                        | Content Type                                       |
| -------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------- |
| convoy.RefreshPortalLinkAuthTokenBadRequestError   | 400                                                | application/json                                   |
| convoy.RefreshPortalLinkAuthTokenUnauthorizedError | 401                                                | application/json                                   |
| convoy.RefreshPortalLinkAuthTokenNotFoundError     | 404                                                | application/json                                   |
| convoy.APIError                                    | 4XX, 5XX                                           | \*/\*                                              |

## RevokePortalLink

This endpoint revokes a portal link

### Example Usage

<!-- UsageSnippet language="go" operationID="RevokePortalLink" method="put" path="/v1/projects/{projectID}/portal-links/{portalLinkID}/revoke" -->
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

    res, err := s.PortalLinks.RevokePortalLink(ctx, "<id>", "<id>")
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
| `portalLinkID`                                        | *string*                                              | :heavy_check_mark:                                    | portal link id                                        |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*RevokePortalLinkResponse](../../revokeportallinkresponse.md), error**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| convoy.RevokePortalLinkBadRequestError   | 400                                      | application/json                         |
| convoy.RevokePortalLinkUnauthorizedError | 401                                      | application/json                         |
| convoy.RevokePortalLinkNotFoundError     | 404                                      | application/json                         |
| convoy.APIError                          | 4XX, 5XX                                 | \*/\*                                    |