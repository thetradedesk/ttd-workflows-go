# AdGroups
(*AdGroups*)

## Overview

### Available Operations

* [Create](#create) - Create a new ad group with required fields
* [Update](#update) - Update an ad group with specified fields
* [Archive](#archive) - Archive multiple ad groups
* [BulkCreate](#bulkcreate) - Create multiple new ad groups with required fields
* [BulkUpdate](#bulkupdate) - Update multiple ad groups with specified fields

## Create

Create a new ad group with required fields

### Example Usage

<!-- UsageSnippet language="go" operationID="createAdGroup" method="post" path="/adgroup" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflowsgo.New(
        ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.Create(ctx, &components.AdGroupCreateWorkflowInputWithValidation{
        PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
            IsEnabled: ttdworkflowsgo.Bool(false),
            Description: ttdworkflowsgo.String("twine from gosh poor safely editor astride vice lost and"),
            Budget: &components.AdGroupWorkflowBudgetInput{
                AllocationType: components.AllocationTypeMaximum.ToPointer(),
                BudgetInAdvertiserCurrency: ttdworkflowsgo.Float64(3786.02),
                BudgetInImpressions: ttdworkflowsgo.Int64(783190),
                DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(9747.02),
                DailyTargetInImpressions: ttdworkflowsgo.Int64(985999),
            },
            BaseBidCPMInAdvertiserCurrency: ttdworkflowsgo.Float64(3785.04),
            MaxBidCPMInAdvertiserCurrency: ttdworkflowsgo.Float64(7447.3),
            AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                AudienceID: ttdworkflowsgo.String("<id>"),
                AudienceAcceleratorExclusionsEnabled: ttdworkflowsgo.Bool(true),
                AudienceBoosterEnabled: ttdworkflowsgo.Bool(true),
                AudienceExcluderEnabled: ttdworkflowsgo.Bool(true),
                AudiencePredictorEnabled: ttdworkflowsgo.Bool(false),
                CrossDeviceVendorListForAudience: []int{
                    107263,
                },
                RecencyExclusionWindowInMinutes: ttdworkflowsgo.Int(90062),
                TargetTrackableUsersEnabled: ttdworkflowsgo.Bool(true),
                UseMcIDAsPrimary: ttdworkflowsgo.Bool(true),
            },
            RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                MaximizeReach: ttdworkflowsgo.Bool(true),
                MaximizeLtvIncrementalReach: ttdworkflowsgo.Bool(false),
                CpcInAdvertiserCurrency: ttdworkflowsgo.Float64(2280.31),
                CtrInPercent: nil,
                NielsenOTPInPercent: ttdworkflowsgo.Float64(5175.21),
                CpaInAdvertiserCurrency: ttdworkflowsgo.Float64(2544.37),
                ReturnOnAdSpendPercent: ttdworkflowsgo.Float64(8201.47),
                VcrInPercent: ttdworkflowsgo.Float64(4846.08),
                ViewabilityInPercent: nil,
                VcpmInAdvertiserCurrency: ttdworkflowsgo.Float64(4649.53),
                CpcvInAdvertiserCurrency: ttdworkflowsgo.Float64(313.95),
                MiaozhenOTPInPercent: ttdworkflowsgo.Float64(4704.1),
            },
            CreativeIds: nil,
            AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                components.AdGroupWorkflowAssociateBidListInput{
                    BidListID: "<id>",
                    IsEnabled: ttdworkflowsgo.Bool(false),
                    IsDefaultForDimension: ttdworkflowsgo.Bool(true),
                },
            },
            Name: ttdworkflowsgo.String("<value>"),
            Channel: components.AdGroupChannelDisplay,
            FunnelLocation: components.AdGroupFunnelLocationConsideration,
            ProgrammaticGuaranteedPrivateContractID: ttdworkflowsgo.String("<id>"),
        },
        CampaignID: ttdworkflowsgo.String("<id>"),
        AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
            KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                AreFutureKoaFeaturesEnabled: ttdworkflowsgo.Bool(false),
                PredictiveClearingEnabled: ttdworkflowsgo.Bool(false),
            },
            ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                IsEnabled: false,
                PopulationID: nil,
                DemographicMemberIds: []int{
                    959580,
                    236376,
                },
                MobileDemographicMemberIds: []int{
                    664689,
                    827980,
                    21321,
                },
            },
            ContractTargeting: &components.AdGroupWorkflowContractTargetingInput{
                AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflowsgo.Bool(true),
            },
            DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                []components.DimensionalBiddingDimensions{},
                []components.DimensionalBiddingDimensions{},
            },
            IsUseClicksAsConversionsEnabled: ttdworkflowsgo.Bool(false),
            IsUseSecondaryConversionsEnabled: ttdworkflowsgo.Bool(false),
            NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
                EnhancedReportingOption: components.EnhancedNielsenReportingOptionsSite.ToPointer(),
                Gender: components.TargetingGenderMale,
                StartAge: components.TargetingStartAgeTwentyFive,
                EndAge: components.TargetingEndAgeSeventeen,
                Countries: []string{
                    "<value 1>",
                    "<value 2>",
                    "<value 3>",
                },
            },
            NewFrequencyConfigs: []components.AdGroupWorkflowNewFrequencyConfigInput{
                components.AdGroupWorkflowNewFrequencyConfigInput{
                    CounterName: nil,
                    FrequencyCap: ttdworkflowsgo.Int(375286),
                    FrequencyGoal: ttdworkflowsgo.Int(534735),
                    ResetIntervalInMinutes: ttdworkflowsgo.Int(788122),
                },
            },
            Flights: []components.AdGroupWorkflowFlightInput{
                components.AdGroupWorkflowFlightInput{
                    AllocationType: components.AllocationTypeMaximum.ToPointer(),
                    BudgetInAdvertiserCurrency: ttdworkflowsgo.Float64(4070.96),
                    BudgetInImpressions: ttdworkflowsgo.Int64(901477),
                    DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(5847.35),
                    DailyTargetInImpressions: ttdworkflowsgo.Int64(257517),
                    CampaignFlightID: 874887,
                },
            },
        },
        ValidateInputOnly: ttdworkflowsgo.Bool(true),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.AdGroupPayload != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                  | Type                                                                                                                       | Required                                                                                                                   | Description                                                                                                                |
| -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                                                      | :heavy_check_mark:                                                                                                         | The context to use for the request.                                                                                        |
| `request`                                                                                                                  | [components.AdGroupCreateWorkflowInputWithValidation](../../models/components/adgroupcreateworkflowinputwithvalidation.md) | :heavy_check_mark:                                                                                                         | The request object to use for the request.                                                                                 |
| `opts`                                                                                                                     | [][operations.Option](../../models/operations/option.md)                                                                   | :heavy_minus_sign:                                                                                                         | The options for this request.                                                                                              |

### Response

**[*operations.CreateAdGroupResponse](../../models/operations/createadgroupresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 403                      | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## Update

Only the fields provided in the request payload will be updated.

### Example Usage

<!-- UsageSnippet language="go" operationID="updateAdGroup" method="patch" path="/adgroup" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflowsgo.New(
        ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.Update(ctx, &components.AdGroupUpdateWorkflowInputWithValidation{
        ID: ttdworkflowsgo.String("<id>"),
        PrimaryInput: &components.AdGroupUpdateWorkflowPrimaryInput{
            IsEnabled: nil,
            Description: ttdworkflowsgo.String("likely upliftingly league that finally after owlishly when furthermore brush"),
            Budget: &components.AdGroupWorkflowBudgetInput{
                AllocationType: components.AllocationTypeMaximum.ToPointer(),
                BudgetInAdvertiserCurrency: ttdworkflowsgo.Float64(2166.43),
                BudgetInImpressions: ttdworkflowsgo.Int64(508947),
                DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(5830.53),
                DailyTargetInImpressions: ttdworkflowsgo.Int64(377823),
            },
            BaseBidCPMInAdvertiserCurrency: ttdworkflowsgo.Float64(1710.9),
            MaxBidCPMInAdvertiserCurrency: ttdworkflowsgo.Float64(1926.83),
            AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                AudienceID: ttdworkflowsgo.String("<id>"),
                AudienceAcceleratorExclusionsEnabled: ttdworkflowsgo.Bool(false),
                AudienceBoosterEnabled: ttdworkflowsgo.Bool(true),
                AudienceExcluderEnabled: ttdworkflowsgo.Bool(true),
                AudiencePredictorEnabled: ttdworkflowsgo.Bool(true),
                CrossDeviceVendorListForAudience: []int{
                    774064,
                    165155,
                    542528,
                },
                RecencyExclusionWindowInMinutes: ttdworkflowsgo.Int(740341),
                TargetTrackableUsersEnabled: ttdworkflowsgo.Bool(false),
                UseMcIDAsPrimary: ttdworkflowsgo.Bool(true),
            },
            RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                MaximizeReach: ttdworkflowsgo.Bool(false),
                MaximizeLtvIncrementalReach: ttdworkflowsgo.Bool(false),
                CpcInAdvertiserCurrency: ttdworkflowsgo.Float64(1146.61),
                CtrInPercent: ttdworkflowsgo.Float64(3063.1),
                NielsenOTPInPercent: ttdworkflowsgo.Float64(411.57),
                CpaInAdvertiserCurrency: nil,
                ReturnOnAdSpendPercent: ttdworkflowsgo.Float64(7161.01),
                VcrInPercent: ttdworkflowsgo.Float64(5983.85),
                ViewabilityInPercent: ttdworkflowsgo.Float64(9094.92),
                VcpmInAdvertiserCurrency: ttdworkflowsgo.Float64(1135.94),
                CpcvInAdvertiserCurrency: ttdworkflowsgo.Float64(6372.45),
                MiaozhenOTPInPercent: ttdworkflowsgo.Float64(8405.28),
            },
            CreativeIds: []string{
                "<value 1>",
                "<value 2>",
                "<value 3>",
            },
            AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                components.AdGroupWorkflowAssociateBidListInput{
                    BidListID: "<id>",
                    IsEnabled: ttdworkflowsgo.Bool(true),
                    IsDefaultForDimension: ttdworkflowsgo.Bool(true),
                },
            },
            Name: ttdworkflowsgo.String("<value>"),
            Channel: components.AdGroupChannelNative.ToPointer(),
            FunnelLocation: components.AdGroupFunnelLocationConversion.ToPointer(),
        },
        AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
            KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                AreFutureKoaFeaturesEnabled: ttdworkflowsgo.Bool(false),
                PredictiveClearingEnabled: ttdworkflowsgo.Bool(true),
            },
            ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                IsEnabled: false,
                PopulationID: ttdworkflowsgo.Int(935670),
                DemographicMemberIds: []int{
                    873274,
                    940674,
                    350994,
                },
                MobileDemographicMemberIds: []int{
                    572403,
                    872508,
                    141651,
                },
            },
            ContractTargeting: &components.AdGroupWorkflowContractTargetingInput{
                AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflowsgo.Bool(true),
            },
            DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                []components.DimensionalBiddingDimensions{
                    components.DimensionalBiddingDimensionsHasContentLivestream,
                },
            },
            IsUseClicksAsConversionsEnabled: ttdworkflowsgo.Bool(false),
            IsUseSecondaryConversionsEnabled: ttdworkflowsgo.Bool(false),
            NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
                EnhancedReportingOption: components.EnhancedNielsenReportingOptionsNone.ToPointer(),
                Gender: components.TargetingGenderFemale,
                StartAge: components.TargetingStartAgeFiftyFive,
                EndAge: components.TargetingEndAgeSixtyFourPlus,
                Countries: []string{
                    "<value 1>",
                    "<value 2>",
                },
            },
            NewFrequencyConfigs: []components.AdGroupWorkflowNewFrequencyConfigInput{
                components.AdGroupWorkflowNewFrequencyConfigInput{
                    CounterName: ttdworkflowsgo.String("<value>"),
                    FrequencyCap: ttdworkflowsgo.Int(685969),
                    FrequencyGoal: ttdworkflowsgo.Int(448470),
                    ResetIntervalInMinutes: ttdworkflowsgo.Int(577492),
                },
            },
            Flights: []components.AdGroupWorkflowFlightInput{
                components.AdGroupWorkflowFlightInput{
                    AllocationType: components.AllocationTypeMinimum.ToPointer(),
                    BudgetInAdvertiserCurrency: ttdworkflowsgo.Float64(5325.23),
                    BudgetInImpressions: ttdworkflowsgo.Int64(876101),
                    DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(44.58),
                    DailyTargetInImpressions: ttdworkflowsgo.Int64(815686),
                    CampaignFlightID: 528311,
                },
            },
        },
        ValidateInputOnly: ttdworkflowsgo.Bool(false),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.AdGroupPayload != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                  | Type                                                                                                                       | Required                                                                                                                   | Description                                                                                                                |
| -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                      | [context.Context](https://pkg.go.dev/context#Context)                                                                      | :heavy_check_mark:                                                                                                         | The context to use for the request.                                                                                        |
| `request`                                                                                                                  | [components.AdGroupUpdateWorkflowInputWithValidation](../../models/components/adgroupupdateworkflowinputwithvalidation.md) | :heavy_check_mark:                                                                                                         | The request object to use for the request.                                                                                 |
| `opts`                                                                                                                     | [][operations.Option](../../models/operations/option.md)                                                                   | :heavy_minus_sign:                                                                                                         | The options for this request.                                                                                              |

### Response

**[*operations.UpdateAdGroupResponse](../../models/operations/updateadgroupresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 403                      | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## Archive

**NOTE**: Once archived, ad groups cannot be un-archived.

### Example Usage

<!-- UsageSnippet language="go" operationID="archiveAdGroups" method="post" path="/adgroup/archive" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflowsgo.New(
        ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.Archive(ctx, ttdworkflowsgo.Bool(false), []string{
        "<value 1>",
        "<value 2>",
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.Strings != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `forceArchive`                                           | **bool*                                                  | :heavy_minus_sign:                                       | N/A                                                      |
| `requestBody`                                            | []*string*                                               | :heavy_minus_sign:                                       | N/A                                                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.ArchiveAdGroupsResponse](../../models/operations/archiveadgroupsresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 403                      | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## BulkCreate

Create multiple new ad groups with required fields

### Example Usage

<!-- UsageSnippet language="go" operationID="createAdGroupsJob" method="post" path="/standardjob/adgroup/bulk" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflowsgo.New(
        ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.BulkCreate(ctx, &components.AdGroupBulkCreateWorkflowInputWithValidation{
        Input: []components.AdGroupCreateWorkflowInput{},
        ValidateInputOnly: ttdworkflowsgo.Bool(false),
        CallbackInput: &components.WorkflowCallbackInput{
            CallbackURL: "https://fantastic-daughter.biz/",
            CallbackHeaders: map[string]string{
                "key": "<value>",
                "key1": "<value>",
                "key2": "<value>",
            },
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.StandardJobSubmitResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                          | Type                                                                                                                               | Required                                                                                                                           | Description                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                              | [context.Context](https://pkg.go.dev/context#Context)                                                                              | :heavy_check_mark:                                                                                                                 | The context to use for the request.                                                                                                |
| `request`                                                                                                                          | [components.AdGroupBulkCreateWorkflowInputWithValidation](../../models/components/adgroupbulkcreateworkflowinputwithvalidation.md) | :heavy_check_mark:                                                                                                                 | The request object to use for the request.                                                                                         |
| `opts`                                                                                                                             | [][operations.Option](../../models/operations/option.md)                                                                           | :heavy_minus_sign:                                                                                                                 | The options for this request.                                                                                                      |

### Response

**[*operations.CreateAdGroupsJobResponse](../../models/operations/createadgroupsjobresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 403                      | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## BulkUpdate

Only the fields provided in the request payload for each specific ad group will be updated.

### Example Usage

<!-- UsageSnippet language="go" operationID="updateAdGroupsJob" method="patch" path="/standardjob/adgroup/bulk" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflowsgo.New(
        ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.BulkUpdate(ctx, &components.AdGroupBulkUpdateWorkflowInputWithValidation{
        Input: []components.AdGroupUpdateWorkflowInput{
            components.AdGroupUpdateWorkflowInput{
                ID: ttdworkflowsgo.String("<id>"),
                PrimaryInput: &components.AdGroupUpdateWorkflowPrimaryInput{
                    IsEnabled: ttdworkflowsgo.Bool(false),
                    Description: ttdworkflowsgo.String("stealthily miserable imaginary er since athwart er blah marten"),
                    Budget: &components.AdGroupWorkflowBudgetInput{
                        AllocationType: components.AllocationTypeMinimum.ToPointer(),
                        BudgetInAdvertiserCurrency: ttdworkflowsgo.Float64(5440.47),
                        BudgetInImpressions: nil,
                        DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(6251.13),
                        DailyTargetInImpressions: ttdworkflowsgo.Int64(931411),
                    },
                    BaseBidCPMInAdvertiserCurrency: ttdworkflowsgo.Float64(188.02),
                    MaxBidCPMInAdvertiserCurrency: ttdworkflowsgo.Float64(6077.98),
                    AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                        AudienceID: ttdworkflowsgo.String("<id>"),
                        AudienceAcceleratorExclusionsEnabled: ttdworkflowsgo.Bool(true),
                        AudienceBoosterEnabled: ttdworkflowsgo.Bool(true),
                        AudienceExcluderEnabled: ttdworkflowsgo.Bool(false),
                        AudiencePredictorEnabled: ttdworkflowsgo.Bool(false),
                        CrossDeviceVendorListForAudience: []int{
                            27262,
                        },
                        RecencyExclusionWindowInMinutes: ttdworkflowsgo.Int(676417),
                        TargetTrackableUsersEnabled: ttdworkflowsgo.Bool(true),
                        UseMcIDAsPrimary: ttdworkflowsgo.Bool(true),
                    },
                    RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflowsgo.Bool(false),
                        MaximizeLtvIncrementalReach: ttdworkflowsgo.Bool(true),
                        CpcInAdvertiserCurrency: nil,
                        CtrInPercent: ttdworkflowsgo.Float64(2972.79),
                        NielsenOTPInPercent: ttdworkflowsgo.Float64(4206.38),
                        CpaInAdvertiserCurrency: nil,
                        ReturnOnAdSpendPercent: ttdworkflowsgo.Float64(842.94),
                        VcrInPercent: ttdworkflowsgo.Float64(6307.13),
                        ViewabilityInPercent: ttdworkflowsgo.Float64(9286.78),
                        VcpmInAdvertiserCurrency: ttdworkflowsgo.Float64(8251.2),
                        CpcvInAdvertiserCurrency: ttdworkflowsgo.Float64(4502.77),
                        MiaozhenOTPInPercent: ttdworkflowsgo.Float64(2362.43),
                    },
                    CreativeIds: []string{
                        "<value 1>",
                    },
                    AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                        components.AdGroupWorkflowAssociateBidListInput{
                            BidListID: "<id>",
                            IsEnabled: ttdworkflowsgo.Bool(true),
                            IsDefaultForDimension: ttdworkflowsgo.Bool(true),
                        },
                    },
                    Name: ttdworkflowsgo.String("<value>"),
                    Channel: components.AdGroupChannelTv.ToPointer(),
                    FunnelLocation: components.AdGroupFunnelLocationNone.ToPointer(),
                },
                AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
                    KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                        AreFutureKoaFeaturesEnabled: ttdworkflowsgo.Bool(true),
                        PredictiveClearingEnabled: ttdworkflowsgo.Bool(false),
                    },
                    ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                        IsEnabled: true,
                        PopulationID: ttdworkflowsgo.Int(907569),
                        DemographicMemberIds: nil,
                        MobileDemographicMemberIds: []int{
                            169306,
                            568551,
                        },
                    },
                    ContractTargeting: &components.AdGroupWorkflowContractTargetingInput{
                        AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflowsgo.Bool(true),
                    },
                    DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                        []components.DimensionalBiddingDimensions{
                            components.DimensionalBiddingDimensionsHasFrequencyAdjustmentID,
                        },
                    },
                    IsUseClicksAsConversionsEnabled: ttdworkflowsgo.Bool(true),
                    IsUseSecondaryConversionsEnabled: ttdworkflowsgo.Bool(true),
                    NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
                        EnhancedReportingOption: components.EnhancedNielsenReportingOptionsAudience.ToPointer(),
                        Gender: components.TargetingGenderFemale,
                        StartAge: components.TargetingStartAgeFortyFive,
                        EndAge: components.TargetingEndAgeThirtyFour,
                        Countries: []string{
                            "<value 1>",
                            "<value 2>",
                        },
                    },
                    NewFrequencyConfigs: []components.AdGroupWorkflowNewFrequencyConfigInput{
                        components.AdGroupWorkflowNewFrequencyConfigInput{
                            CounterName: ttdworkflowsgo.String("<value>"),
                            FrequencyCap: ttdworkflowsgo.Int(25438),
                            FrequencyGoal: ttdworkflowsgo.Int(637221),
                            ResetIntervalInMinutes: ttdworkflowsgo.Int(375296),
                        },
                    },
                    Flights: nil,
                },
            },
        },
        ValidateInputOnly: ttdworkflowsgo.Bool(true),
        CallbackInput: &components.WorkflowCallbackInput{
            CallbackURL: "https://winged-bathhouse.net",
            CallbackHeaders: nil,
        },
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.StandardJobSubmitResponse != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                          | Type                                                                                                                               | Required                                                                                                                           | Description                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                              | [context.Context](https://pkg.go.dev/context#Context)                                                                              | :heavy_check_mark:                                                                                                                 | The context to use for the request.                                                                                                |
| `request`                                                                                                                          | [components.AdGroupBulkUpdateWorkflowInputWithValidation](../../models/components/adgroupbulkupdateworkflowinputwithvalidation.md) | :heavy_check_mark:                                                                                                                 | The request object to use for the request.                                                                                         |
| `opts`                                                                                                                             | [][operations.Option](../../models/operations/option.md)                                                                           | :heavy_minus_sign:                                                                                                                 | The options for this request.                                                                                                      |

### Response

**[*operations.UpdateAdGroupsJobResponse](../../models/operations/updateadgroupsjobresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 403                      | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |