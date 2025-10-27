# AdGroups
(*AdGroups*)

## Overview

### Available Operations

* [Create](#create) - Create a new ad group
* [Update](#update) - Update an ad group
* [Archive](#archive) - Archive multiple ad groups
* [BulkCreate](#bulkcreate) - Submit a job to create multiple new ad groups
* [BulkUpdate](#bulkupdate) - Submit a job to update multiple ad groups

## Create

Create a new ad group

### Example Usage

<!-- UsageSnippet language="go" operationID="createAdGroup" method="post" path="/adgroup" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.Create(ctx, &components.AdGroupCreateWorkflowInputWithValidation{
        PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
            IsEnabled: ttdworkflows.Pointer(false),
            Description: ttdworkflows.Pointer("twine from gosh poor safely editor astride vice lost and"),
            Budget: &components.AdGroupWorkflowBudgetInput{
                AllocationType: components.AllocationTypeMaximum.ToPointer(),
                BudgetInAdvertiserCurrency: ttdworkflows.Pointer[float64](3786.02),
                BudgetInImpressions: ttdworkflows.Pointer[int64](783190),
                DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](9747.02),
                DailyTargetInImpressions: ttdworkflows.Pointer[int64](985999),
            },
            BaseBidCPMInAdvertiserCurrency: ttdworkflows.Pointer[float64](3785.04),
            MaxBidCPMInAdvertiserCurrency: ttdworkflows.Pointer[float64](7447.3),
            AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                AudienceID: ttdworkflows.Pointer("<id>"),
                AudienceAcceleratorExclusionsEnabled: ttdworkflows.Pointer(true),
                AudienceBoosterEnabled: ttdworkflows.Pointer(true),
                AudienceExcluderEnabled: ttdworkflows.Pointer(true),
                AudiencePredictorEnabled: ttdworkflows.Pointer(false),
                CrossDeviceVendorListForAudience: []int{
                    107263,
                },
                RecencyExclusionWindowInMinutes: ttdworkflows.Pointer[int](90062),
                TargetTrackableUsersEnabled: ttdworkflows.Pointer(true),
                UseMcIDAsPrimary: ttdworkflows.Pointer(true),
            },
            RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Pointer(true),
                MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
                CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](2280.31),
                CtrInPercent: nil,
                NielsenOTPInPercent: ttdworkflows.Pointer[float64](5175.21),
                CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](2544.37),
                ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](8201.47),
                VcrInPercent: ttdworkflows.Pointer[float64](4846.08),
                ViewabilityInPercent: nil,
                VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](4649.53),
                CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](313.95),
                MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](4704.1),
            },
            CreativeIds: nil,
            AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                components.AdGroupWorkflowAssociateBidListInput{
                    BidListID: "<id>",
                    IsEnabled: ttdworkflows.Pointer(false),
                    IsDefaultForDimension: ttdworkflows.Pointer(true),
                },
            },
            Name: ttdworkflows.Pointer("<value>"),
            Channel: components.AdGroupChannelDisplay,
            FunnelLocation: components.AdGroupFunnelLocationConsideration,
            ProgrammaticGuaranteedPrivateContractID: ttdworkflows.Pointer("<id>"),
        },
        CampaignID: ttdworkflows.Pointer("<id>"),
        AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
            KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                AreFutureKoaFeaturesEnabled: ttdworkflows.Pointer(false),
                PredictiveClearingEnabled: ttdworkflows.Pointer(false),
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
                AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflows.Pointer(true),
            },
            DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                []components.DimensionalBiddingDimensions{},
                []components.DimensionalBiddingDimensions{},
            },
            IsUseClicksAsConversionsEnabled: ttdworkflows.Pointer(false),
            IsUseSecondaryConversionsEnabled: ttdworkflows.Pointer(false),
            NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
                EnhancedReportingOption: components.EnhancedNielsenReportingOptionsInputSite.ToPointer(),
                Gender: components.TargetingGenderInputMale,
                StartAge: components.TargetingStartAgeInputTwentyFive,
                EndAge: components.TargetingEndAgeInputSeventeen,
                Countries: []string{
                    "<value 1>",
                    "<value 2>",
                    "<value 3>",
                },
            },
            NewFrequencyConfigs: []components.AdGroupWorkflowNewFrequencyConfigInput{
                components.AdGroupWorkflowNewFrequencyConfigInput{
                    CounterName: nil,
                    FrequencyCap: ttdworkflows.Pointer[int](375286),
                    FrequencyGoal: ttdworkflows.Pointer[int](534735),
                    ResetIntervalInMinutes: ttdworkflows.Pointer[int](788122),
                },
            },
            Flights: []components.AdGroupWorkflowFlightInput{
                components.AdGroupWorkflowFlightInput{
                    AllocationType: components.AllocationTypeMaximum.ToPointer(),
                    BudgetInAdvertiserCurrency: ttdworkflows.Pointer[float64](4070.96),
                    BudgetInImpressions: ttdworkflows.Pointer[int64](901477),
                    DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](5847.35),
                    DailyTargetInImpressions: ttdworkflows.Pointer[int64](257517),
                    CampaignFlightID: 874887,
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Pointer(true),
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
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.Update(ctx, &components.AdGroupUpdateWorkflowInputWithValidation{
        ID: ttdworkflows.Pointer("<id>"),
        PrimaryInput: &components.AdGroupUpdateWorkflowPrimaryInput{
            IsEnabled: nil,
            Description: ttdworkflows.Pointer("likely upliftingly league that finally after owlishly when furthermore brush"),
            Budget: &components.AdGroupWorkflowBudgetInput{
                AllocationType: components.AllocationTypeMaximum.ToPointer(),
                BudgetInAdvertiserCurrency: ttdworkflows.Pointer[float64](2166.43),
                BudgetInImpressions: ttdworkflows.Pointer[int64](508947),
                DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](5830.53),
                DailyTargetInImpressions: ttdworkflows.Pointer[int64](377823),
            },
            BaseBidCPMInAdvertiserCurrency: ttdworkflows.Pointer[float64](1710.9),
            MaxBidCPMInAdvertiserCurrency: ttdworkflows.Pointer[float64](1926.83),
            AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                AudienceID: ttdworkflows.Pointer("<id>"),
                AudienceAcceleratorExclusionsEnabled: ttdworkflows.Pointer(false),
                AudienceBoosterEnabled: ttdworkflows.Pointer(true),
                AudienceExcluderEnabled: ttdworkflows.Pointer(true),
                AudiencePredictorEnabled: ttdworkflows.Pointer(true),
                CrossDeviceVendorListForAudience: []int{
                    774064,
                    165155,
                    542528,
                },
                RecencyExclusionWindowInMinutes: ttdworkflows.Pointer[int](740341),
                TargetTrackableUsersEnabled: ttdworkflows.Pointer(false),
                UseMcIDAsPrimary: ttdworkflows.Pointer(true),
            },
            RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Pointer(false),
                MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
                CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](1146.61),
                CtrInPercent: ttdworkflows.Pointer[float64](3063.1),
                NielsenOTPInPercent: ttdworkflows.Pointer[float64](411.57),
                CpaInAdvertiserCurrency: nil,
                ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](7161.01),
                VcrInPercent: ttdworkflows.Pointer[float64](5983.85),
                ViewabilityInPercent: ttdworkflows.Pointer[float64](9094.92),
                VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](1135.94),
                CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](6372.45),
                MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](8405.28),
            },
            CreativeIds: []string{
                "<value 1>",
                "<value 2>",
                "<value 3>",
            },
            AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                components.AdGroupWorkflowAssociateBidListInput{
                    BidListID: "<id>",
                    IsEnabled: ttdworkflows.Pointer(true),
                    IsDefaultForDimension: ttdworkflows.Pointer(true),
                },
            },
            Name: ttdworkflows.Pointer("<value>"),
            Channel: components.AdGroupChannelNative.ToPointer(),
            FunnelLocation: components.AdGroupFunnelLocationConversion.ToPointer(),
        },
        AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
            KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                AreFutureKoaFeaturesEnabled: ttdworkflows.Pointer(false),
                PredictiveClearingEnabled: ttdworkflows.Pointer(true),
            },
            ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                IsEnabled: false,
                PopulationID: ttdworkflows.Pointer[int](935670),
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
                AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflows.Pointer(true),
            },
            DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                []components.DimensionalBiddingDimensions{
                    components.DimensionalBiddingDimensionsHasContentLivestream,
                },
            },
            IsUseClicksAsConversionsEnabled: ttdworkflows.Pointer(false),
            IsUseSecondaryConversionsEnabled: ttdworkflows.Pointer(false),
            NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
                EnhancedReportingOption: components.EnhancedNielsenReportingOptionsInputNone.ToPointer(),
                Gender: components.TargetingGenderInputFemale,
                StartAge: components.TargetingStartAgeInputFiftyFive,
                EndAge: components.TargetingEndAgeInputSixtyFourPlus,
                Countries: []string{
                    "<value 1>",
                    "<value 2>",
                },
            },
            NewFrequencyConfigs: []components.AdGroupWorkflowNewFrequencyConfigInput{
                components.AdGroupWorkflowNewFrequencyConfigInput{
                    CounterName: ttdworkflows.Pointer("<value>"),
                    FrequencyCap: ttdworkflows.Pointer[int](685969),
                    FrequencyGoal: ttdworkflows.Pointer[int](448470),
                    ResetIntervalInMinutes: ttdworkflows.Pointer[int](577492),
                },
            },
            Flights: []components.AdGroupWorkflowFlightInput{
                components.AdGroupWorkflowFlightInput{
                    AllocationType: components.AllocationTypeMinimum.ToPointer(),
                    BudgetInAdvertiserCurrency: ttdworkflows.Pointer[float64](5325.23),
                    BudgetInImpressions: ttdworkflows.Pointer[int64](876101),
                    DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](44.58),
                    DailyTargetInImpressions: ttdworkflows.Pointer[int64](815686),
                    CampaignFlightID: 528311,
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Pointer(false),
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
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.Archive(ctx, ttdworkflows.Pointer(false), []string{
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

Submit a job to create multiple new ad groups

### Example Usage

<!-- UsageSnippet language="go" operationID="createAdGroupsJob" method="post" path="/standardjob/adgroup/bulk" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.BulkCreate(ctx, &components.AdGroupBulkCreateWorkflowInputWithValidation{
        Input: []components.AdGroupCreateWorkflowInput{},
        ValidateInputOnly: ttdworkflows.Pointer(false),
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
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.BulkUpdate(ctx, &components.AdGroupBulkUpdateWorkflowInputWithValidation{
        Input: []components.AdGroupUpdateWorkflowInput{
            components.AdGroupUpdateWorkflowInput{
                ID: ttdworkflows.Pointer("<id>"),
                PrimaryInput: &components.AdGroupUpdateWorkflowPrimaryInput{
                    IsEnabled: ttdworkflows.Pointer(false),
                    Description: ttdworkflows.Pointer("stealthily miserable imaginary er since athwart er blah marten"),
                    Budget: &components.AdGroupWorkflowBudgetInput{
                        AllocationType: components.AllocationTypeMinimum.ToPointer(),
                        BudgetInAdvertiserCurrency: ttdworkflows.Pointer[float64](5440.47),
                        BudgetInImpressions: nil,
                        DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](6251.13),
                        DailyTargetInImpressions: ttdworkflows.Pointer[int64](931411),
                    },
                    BaseBidCPMInAdvertiserCurrency: ttdworkflows.Pointer[float64](188.02),
                    MaxBidCPMInAdvertiserCurrency: ttdworkflows.Pointer[float64](6077.98),
                    AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                        AudienceID: ttdworkflows.Pointer("<id>"),
                        AudienceAcceleratorExclusionsEnabled: ttdworkflows.Pointer(true),
                        AudienceBoosterEnabled: ttdworkflows.Pointer(true),
                        AudienceExcluderEnabled: ttdworkflows.Pointer(false),
                        AudiencePredictorEnabled: ttdworkflows.Pointer(false),
                        CrossDeviceVendorListForAudience: []int{
                            27262,
                        },
                        RecencyExclusionWindowInMinutes: ttdworkflows.Pointer[int](676417),
                        TargetTrackableUsersEnabled: ttdworkflows.Pointer(true),
                        UseMcIDAsPrimary: ttdworkflows.Pointer(true),
                    },
                    RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflows.Pointer(false),
                        MaximizeLtvIncrementalReach: ttdworkflows.Pointer(true),
                        CpcInAdvertiserCurrency: nil,
                        CtrInPercent: ttdworkflows.Pointer[float64](2972.79),
                        NielsenOTPInPercent: ttdworkflows.Pointer[float64](4206.38),
                        CpaInAdvertiserCurrency: nil,
                        ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](842.94),
                        VcrInPercent: ttdworkflows.Pointer[float64](6307.13),
                        ViewabilityInPercent: ttdworkflows.Pointer[float64](9286.78),
                        VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](8251.2),
                        CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](4502.77),
                        MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](2362.43),
                    },
                    CreativeIds: []string{
                        "<value 1>",
                    },
                    AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                        components.AdGroupWorkflowAssociateBidListInput{
                            BidListID: "<id>",
                            IsEnabled: ttdworkflows.Pointer(true),
                            IsDefaultForDimension: ttdworkflows.Pointer(true),
                        },
                    },
                    Name: ttdworkflows.Pointer("<value>"),
                    Channel: components.AdGroupChannelTv.ToPointer(),
                    FunnelLocation: components.AdGroupFunnelLocationNone.ToPointer(),
                },
                AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
                    KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                        AreFutureKoaFeaturesEnabled: ttdworkflows.Pointer(true),
                        PredictiveClearingEnabled: ttdworkflows.Pointer(false),
                    },
                    ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                        IsEnabled: true,
                        PopulationID: ttdworkflows.Pointer[int](907569),
                        DemographicMemberIds: nil,
                        MobileDemographicMemberIds: []int{
                            169306,
                            568551,
                        },
                    },
                    ContractTargeting: &components.AdGroupWorkflowContractTargetingInput{
                        AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflows.Pointer(true),
                    },
                    DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                        []components.DimensionalBiddingDimensions{
                            components.DimensionalBiddingDimensionsHasFrequencyAdjustmentID,
                        },
                    },
                    IsUseClicksAsConversionsEnabled: ttdworkflows.Pointer(true),
                    IsUseSecondaryConversionsEnabled: ttdworkflows.Pointer(true),
                    NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
                        EnhancedReportingOption: components.EnhancedNielsenReportingOptionsInputAudience.ToPointer(),
                        Gender: components.TargetingGenderInputFemale,
                        StartAge: components.TargetingStartAgeInputFortyFive,
                        EndAge: components.TargetingEndAgeInputThirtyFour,
                        Countries: []string{
                            "<value 1>",
                            "<value 2>",
                        },
                    },
                    NewFrequencyConfigs: []components.AdGroupWorkflowNewFrequencyConfigInput{
                        components.AdGroupWorkflowNewFrequencyConfigInput{
                            CounterName: ttdworkflows.Pointer("<value>"),
                            FrequencyCap: ttdworkflows.Pointer[int](25438),
                            FrequencyGoal: ttdworkflows.Pointer[int](637221),
                            ResetIntervalInMinutes: ttdworkflows.Pointer[int](375296),
                        },
                    },
                    Flights: nil,
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Pointer(true),
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