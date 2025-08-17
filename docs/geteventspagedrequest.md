# GetEventsPagedRequest


## Fields

| Field                                                      | Type                                                       | Required                                                   | Description                                                |
| ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| `ProjectID`                                                | *string*                                                   | :heavy_check_mark:                                         | Project ID                                                 |
| `Direction`                                                | [*GetEventsPagedDirection](./geteventspageddirection.md)   | :heavy_minus_sign:                                         | N/A                                                        |
| `EndDate`                                                  | **string*                                                  | :heavy_minus_sign:                                         | The end date                                               |
| `EndpointID`                                               | []*string*                                                 | :heavy_minus_sign:                                         | A list of endpoint ids to filter by                        |
| `IdempotencyKey`                                           | **string*                                                  | :heavy_minus_sign:                                         | IdempotencyKey to filter by                                |
| `NextPageCursor`                                           | **string*                                                  | :heavy_minus_sign:                                         | A pagination cursor to fetch the next page of a list       |
| `PerPage`                                                  | **int64*                                                   | :heavy_minus_sign:                                         | The number of items to return per page                     |
| `PrevPageCursor`                                           | **string*                                                  | :heavy_minus_sign:                                         | A pagination cursor to fetch the previous page of a list   |
| `Query`                                                    | **string*                                                  | :heavy_minus_sign:                                         | Any arbitrary value to filter the events payload           |
| `Sort`                                                     | **string*                                                  | :heavy_minus_sign:                                         | Sort order, values are `ASC` or `DESC`, defaults to `DESC` |
| `SourceID`                                                 | []*string*                                                 | :heavy_minus_sign:                                         | A list of Source IDs to filter the events by.              |
| `StartDate`                                                | **string*                                                  | :heavy_minus_sign:                                         | The start date                                             |