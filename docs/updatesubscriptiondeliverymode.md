# UpdateSubscriptionDeliveryMode

Delivery mode configuration

## Example Usage

```go
import (
	"github.com/frain-dev/convoy"
)

value := convoy.UpdateSubscriptionDeliveryModeAtLeastOnce

// Open enum: custom values can be created with a direct type cast
custom := convoy.UpdateSubscriptionDeliveryMode("custom_value")
```


## Values

| Name                                        | Value                                       |
| ------------------------------------------- | ------------------------------------------- |
| `UpdateSubscriptionDeliveryModeAtLeastOnce` | at_least_once                               |
| `UpdateSubscriptionDeliveryModeAtMostOnce`  | at_most_once                                |