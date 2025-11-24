<!-- Start SDK Example Usage [usage] -->
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