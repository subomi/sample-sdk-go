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

Convoy API Reference: Convoy is a fast and secure webhooks proxy. This document contains datastore.s API specification.
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
	"github.com/frain-dev/convoy/models/components"
	"log"
	"os"
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
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name         | Type   | Scheme  | Environment Variable  |
| ------------ | ------ | ------- | --------------------- |
| `APIKeyAuth` | apiKey | API key | `CONVOY_API_KEY_AUTH` |

You can configure it using the `WithSecurity` option when initializing the SDK client instance. For example:
```go
package main

import (
	"context"
	"github.com/frain-dev/convoy"
	"github.com/frain-dev/convoy/models/components"
	"log"
	"os"
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
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>


### [Events](docs/sdks/events/README.md)

* [CreateEndpointEvent](docs/sdks/events/README.md#createendpointevent) - Create an event

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `retry.Config` object to the call by using the `WithRetries` option:
```go
package main

import (
	"context"
	"github.com/frain-dev/convoy"
	"github.com/frain-dev/convoy/models/components"
	"github.com/frain-dev/convoy/retry"
	"log"
	"models/operations"
	"os"
)

func main() {
	ctx := context.Background()

	s := convoy.New(
		convoy.WithSecurity(os.Getenv("CONVOY_API_KEY_AUTH")),
	)

	res, err := s.Events.CreateEndpointEvent(ctx, "<id>", components.ModelsCreateEvent{}, operations.WithRetries(
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
	"github.com/frain-dev/convoy/models/components"
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
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or an error, they will never return both.

By Default, an API error will return `apierrors.APIError`. When custom error responses are specified for an operation, the SDK may also return their associated error. You can refer to respective *Errors* tables in SDK docs for more details on possible error types for each operation.

For example, the `CreateEndpointEvent` function may return the following errors:

| Error Type                  | Status Code | Content Type     |
| --------------------------- | ----------- | ---------------- |
| apierrors.BadRequestError   | 400         | application/json |
| apierrors.UnauthorizedError | 401         | application/json |
| apierrors.NotFoundError     | 404         | application/json |
| apierrors.APIError          | 4XX, 5XX    | \*/\*            |

### Example

```go
package main

import (
	"context"
	"errors"
	"github.com/frain-dev/convoy"
	"github.com/frain-dev/convoy/models/apierrors"
	"github.com/frain-dev/convoy/models/components"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := convoy.New(
		convoy.WithSecurity(os.Getenv("CONVOY_API_KEY_AUTH")),
	)

	res, err := s.Events.CreateEndpointEvent(ctx, "<id>", components.ModelsCreateEvent{})
	if err != nil {

		var e *apierrors.BadRequestError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *apierrors.UnauthorizedError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *apierrors.NotFoundError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *apierrors.APIError
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
	"github.com/frain-dev/convoy/models/components"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := convoy.New(
		convoy.WithServerURL("https://dashboard.getconvoy.io/api"),
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
