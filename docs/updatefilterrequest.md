# UpdateFilterRequest


## Fields

| Field                                                   | Type                                                    | Required                                                | Description                                             |
| ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- | ------------------------------------------------------- |
| `Body`                                                  | map[string]*any*                                        | :heavy_minus_sign:                                      | Body matching criteria (optional)                       |
| `EventType`                                             | **string*                                               | :heavy_minus_sign:                                      | Type of event this filter applies to (optional)         |
| `Headers`                                               | map[string]*any*                                        | :heavy_minus_sign:                                      | Header matching criteria (optional)                     |
| `IsFlattened`                                           | **bool*                                                 | :heavy_minus_sign:                                      | Whether the filter uses flattened JSON paths (optional) |