# CreateSubscriptionDeliveryMode

Delivery mode configuration

## Example Usage

```go
import (
	"github.com/frain-dev/convoy"
)

value := convoy.CreateSubscriptionDeliveryModeAtLeastOnce

// Open enum: custom values can be created with a direct type cast
custom := convoy.CreateSubscriptionDeliveryMode("custom_value")
```


## Values

| Name                                        | Value                                       |
| ------------------------------------------- | ------------------------------------------- |
| `CreateSubscriptionDeliveryModeAtLeastOnce` | at_least_once                               |
| `CreateSubscriptionDeliveryModeAtMostOnce`  | at_most_once                                |