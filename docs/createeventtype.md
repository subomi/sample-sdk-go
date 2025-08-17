# CreateEventType


## Fields

| Field                                                      | Type                                                       | Required                                                   | Description                                                |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| `Category`                                                 | **string*                                                  | :heavy_minus_sign:                                         | Category is a product-specific grouping for the event type |
| `Description`                                              | **string*                                                  | :heavy_minus_sign:                                         | Description is used to describe what the event type does   |
| `JSONSchema`                                               | map[string]*any*                                           | :heavy_minus_sign:                                         | JSONSchema is the JSON structure of the event type         |
| `Name`                                                     | **string*                                                  | :heavy_minus_sign:                                         | Name is the event type name. E.g., invoice.created         |