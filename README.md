# convoy

Developer-friendly & type-safe Go SDK specifically catered to leverage *convoy* API.

<div align="left">
    <a href="https://www.speakeasy.com/?utm_source=convoy&utm_campaign=go"><img src="https://custom-icon-badges.demolab.com/badge/-Built%20By%20Speakeasy-212015?style=for-the-badge&logoColor=FBE331&logo=speakeasy&labelColor=545454" /></a>
    <a href="https://opensource.org/licenses/MIT">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
    </a>
</div>


<br /><br />
> [!IMPORTANT]
> This SDK is not yet ready for production use. To complete setup please follow the steps outlined in your [workspace](https://app.speakeasy.com/org/speakeasy-self/speakeasy-self). Delete this section before > publishing to a package manager.

<!-- Start Summary [summary] -->
## Summary

Convoy API Reference: Convoy is a fast and secure webhooks proxy. This document contains s API specification.
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [convoy](#convoy)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

To add the SDK as a dependency to your project:
```bash
go get github.com/frain-dev/convoy
```
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

```go
package main

import (
	"context"
	"github.com/frain-dev/convoy"
	"log"
	"os"
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
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name         | Type | Scheme      | Environment Variable |
| ------------ | ---- | ----------- | -------------------- |
| `BearerAuth` | http | HTTP Bearer | `CONVOY_BEARER_AUTH` |

You can configure it using the `WithSecurity` option when initializing the SDK client instance. For example:
```go
package main

import (
	"context"
	"github.com/frain-dev/convoy"
	"log"
	"os"
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
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [DeliveryAttempts](docs/sdks/deliveryattempts/README.md)

* [GetDeliveryAttempts](docs/sdks/deliveryattempts/README.md#getdeliveryattempts) - List delivery attempts
* [GetDeliveryAttempt](docs/sdks/deliveryattempts/README.md#getdeliveryattempt) - Retrieve a delivery attempt

### [Endpoints](docs/sdks/endpoints/README.md)

* [PauseEndpoint](docs/sdks/endpoints/README.md#pauseendpoint) - Pause endpoint

### [EventDeliveries](docs/sdks/eventdeliveries/README.md)

* [GetEventDeliveriesPaged](docs/sdks/eventdeliveries/README.md#geteventdeliveriespaged) - List all event deliveries
* [GetEventDelivery](docs/sdks/eventdeliveries/README.md#geteventdelivery) - Retrieve an event delivery
* [ResendEventDelivery](docs/sdks/eventdeliveries/README.md#resendeventdelivery) - Retry event delivery
* [BatchRetryEventDelivery](docs/sdks/eventdeliveries/README.md#batchretryeventdelivery) - Batch retry event delivery
* [ForceResendEventDeliveries](docs/sdks/eventdeliveries/README.md#forceresendeventdeliveries) - Force retry event delivery

### [Events](docs/sdks/events/README.md)

* [GetEventsPaged](docs/sdks/events/README.md#geteventspaged) - List all events
* [CreateEndpointEvent](docs/sdks/events/README.md#createendpointevent) - Create an event
* [GetEndpointEvent](docs/sdks/events/README.md#getendpointevent) - Retrieve an event
* [ReplayEndpointEvent](docs/sdks/events/README.md#replayendpointevent) - Replay event
* [BatchReplayEvents](docs/sdks/events/README.md#batchreplayevents) - Batch replay events
* [CreateBroadcastEvent](docs/sdks/events/README.md#createbroadcastevent) - Create a broadcast event
* [CreateDynamicEvent](docs/sdks/events/README.md#createdynamicevent) - Dynamic Events
* [CreateEndpointFanoutEvent](docs/sdks/events/README.md#createendpointfanoutevent) - Fan out an event

### [EventTypes](docs/sdks/eventtypes/README.md)

* [GetEventTypes](docs/sdks/eventtypes/README.md#geteventtypes) - Retrieves a project's event types
* [CreateEventType](docs/sdks/eventtypes/README.md#createeventtype) - Create an event type
* [UpdateEventType](docs/sdks/eventtypes/README.md#updateeventtype) - Updates an event type
* [DeprecateEventType](docs/sdks/eventtypes/README.md#deprecateeventtype) - Deprecates an event type
* [ImportOpenAPISpec](docs/sdks/eventtypes/README.md#importopenapispec) - Import event types from OpenAPI spec

### [Filters](docs/sdks/filters/README.md)

* [GetFilters](docs/sdks/filters/README.md#getfilters) - List all filters
* [CreateFilter](docs/sdks/filters/README.md#createfilter) - Create a new filter
* [DeleteFilter](docs/sdks/filters/README.md#deletefilter) - Delete a filter
* [GetFilter](docs/sdks/filters/README.md#getfilter) - Get a filter
* [UpdateFilter](docs/sdks/filters/README.md#updatefilter) - Update a filter
* [BulkCreateFilters](docs/sdks/filters/README.md#bulkcreatefilters) - Create multiple subscription filters
* [BulkUpdateFilters](docs/sdks/filters/README.md#bulkupdatefilters) - Update multiple subscription filters
* [TestFilter](docs/sdks/filters/README.md#testfilter) - Test a filter

### [MetaEvents](docs/sdks/metaevents/README.md)

* [GetMetaEventsPaged](docs/sdks/metaevents/README.md#getmetaeventspaged) - List all meta events
* [GetMetaEvent](docs/sdks/metaevents/README.md#getmetaevent) - Retrieve a meta event
* [ResendMetaEvent](docs/sdks/metaevents/README.md#resendmetaevent) - Retry meta event

### [PortalLinks](docs/sdks/portallinks/README.md)

* [LoadPortalLinksPaged](docs/sdks/portallinks/README.md#loadportallinkspaged) - List all portal links
* [CreatePortalLink](docs/sdks/portallinks/README.md#createportallink) - Create a portal link
* [GetPortalLink](docs/sdks/portallinks/README.md#getportallink) - Retrieve a portal link
* [GeneratePortalToken](docs/sdks/portallinks/README.md#generateportaltoken) - Updates a portal link auth token
* [UpdatePortalLink](docs/sdks/portallinks/README.md#updateportallink) - Update a portal link
* [RefreshPortalLinkAuthToken](docs/sdks/portallinks/README.md#refreshportallinkauthtoken) - Get a portal link auth token
* [RevokePortalLink](docs/sdks/portallinks/README.md#revokeportallink) - Revoke a portal link

### [Sources](docs/sdks/sources/README.md)

* [LoadSourcesPaged](docs/sdks/sources/README.md#loadsourcespaged) - List all sources
* [CreateSource](docs/sdks/sources/README.md#createsource) - Create a source
* [DeleteSource](docs/sdks/sources/README.md#deletesource) - Delete a source
* [GetSource](docs/sdks/sources/README.md#getsource) - Retrieve a source
* [UpdateSource](docs/sdks/sources/README.md#updatesource) - Update a source
* [TestSourceFunction](docs/sdks/sources/README.md#testsourcefunction) - Validate source function

### [Subscriptions](docs/sdks/subscriptions/README.md)

* [GetSubscriptions](docs/sdks/subscriptions/README.md#getsubscriptions) - List all subscriptions
* [CreateSubscription](docs/sdks/subscriptions/README.md#createsubscription) - Create a subscription
* [DeleteSubscription](docs/sdks/subscriptions/README.md#deletesubscription) - Delete subscription
* [GetSubscription](docs/sdks/subscriptions/README.md#getsubscription) - Retrieve a subscription
* [UpdateSubscription](docs/sdks/subscriptions/README.md#updatesubscription) - Update a subscription
* [TestSubscriptionFilter](docs/sdks/subscriptions/README.md#testsubscriptionfilter) - Validate subscription filter
* [TestSubscriptionFunction](docs/sdks/subscriptions/README.md#testsubscriptionfunction) - Test a subscription function

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `retry.Config` object to the call by using the `WithRetries` option:
```go
package main

import (
	""
	"context"
	"github.com/frain-dev/convoy"
	"github.com/frain-dev/convoy/retry"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := convoy.New(
		convoy.WithSecurity(os.Getenv("CONVOY_BEARER_AUTH")),
	)

	res, err := s.Endpoints.PauseEndpoint(ctx, "<id>", "<id>", convoy.WithRetries(
		retry.Config{
			Strategy: "backoff",
			Backoff: &retry.BackoffStrategy{
				InitialInterval: 1,
				MaxInterval:     50,
				Exponent:        1.1,
				MaxElapsedTime:  100,
			},
			RetryConnectionErrors: false,
		}))
	if err != nil {
		log.Fatal(err)
	}
	if res.Object != nil {
		// handle response
	}
}

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `WithRetryConfig` option at SDK initialization:
```go
package main

import (
	"context"
	"github.com/frain-dev/convoy"
	"github.com/frain-dev/convoy/retry"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := convoy.New(
		convoy.WithRetryConfig(
			retry.Config{
				Strategy: "backoff",
				Backoff: &retry.BackoffStrategy{
					InitialInterval: 1,
					MaxInterval:     50,
					Exponent:        1.1,
					MaxElapsedTime:  100,
				},
				RetryConnectionErrors: false,
			}),
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
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or an error, they will never return both.

By Default, an API error will return `convoy.APIError`. When custom error responses are specified for an operation, the SDK may also return their associated error. You can refer to respective *Errors* tables in SDK docs for more details on possible error types for each operation.

For example, the `PauseEndpoint` function may return the following errors:

| Error Type                            | Status Code | Content Type     |
| ------------------------------------- | ----------- | ---------------- |
| convoy.PauseEndpointBadRequestError   | 400         | application/json |
| convoy.PauseEndpointUnauthorizedError | 401         | application/json |
| convoy.PauseEndpointNotFoundError     | 404         | application/json |
| convoy.APIError                       | 4XX, 5XX    | \*/\*            |

### Example

```go
package main

import (
	"context"
	"errors"
	"github.com/frain-dev/convoy"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := convoy.New(
		convoy.WithSecurity(os.Getenv("CONVOY_BEARER_AUTH")),
	)

	res, err := s.Endpoints.PauseEndpoint(ctx, "<id>", "<id>")
	if err != nil {

		var e *PauseEndpointBadRequestError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *PauseEndpointUnauthorizedError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *PauseEndpointNotFoundError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *convoy.APIError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}
	}
}

```
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Override Server URL Per-Client

The default server can be overridden globally using the `WithServerURL(serverURL string)` option when initializing the SDK client instance. For example:
```go
package main

import (
	"context"
	"github.com/frain-dev/convoy"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := convoy.New(
		convoy.WithServerURL("https://dashboard.getconvoy.io/api"),
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
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Go SDK makes API calls that wrap an internal HTTP client. The requirements for the HTTP client are very simple. It must match this interface:

```go
type HTTPClient interface {
	Do(req *http.Request) (*http.Response, error)
}
```

The built-in `net/http` client satisfies this interface and a default client based on the built-in is provided by default. To replace this default with a client of your own, you can implement this interface yourself or provide your own client configured as desired. Here's a simple example, which adds a client with a 30 second timeout.

```go
import (
	"net/http"
	"time"

	"github.com/frain-dev/convoy"
)

var (
	httpClient = &http.Client{Timeout: 30 * time.Second}
	sdkClient  = convoy.New(convoy.WithClient(httpClient))
)
```

This can be a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration.
<!-- End Custom HTTP Client [http-client] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=convoy&utm_campaign=go)
