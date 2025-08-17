# GetMetaEventsPagedRequest


## Fields

| Field                                                            | Type                                                             | Required                                                         | Description                                                      |
| ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------- |
| `ProjectID`                                                      | *string*                                                         | :heavy_check_mark:                                               | Project ID                                                       |
| `Direction`                                                      | [*GetMetaEventsPagedDirection](./getmetaeventspageddirection.md) | :heavy_minus_sign:                                               | N/A                                                              |
| `EndDate`                                                        | **string*                                                        | :heavy_minus_sign:                                               | The end date                                                     |
| `NextPageCursor`                                                 | **string*                                                        | :heavy_minus_sign:                                               | A pagination cursor to fetch the next page of a list             |
| `PerPage`                                                        | **int64*                                                         | :heavy_minus_sign:                                               | The number of items to return per page                           |
| `PrevPageCursor`                                                 | **string*                                                        | :heavy_minus_sign:                                               | A pagination cursor to fetch the previous page of a list         |
| `Sort`                                                           | **string*                                                        | :heavy_minus_sign:                                               | Sort order, values are `ASC` or `DESC`, defaults to `DESC`       |
| `StartDate`                                                      | **string*                                                        | :heavy_minus_sign:                                               | The start date                                                   |