# GetEndpointsRequest


## Fields

| Field                                                      | Type                                                       | Required                                                   | Description                                                |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| `ProjectID`                                                | *string*                                                   | :heavy_check_mark:                                         | Project ID                                                 |
| `Direction`                                                | [*GetEndpointsDirection](./getendpointsdirection.md)       | :heavy_minus_sign:                                         | N/A                                                        |
| `NextPageCursor`                                           | **string*                                                  | :heavy_minus_sign:                                         | A pagination cursor to fetch the next page of a list       |
| `OwnerID`                                                  | **string*                                                  | :heavy_minus_sign:                                         | The owner ID of the endpoint                               |
| `PerPage`                                                  | **int64*                                                   | :heavy_minus_sign:                                         | The number of items to return per page                     |
| `PrevPageCursor`                                           | **string*                                                  | :heavy_minus_sign:                                         | A pagination cursor to fetch the previous page of a list   |
| `Q`                                                        | **string*                                                  | :heavy_minus_sign:                                         | The name of the endpoint                                   |
| `Sort`                                                     | **string*                                                  | :heavy_minus_sign:                                         | Sort order, values are `ASC` or `DESC`, defaults to `DESC` |