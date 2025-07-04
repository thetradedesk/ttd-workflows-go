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

```go
package main

import(
	"context"
	"os"
	ttdworkflows "ttd-workflows"
	"ttd-workflows/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.Create(ctx, &components.AdGroupCreateWorkflowInputWithValidation{
        PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
            IsEnabled: ttdworkflows.Bool(false),
            Description: ttdworkflows.String("twine from gosh poor safely editor astride vice lost and"),
            Budget: &components.AdGroupWorkflowBudgetInput{
                AllocationType: components.AllocationTypeMaximum.ToPointer(),
                BudgetInAdvertiserCurrency: ttdworkflows.Float64(3786.02),
                BudgetInImpressions: ttdworkflows.Int64(783190),
                DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(9747.02),
                DailyTargetInImpressions: ttdworkflows.Int64(985999),
            },
            BaseBidCPMInAdvertiserCurrency: ttdworkflows.Float64(3785.04),
            MaxBidCPMInAdvertiserCurrency: ttdworkflows.Float64(7447.3),
            AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                AudienceID: ttdworkflows.String("<id>"),
                AudienceAcceleratorExclusionsEnabled: ttdworkflows.Bool(true),
                AudienceBoosterEnabled: ttdworkflows.Bool(true),
                AudienceExcluderEnabled: ttdworkflows.Bool(true),
                AudiencePredictorEnabled: ttdworkflows.Bool(false),
                CrossDeviceVendorListForAudience: []int{
                    107263,
                },
                RecencyExclusionWindowInMinutes: ttdworkflows.Int(90062),
                TargetTrackableUsersEnabled: ttdworkflows.Bool(true),
                UseMcIDAsPrimary: ttdworkflows.Bool(true),
            },
            RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Bool(true),
                MaximizeLtvIncrementalReach: ttdworkflows.Bool(false),
                CpcInAdvertiserCurrency: ttdworkflows.Float64(2280.31),
                CtrInPercent: nil,
                NielsenOTPInPercent: ttdworkflows.Float64(5175.21),
                CpaInAdvertiserCurrency: ttdworkflows.Float64(2544.37),
                ReturnOnAdSpendPercent: ttdworkflows.Float64(8201.47),
                VcrInPercent: ttdworkflows.Float64(4846.08),
                ViewabilityInPercent: nil,
                VcpmInAdvertiserCurrency: ttdworkflows.Float64(4649.53),
                CpcvInAdvertiserCurrency: ttdworkflows.Float64(313.95),
                MiaozhenOTPInPercent: ttdworkflows.Float64(4704.1),
            },
            CreativeIds: nil,
            AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                components.AdGroupWorkflowAssociateBidListInput{
                    BidListID: "<id>",
                    IsEnabled: ttdworkflows.Bool(false),
                    IsDefaultForDimension: ttdworkflows.Bool(true),
                },
            },
            Name: ttdworkflows.String("<value>"),
            Channel: components.AdGroupChannelDisplay,
            FunnelLocation: components.AdGroupFunnelLocationConsideration,
            ProgrammaticGuaranteedPrivateContractID: ttdworkflows.String("<id>"),
        },
        CampaignID: ttdworkflows.String("<id>"),
        AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
            KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                AreFutureKoaFeaturesEnabled: ttdworkflows.Bool(false),
                PredictiveClearingEnabled: ttdworkflows.Bool(false),
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
                AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflows.Bool(true),
            },
            DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                []components.DimensionalBiddingDimensions{},
                []components.DimensionalBiddingDimensions{},
            },
            IsUseClicksAsConversionsEnabled: ttdworkflows.Bool(false),
            IsUseSecondaryConversionsEnabled: ttdworkflows.Bool(false),
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
                    FrequencyCap: ttdworkflows.Int(375286),
                    FrequencyGoal: ttdworkflows.Int(534735),
                    ResetIntervalInMinutes: ttdworkflows.Int(788122),
                },
            },
            Flights: []components.AdGroupWorkflowFlightInput{
                components.AdGroupWorkflowFlightInput{
                    AllocationType: components.AllocationTypeMaximum.ToPointer(),
                    BudgetInAdvertiserCurrency: ttdworkflows.Float64(4070.96),
                    BudgetInImpressions: ttdworkflows.Int64(901477),
                    DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(5847.35),
                    DailyTargetInImpressions: ttdworkflows.Int64(257517),
                    CampaignFlightID: 874887,
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Bool(true),
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

```go
package main

import(
	"context"
	"os"
	ttdworkflows "ttd-workflows"
	"ttd-workflows/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.Update(ctx, &components.AdGroupUpdateWorkflowInputWithValidation{
        ID: ttdworkflows.String("<id>"),
        PrimaryInput: &components.AdGroupUpdateWorkflowPrimaryInput{
            IsEnabled: nil,
            Description: ttdworkflows.String("likely upliftingly league that finally after owlishly when furthermore brush"),
            Budget: &components.AdGroupWorkflowBudgetInput{
                AllocationType: components.AllocationTypeMaximum.ToPointer(),
                BudgetInAdvertiserCurrency: ttdworkflows.Float64(2166.43),
                BudgetInImpressions: ttdworkflows.Int64(508947),
                DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(5830.53),
                DailyTargetInImpressions: ttdworkflows.Int64(377823),
            },
            BaseBidCPMInAdvertiserCurrency: ttdworkflows.Float64(1710.9),
            MaxBidCPMInAdvertiserCurrency: ttdworkflows.Float64(1926.83),
            AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                AudienceID: ttdworkflows.String("<id>"),
                AudienceAcceleratorExclusionsEnabled: ttdworkflows.Bool(false),
                AudienceBoosterEnabled: ttdworkflows.Bool(true),
                AudienceExcluderEnabled: ttdworkflows.Bool(true),
                AudiencePredictorEnabled: ttdworkflows.Bool(true),
                CrossDeviceVendorListForAudience: []int{
                    774064,
                    165155,
                    542528,
                },
                RecencyExclusionWindowInMinutes: ttdworkflows.Int(740341),
                TargetTrackableUsersEnabled: ttdworkflows.Bool(false),
                UseMcIDAsPrimary: ttdworkflows.Bool(true),
            },
            RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Bool(false),
                MaximizeLtvIncrementalReach: ttdworkflows.Bool(false),
                CpcInAdvertiserCurrency: ttdworkflows.Float64(1146.61),
                CtrInPercent: ttdworkflows.Float64(3063.1),
                NielsenOTPInPercent: ttdworkflows.Float64(411.57),
                CpaInAdvertiserCurrency: nil,
                ReturnOnAdSpendPercent: ttdworkflows.Float64(7161.01),
                VcrInPercent: ttdworkflows.Float64(5983.85),
                ViewabilityInPercent: ttdworkflows.Float64(9094.92),
                VcpmInAdvertiserCurrency: ttdworkflows.Float64(1135.94),
                CpcvInAdvertiserCurrency: ttdworkflows.Float64(6372.45),
                MiaozhenOTPInPercent: ttdworkflows.Float64(8405.28),
            },
            CreativeIds: []string{
                "<value 1>",
                "<value 2>",
                "<value 3>",
            },
            AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                components.AdGroupWorkflowAssociateBidListInput{
                    BidListID: "<id>",
                    IsEnabled: ttdworkflows.Bool(true),
                    IsDefaultForDimension: ttdworkflows.Bool(true),
                },
            },
            Name: ttdworkflows.String("<value>"),
            Channel: components.AdGroupChannelNative.ToPointer(),
            FunnelLocation: components.AdGroupFunnelLocationConversion.ToPointer(),
        },
        AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
            KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                AreFutureKoaFeaturesEnabled: ttdworkflows.Bool(false),
                PredictiveClearingEnabled: ttdworkflows.Bool(true),
            },
            ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                IsEnabled: false,
                PopulationID: ttdworkflows.Int(935670),
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
                AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflows.Bool(true),
            },
            DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                []components.DimensionalBiddingDimensions{
                    components.DimensionalBiddingDimensionsHasContentLivestream,
                },
            },
            IsUseClicksAsConversionsEnabled: ttdworkflows.Bool(false),
            IsUseSecondaryConversionsEnabled: ttdworkflows.Bool(false),
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
                    CounterName: ttdworkflows.String("<value>"),
                    FrequencyCap: ttdworkflows.Int(685969),
                    FrequencyGoal: ttdworkflows.Int(448470),
                    ResetIntervalInMinutes: ttdworkflows.Int(577492),
                },
            },
            Flights: []components.AdGroupWorkflowFlightInput{
                components.AdGroupWorkflowFlightInput{
                    AllocationType: components.AllocationTypeMinimum.ToPointer(),
                    BudgetInAdvertiserCurrency: ttdworkflows.Float64(5325.23),
                    BudgetInImpressions: ttdworkflows.Int64(876101),
                    DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(44.58),
                    DailyTargetInImpressions: ttdworkflows.Int64(815686),
                    CampaignFlightID: 528311,
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Bool(false),
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

```go
package main

import(
	"context"
	"os"
	ttdworkflows "ttd-workflows"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.Archive(ctx, ttdworkflows.Bool(false), []string{
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

```go
package main

import(
	"context"
	"os"
	ttdworkflows "ttd-workflows"
	"ttd-workflows/models/components"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.AdGroups.BulkCreate(ctx, &components.AdGroupBulkCreateWorkflowInputWithValidation{
        Input: []components.AdGroupCreateWorkflowInput{},
        ValidateInputOnly: ttdworkflows.Bool(false),
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

```go
package main

import(
	"context"
	"os"
	ttdworkflows "ttd-workflows"
	"ttd-workflows/models/components"
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
                ID: ttdworkflows.String("<id>"),
                PrimaryInput: &components.AdGroupUpdateWorkflowPrimaryInput{
                    IsEnabled: ttdworkflows.Bool(false),
                    Description: ttdworkflows.String("stealthily miserable imaginary er since athwart er blah marten"),
                    Budget: &components.AdGroupWorkflowBudgetInput{
                        AllocationType: components.AllocationTypeMinimum.ToPointer(),
                        BudgetInAdvertiserCurrency: ttdworkflows.Float64(5440.47),
                        BudgetInImpressions: nil,
                        DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(6251.13),
                        DailyTargetInImpressions: ttdworkflows.Int64(931411),
                    },
                    BaseBidCPMInAdvertiserCurrency: ttdworkflows.Float64(188.02),
                    MaxBidCPMInAdvertiserCurrency: ttdworkflows.Float64(6077.98),
                    AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                        AudienceID: ttdworkflows.String("<id>"),
                        AudienceAcceleratorExclusionsEnabled: ttdworkflows.Bool(true),
                        AudienceBoosterEnabled: ttdworkflows.Bool(true),
                        AudienceExcluderEnabled: ttdworkflows.Bool(false),
                        AudiencePredictorEnabled: ttdworkflows.Bool(false),
                        CrossDeviceVendorListForAudience: []int{
                            27262,
                        },
                        RecencyExclusionWindowInMinutes: ttdworkflows.Int(676417),
                        TargetTrackableUsersEnabled: ttdworkflows.Bool(true),
                        UseMcIDAsPrimary: ttdworkflows.Bool(true),
                    },
                    RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflows.Bool(false),
                        MaximizeLtvIncrementalReach: ttdworkflows.Bool(true),
                        CpcInAdvertiserCurrency: nil,
                        CtrInPercent: ttdworkflows.Float64(2972.79),
                        NielsenOTPInPercent: ttdworkflows.Float64(4206.38),
                        CpaInAdvertiserCurrency: nil,
                        ReturnOnAdSpendPercent: ttdworkflows.Float64(842.94),
                        VcrInPercent: ttdworkflows.Float64(6307.13),
                        ViewabilityInPercent: ttdworkflows.Float64(9286.78),
                        VcpmInAdvertiserCurrency: ttdworkflows.Float64(8251.2),
                        CpcvInAdvertiserCurrency: ttdworkflows.Float64(4502.77),
                        MiaozhenOTPInPercent: ttdworkflows.Float64(2362.43),
                    },
                    CreativeIds: []string{
                        "<value 1>",
                    },
                    AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                        components.AdGroupWorkflowAssociateBidListInput{
                            BidListID: "<id>",
                            IsEnabled: ttdworkflows.Bool(true),
                            IsDefaultForDimension: ttdworkflows.Bool(true),
                        },
                    },
                    Name: ttdworkflows.String("<value>"),
                    Channel: components.AdGroupChannelTv.ToPointer(),
                    FunnelLocation: components.AdGroupFunnelLocationNone.ToPointer(),
                },
                AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
                    KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                        AreFutureKoaFeaturesEnabled: ttdworkflows.Bool(true),
                        PredictiveClearingEnabled: ttdworkflows.Bool(false),
                    },
                    ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                        IsEnabled: true,
                        PopulationID: ttdworkflows.Int(907569),
                        DemographicMemberIds: nil,
                        MobileDemographicMemberIds: []int{
                            169306,
                            568551,
                        },
                    },
                    ContractTargeting: &components.AdGroupWorkflowContractTargetingInput{
                        AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflows.Bool(true),
                    },
                    DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                        []components.DimensionalBiddingDimensions{
                            components.DimensionalBiddingDimensionsHasFrequencyAdjustmentID,
                        },
                    },
                    IsUseClicksAsConversionsEnabled: ttdworkflows.Bool(true),
                    IsUseSecondaryConversionsEnabled: ttdworkflows.Bool(true),
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
                            CounterName: ttdworkflows.String("<value>"),
                            FrequencyCap: ttdworkflows.Int(25438),
                            FrequencyGoal: ttdworkflows.Int(637221),
                            ResetIntervalInMinutes: ttdworkflows.Int(375296),
                        },
                    },
                    Flights: nil,
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Bool(true),
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