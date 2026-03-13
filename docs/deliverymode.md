# DeliveryMode

## Example Usage

```go
import (
	"github.com/frain-dev/convoy"
)

value := convoy.DeliveryModeAtLeastOnce

// Open enum: custom values can be created with a direct type cast
custom := convoy.DeliveryMode("custom_value")
```


## Values

| Name                      | Value                     |
| ------------------------- | ------------------------- |
| `DeliveryModeAtLeastOnce` | at_least_once             |
| `DeliveryModeAtMostOnce`  | at_most_once              |