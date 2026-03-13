# VerifierType

## Example Usage

```go
import (
	"github.com/frain-dev/convoy"
)

value := convoy.VerifierTypeNoop
```


## Values

| Name                    | Value                   |
| ----------------------- | ----------------------- |
| `VerifierTypeNoop`      | noop                    |
| `VerifierTypeHmac`      | hmac                    |
| `VerifierTypeBasicAuth` | basic_auth              |
| `VerifierTypeAPIKey`    | api_key                 |