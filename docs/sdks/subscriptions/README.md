# Subscriptions
(*Subscriptions*)

## Overview

Subscription related APIs

### Available Operations

* [GetSubscriptions](#getsubscriptions) - List all subscriptions
* [CreateSubscription](#createsubscription) - Create a subscription
* [DeleteSubscription](#deletesubscription) - Delete subscription
* [GetSubscription](#getsubscription) - Retrieve a subscription
* [UpdateSubscription](#updatesubscription) - Update a subscription
* [TestSubscriptionFilter](#testsubscriptionfilter) - Validate subscription filter
* [TestSubscriptionFunction](#testsubscriptionfunction) - Test a subscription function

## GetSubscriptions

This endpoint fetches all the subscriptions

### Example Usage

<!-- UsageSnippet language="go" operationID="GetSubscriptions" method="get" path="/v1/projects/{projectID}/subscriptions" -->
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

    res, err := s.Subscriptions.GetSubscriptions(ctx, convoy.GetSubscriptionsRequest{
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
| `request`                                                   | [GetSubscriptionsRequest](../../getsubscriptionsrequest.md) | :heavy_check_mark:                                          | The request object to use for the request.                  |
| `opts`                                                      | [][convoy.Option](../../option.md)                          | :heavy_minus_sign:                                          | The options for this request.                               |

### Response

**[*GetSubscriptionsResponse](../../getsubscriptionsresponse.md), error**

### Errors

| Error Type                               | Status Code                              | Content Type                             |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| convoy.GetSubscriptionsBadRequestError   | 400                                      | application/json                         |
| convoy.GetSubscriptionsUnauthorizedError | 401                                      | application/json                         |
| convoy.GetSubscriptionsNotFoundError     | 404                                      | application/json                         |
| convoy.APIError                          | 4XX, 5XX                                 | \*/\*                                    |

## CreateSubscription

This endpoint creates a subscriptions

### Example Usage

<!-- UsageSnippet language="go" operationID="CreateSubscription" method="post" path="/v1/projects/{projectID}/subscriptions" -->
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

    res, err := s.Subscriptions.CreateSubscription(ctx, "<id>", convoy.CreateSubscription{})
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
| `createSubscription`                                  | [CreateSubscription](../../createsubscription.md)     | :heavy_check_mark:                                    | Subscription details                                  |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*CreateSubscriptionResponse](../../createsubscriptionresponse.md), error**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| convoy.CreateSubscriptionBadRequestError   | 400                                        | application/json                           |
| convoy.CreateSubscriptionUnauthorizedError | 401                                        | application/json                           |
| convoy.CreateSubscriptionNotFoundError     | 404                                        | application/json                           |
| convoy.APIError                            | 4XX, 5XX                                   | \*/\*                                      |

## DeleteSubscription

This endpoint deletes a subscription

### Example Usage

<!-- UsageSnippet language="go" operationID="DeleteSubscription" method="delete" path="/v1/projects/{projectID}/subscriptions/{subscriptionID}" -->
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

    res, err := s.Subscriptions.DeleteSubscription(ctx, "<id>", "<id>")
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
| `subscriptionID`                                      | *string*                                              | :heavy_check_mark:                                    | subscription id                                       |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*DeleteSubscriptionResponse](../../deletesubscriptionresponse.md), error**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| convoy.DeleteSubscriptionBadRequestError   | 400                                        | application/json                           |
| convoy.DeleteSubscriptionUnauthorizedError | 401                                        | application/json                           |
| convoy.DeleteSubscriptionNotFoundError     | 404                                        | application/json                           |
| convoy.APIError                            | 4XX, 5XX                                   | \*/\*                                      |

## GetSubscription

This endpoint retrieves a single subscription

### Example Usage

<!-- UsageSnippet language="go" operationID="GetSubscription" method="get" path="/v1/projects/{projectID}/subscriptions/{subscriptionID}" -->
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

    res, err := s.Subscriptions.GetSubscription(ctx, "<id>", "<id>")
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
| `subscriptionID`                                      | *string*                                              | :heavy_check_mark:                                    | subscription id                                       |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*GetSubscriptionResponse](../../getsubscriptionresponse.md), error**

### Errors

| Error Type                              | Status Code                             | Content Type                            |
| --------------------------------------- | --------------------------------------- | --------------------------------------- |
| convoy.GetSubscriptionBadRequestError   | 400                                     | application/json                        |
| convoy.GetSubscriptionUnauthorizedError | 401                                     | application/json                        |
| convoy.GetSubscriptionNotFoundError     | 404                                     | application/json                        |
| convoy.APIError                         | 4XX, 5XX                                | \*/\*                                   |

## UpdateSubscription

This endpoint updates a subscription

### Example Usage

<!-- UsageSnippet language="go" operationID="UpdateSubscription" method="put" path="/v1/projects/{projectID}/subscriptions/{subscriptionID}" -->
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

    res, err := s.Subscriptions.UpdateSubscription(ctx, "<id>", "<id>", convoy.UpdateSubscription{})
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
| `subscriptionID`                                      | *string*                                              | :heavy_check_mark:                                    | subscription id                                       |
| `updateSubscription`                                  | [UpdateSubscription](../../updatesubscription.md)     | :heavy_check_mark:                                    | Subscription Details                                  |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*UpdateSubscriptionResponse](../../updatesubscriptionresponse.md), error**

### Errors

| Error Type                                 | Status Code                                | Content Type                               |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| convoy.UpdateSubscriptionBadRequestError   | 400                                        | application/json                           |
| convoy.UpdateSubscriptionUnauthorizedError | 401                                        | application/json                           |
| convoy.UpdateSubscriptionNotFoundError     | 404                                        | application/json                           |
| convoy.APIError                            | 4XX, 5XX                                   | \*/\*                                      |

## TestSubscriptionFilter

This endpoint validates that a filter will match a certain payload structure.

### Example Usage

<!-- UsageSnippet language="go" operationID="TestSubscriptionFilter" method="post" path="/v1/projects/{projectID}/subscriptions/test_filter" -->
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

    res, err := s.Subscriptions.TestSubscriptionFilter(ctx, "<id>", convoy.TestFilter{})
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
| `testFilter`                                          | [TestFilter](../../testfilter.md)                     | :heavy_check_mark:                                    | Filter Details                                        |
| `opts`                                                | [][convoy.Option](../../option.md)                    | :heavy_minus_sign:                                    | The options for this request.                         |

### Response

**[*TestSubscriptionFilterResponse](../../testsubscriptionfilterresponse.md), error**

### Errors

| Error Type                                     | Status Code                                    | Content Type                                   |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| convoy.TestSubscriptionFilterBadRequestError   | 400                                            | application/json                               |
| convoy.TestSubscriptionFilterUnauthorizedError | 401                                            | application/json                               |
| convoy.TestSubscriptionFilterNotFoundError     | 404                                            | application/json                               |
| convoy.APIError                                | 4XX, 5XX                                       | \*/\*                                          |

## TestSubscriptionFunction

This endpoint test runs a transform function against a payload.

### Example Usage

<!-- UsageSnippet language="go" operationID="TestSubscriptionFunction" method="post" path="/v1/projects/{projectID}/subscriptions/test_function" -->
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

    res, err := s.Subscriptions.TestSubscriptionFunction(ctx, "<id>", convoy.FunctionRequest{})
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

**[*TestSubscriptionFunctionResponse](../../testsubscriptionfunctionresponse.md), error**

### Errors

| Error Type                                       | Status Code                                      | Content Type                                     |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| convoy.TestSubscriptionFunctionBadRequestError   | 400                                              | application/json                                 |
| convoy.TestSubscriptionFunctionUnauthorizedError | 401                                              | application/json                                 |
| convoy.TestSubscriptionFunctionNotFoundError     | 404                                              | application/json                                 |
| convoy.APIError                                  | 4XX, 5XX                                         | \*/\*                                            |