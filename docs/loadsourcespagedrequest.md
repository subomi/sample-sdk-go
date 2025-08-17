# LoadSourcesPagedRequest


## Fields

| Field                                                        | Type                                                         | Required                                                     | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `ProjectID`                                                  | *string*                                                     | :heavy_check_mark:                                           | Project ID                                                   |
| `Direction`                                                  | [*LoadSourcesPagedDirection](./loadsourcespageddirection.md) | :heavy_minus_sign:                                           | N/A                                                          |
| `NextPageCursor`                                             | **string*                                                    | :heavy_minus_sign:                                           | A pagination cursor to fetch the next page of a list         |
| `PerPage`                                                    | **int64*                                                     | :heavy_minus_sign:                                           | The number of items to return per page                       |
| `PrevPageCursor`                                             | **string*                                                    | :heavy_minus_sign:                                           | A pagination cursor to fetch the previous page of a list     |
| `Provider`                                                   | **string*                                                    | :heavy_minus_sign:                                           | The custom source provider e.g. twitter, shopify             |
| `Sort`                                                       | **string*                                                    | :heavy_minus_sign:                                           | Sort order, values are `ASC` or `DESC`, defaults to `DESC`   |
| `Type`                                                       | **string*                                                    | :heavy_minus_sign:                                           | The source type e.g. http, pub_sub                           |