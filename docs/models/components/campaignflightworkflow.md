# CampaignFlightWorkflow


## Fields

| Field                                      | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `ID`                                       | *string*                                   | :heavy_check_mark:                         | N/A                                        |
| `StartDateInclusiveUTC`                    | [time.Time](https://pkg.go.dev/time#Time)  | :heavy_check_mark:                         | N/A                                        |
| `EndDateExclusiveUTC`                      | [*time.Time](https://pkg.go.dev/time#Time) | :heavy_minus_sign:                         | N/A                                        |
| `BudgetInAdvertiserCurrency`               | *float64*                                  | :heavy_check_mark:                         | N/A                                        |
| `BudgetInImpressions`                      | **int64*                                   | :heavy_minus_sign:                         | N/A                                        |
| `DailyTargetInAdvertiserCurrency`          | **float64*                                 | :heavy_minus_sign:                         | N/A                                        |
| `DailyTargetInImpressions`                 | **int64*                                   | :heavy_minus_sign:                         | N/A                                        |