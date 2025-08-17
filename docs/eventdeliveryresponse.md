# EventDeliveryResponse


## Fields

| Field                                            | Type                                             | Required                                         | Description                                      |
| ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ | ------------------------------------------------ |
| `AcknowledgedAt`                                 | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `CliMetadata`                                    | [*CLIMetadata](./climetadata.md)                 | :heavy_minus_sign:                               | N/A                                              |
| `CreatedAt`                                      | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `DeletedAt`                                      | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `DeliveryMode`                                   | [*DeliveryMode](./deliverymode.md)               | :heavy_minus_sign:                               | N/A                                              |
| `Description`                                    | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `DeviceID`                                       | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `DeviceMetadata`                                 | [*Device](./device.md)                           | :heavy_minus_sign:                               | N/A                                              |
| `EndpointID`                                     | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `EndpointMetadata`                               | [*Endpoint](./endpoint.md)                       | :heavy_minus_sign:                               | N/A                                              |
| `EventID`                                        | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `EventMetadata`                                  | [*Event](./event.md)                             | :heavy_minus_sign:                               | N/A                                              |
| `EventType`                                      | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `Headers`                                        | map[string][]*string*                            | :heavy_minus_sign:                               | N/A                                              |
| `IdempotencyKey`                                 | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `Latency`                                        | **string*                                        | :heavy_minus_sign:                               | Deprecated: Latency is deprecated.               |
| `LatencySeconds`                                 | **float64*                                       | :heavy_minus_sign:                               | N/A                                              |
| `Metadata`                                       | [*Metadata](./metadata.md)                       | :heavy_minus_sign:                               | N/A                                              |
| `ProjectID`                                      | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `SourceMetadata`                                 | [*Source](./source.md)                           | :heavy_minus_sign:                               | N/A                                              |
| `Status`                                         | [*EventDeliveryStatus](./eventdeliverystatus.md) | :heavy_minus_sign:                               | N/A                                              |
| `SubscriptionID`                                 | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `UID`                                            | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `UpdatedAt`                                      | **string*                                        | :heavy_minus_sign:                               | N/A                                              |
| `URLQueryParams`                                 | **string*                                        | :heavy_minus_sign:                               | N/A                                              |