# CreateFilterRequest


## Fields

| Field                                           | Type                                            | Required                                        | Description                                     |
| ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- | ----------------------------------------------- |
| `Body`                                          | map[string]*any*                                | :heavy_minus_sign:                              | Body matching criteria (optional)               |
| `EventType`                                     | *string*                                        | :heavy_check_mark:                              | Type of event this filter applies to (required) |
| `Headers`                                       | map[string]*any*                                | :heavy_minus_sign:                              | Header matching criteria (optional)             |