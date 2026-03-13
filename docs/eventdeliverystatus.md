# EventDeliveryStatus

## Example Usage

```go
import (
	"github.com/frain-dev/convoy"
)

value := convoy.EventDeliveryStatusScheduled
```


## Values

| Name                            | Value                           |
| ------------------------------- | ------------------------------- |
| `EventDeliveryStatusScheduled`  | Scheduled                       |
| `EventDeliveryStatusProcessing` | Processing                      |
| `EventDeliveryStatusDiscarded`  | Discarded                       |
| `EventDeliveryStatusFailure`    | Failure                         |
| `EventDeliveryStatusSuccess`    | Success                         |
| `EventDeliveryStatusRetry`      | Retry                           |