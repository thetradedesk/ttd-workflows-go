# Campaigns
(*Campaigns*)

## Overview

### Available Operations

* [CreateCampaign](#createcampaign) - Create a new campaign with required fields
* [Update](#update) - Update a campaign with specified fields
* [BulkCreate](#bulkcreate) - Create multiple new campaigns with required fields
* [BulkUpdate](#bulkupdate) - Update multiple campaigns with specified fields
* [Archive](#archive) - Archive multiple campaigns
* [GetCampaignVersion](#getcampaignversion) - Get a campaign's version

## CreateCampaign

Create a new campaign with required fields

### Example Usage

```go
package main

import(
	"context"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"github.com/thetradedesk/ttd-workflows-go/types"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflowsgo.New(
        ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.Campaigns.CreateCampaign(ctx, &components.CampaignCreateWorkflowInputWithValidation{
        PrimaryInput: components.CampaignCreateWorkflowPrimaryInput{
            Description: ttdworkflowsgo.String("woot furthermore mentor"),
            TimeZone: ttdworkflowsgo.String("Europe/Ulyanovsk"),
            CustomCPAClickWeight: ttdworkflowsgo.Float64(2561.01),
            CustomCPAViewthroughWeight: ttdworkflowsgo.Float64(5604.35),
            CustomCPAType: components.CustomCPATypeClickViewthroughWeighting.ToPointer(),
            ImpressionsOnlyBudgetingCpm: ttdworkflowsgo.Float64(1502.33),
            Budget: &components.CampaignWorkflowBudgetInput{
                PacingMode: components.CampaignPacingModePaceAsSoonAsPossible,
                BudgetInAdvertiserCurrency: 6363.35,
                BudgetInImpressions: ttdworkflowsgo.Int64(836518),
                DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(7814.79),
                DailyTargetInImpressions: ttdworkflowsgo.Int64(784985),
            },
            EndDateInUtc: nil,
            SeedID: nil,
            CampaignConversionReportingColumns: []components.CampaignWorkflowCampaignConversionReportingColumnInput{
                components.CampaignWorkflowCampaignConversionReportingColumnInput{
                    TrackingTagID: "<id>",
                    IncludeInCustomCPA: false,
                    ReportingColumnID: 888649,
                    ROASConfig: &components.CustomROASConfig{
                        IncludeInCustomROAS: false,
                        CustomROASWeight: ttdworkflowsgo.Float64(4766.9),
                        CustomROASClickWeight: ttdworkflowsgo.Float64(3310.24),
                        CustomROASViewthroughWeight: ttdworkflowsgo.Float64(2919.37),
                    },
                    Weight: ttdworkflowsgo.Float64(5369.43),
                    CrossDeviceAttributionModelID: ttdworkflowsgo.String("<id>"),
                },
            },
            AdvertiserID: "<id>",
            Name: "<value>",
            PrimaryChannel: components.CampaignChannelTypeDooh,
            PrimaryGoal: components.CampaignWorkflowROIGoalInput{
                MaximizeReach: ttdworkflowsgo.Bool(false),
                MaximizeLtvIncrementalReach: nil,
                CpcInAdvertiserCurrency: ttdworkflowsgo.Float64(6678.34),
                CtrInPercent: ttdworkflowsgo.Float64(5357.4),
                NielsenOTPInPercent: ttdworkflowsgo.Float64(2741.6),
                CpaInAdvertiserCurrency: ttdworkflowsgo.Float64(4220.63),
                ReturnOnAdSpendPercent: ttdworkflowsgo.Float64(8572.83),
                VcrInPercent: ttdworkflowsgo.Float64(8294.92),
                ViewabilityInPercent: ttdworkflowsgo.Float64(8592.21),
                VcpmInAdvertiserCurrency: ttdworkflowsgo.Float64(8388.8),
                CpcvInAdvertiserCurrency: nil,
                MiaozhenOTPInPercent: ttdworkflowsgo.Float64(3033.14),
            },
            StartDateInUtc: nil,
        },
        AdvancedInput: &components.CampaignWorkflowAdvancedInput{
            Flights: []components.CampaignWorkflowFlightInput{
                components.CampaignWorkflowFlightInput{
                    StartDateInclusiveUTC: types.MustTimeFromString("2024-07-08T10:52:56.944Z"),
                    EndDateExclusiveUTC: types.MustNewTimeFromString("2023-05-12T16:41:56.386Z"),
                    BudgetInAdvertiserCurrency: 5904.11,
                    BudgetInImpressions: nil,
                    DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(6112.24),
                    DailyTargetInImpressions: ttdworkflowsgo.Int64(333131),
                },
            },
            PurchaseOrderNumber: nil,
        },
        AdGroups: []components.CampaignCreateWorkflowAdGroupInput{
            components.CampaignCreateWorkflowAdGroupInput{
                PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
                    IsEnabled: ttdworkflowsgo.Bool(false),
                    Description: ttdworkflowsgo.String("quash lightly rot bashfully slope"),
                    Budget: &components.AdGroupWorkflowBudgetInput{
                        AllocationType: components.AllocationTypeMinimum.ToPointer(),
                        BudgetInAdvertiserCurrency: ttdworkflowsgo.Float64(4043.98),
                        BudgetInImpressions: ttdworkflowsgo.Int64(907414),
                        DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(49.95),
                        DailyTargetInImpressions: ttdworkflowsgo.Int64(62363),
                    },
                    BaseBidCPMInAdvertiserCurrency: ttdworkflowsgo.Float64(1136.89),
                    MaxBidCPMInAdvertiserCurrency: ttdworkflowsgo.Float64(6950.27),
                    AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                        AudienceID: ttdworkflowsgo.String("<id>"),
                        AudienceAcceleratorExclusionsEnabled: ttdworkflowsgo.Bool(false),
                        AudienceBoosterEnabled: ttdworkflowsgo.Bool(true),
                        AudienceExcluderEnabled: ttdworkflowsgo.Bool(false),
                        AudiencePredictorEnabled: ttdworkflowsgo.Bool(true),
                        CrossDeviceVendorListForAudience: []int{
                            458524,
                            284141,
                        },
                        RecencyExclusionWindowInMinutes: ttdworkflowsgo.Int(982426),
                        TargetTrackableUsersEnabled: ttdworkflowsgo.Bool(false),
                        UseMcIDAsPrimary: ttdworkflowsgo.Bool(true),
                    },
                    RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                        MaximizeReach: nil,
                        MaximizeLtvIncrementalReach: ttdworkflowsgo.Bool(true),
                        CpcInAdvertiserCurrency: ttdworkflowsgo.Float64(8782.74),
                        CtrInPercent: nil,
                        NielsenOTPInPercent: ttdworkflowsgo.Float64(7930.85),
                        CpaInAdvertiserCurrency: ttdworkflowsgo.Float64(4606.89),
                        ReturnOnAdSpendPercent: ttdworkflowsgo.Float64(2522.83),
                        VcrInPercent: ttdworkflowsgo.Float64(5828.49),
                        ViewabilityInPercent: ttdworkflowsgo.Float64(6824.44),
                        VcpmInAdvertiserCurrency: ttdworkflowsgo.Float64(7123.95),
                        CpcvInAdvertiserCurrency: ttdworkflowsgo.Float64(6233.72),
                        MiaozhenOTPInPercent: ttdworkflowsgo.Float64(8437.22),
                    },
                    CreativeIds: []string{
                        "<value 1>",
                    },
                    AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                        components.AdGroupWorkflowAssociateBidListInput{
                            BidListID: "<id>",
                            IsEnabled: ttdworkflowsgo.Bool(true),
                            IsDefaultForDimension: ttdworkflowsgo.Bool(false),
                        },
                    },
                    Name: ttdworkflowsgo.String("<value>"),
                    Channel: components.AdGroupChannelNativeVideo,
                    FunnelLocation: components.AdGroupFunnelLocationNone,
                    ProgrammaticGuaranteedPrivateContractID: ttdworkflowsgo.String("<id>"),
                },
                AdvancedInput: &components.CampaignCreateWorkflowAdGroupAdvancedInput{
                    KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                        AreFutureKoaFeaturesEnabled: ttdworkflowsgo.Bool(true),
                        PredictiveClearingEnabled: ttdworkflowsgo.Bool(true),
                    },
                    ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                        IsEnabled: false,
                        PopulationID: ttdworkflowsgo.Int(523753),
                        DemographicMemberIds: nil,
                        MobileDemographicMemberIds: nil,
                    },
                    ContractTargeting: &components.AdGroupWorkflowContractTargetingInput{
                        AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflowsgo.Bool(true),
                    },
                    DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                        []components.DimensionalBiddingDimensions{
                            components.DimensionalBiddingDimensionsHasFullReferrerURL,
                        },
                        []components.DimensionalBiddingDimensions{
                            components.DimensionalBiddingDimensionsHasPublisherID,
                        },
                    },
                    IsUseClicksAsConversionsEnabled: nil,
                    IsUseSecondaryConversionsEnabled: ttdworkflowsgo.Bool(true),
                    NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
                        EnhancedReportingOption: components.EnhancedNielsenReportingOptionsSite.ToPointer(),
                        Gender: components.TargetingGenderFemale,
                        StartAge: components.TargetingStartAgeThirtyFive,
                        EndAge: components.TargetingEndAgeFortyNine,
                        Countries: []string{},
                    },
                    NewFrequencyConfigs: []components.AdGroupWorkflowNewFrequencyConfigInput{
                        components.AdGroupWorkflowNewFrequencyConfigInput{
                            CounterName: ttdworkflowsgo.String("<value>"),
                            FrequencyCap: ttdworkflowsgo.Int(391231),
                            FrequencyGoal: ttdworkflowsgo.Int(499235),
                            ResetIntervalInMinutes: ttdworkflowsgo.Int(587736),
                        },
                    },
                    Flights: []components.CampaignCreateWorkflowAdGroupFlightInput{
                        components.CampaignCreateWorkflowAdGroupFlightInput{
                            AllocationType: components.AllocationTypeFixed.ToPointer(),
                            BudgetInAdvertiserCurrency: ttdworkflowsgo.Float64(5340.32),
                            BudgetInImpressions: ttdworkflowsgo.Int64(492382),
                            DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(5622.5),
                            DailyTargetInImpressions: ttdworkflowsgo.Int64(398919),
                        },
                    },
                },
            },
        },
        ValidateInputOnly: ttdworkflowsgo.Bool(false),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.CampaignPayload != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                    | Type                                                                                                                         | Required                                                                                                                     | Description                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                                                        | :heavy_check_mark:                                                                                                           | The context to use for the request.                                                                                          |
| `request`                                                                                                                    | [components.CampaignCreateWorkflowInputWithValidation](../../models/components/campaigncreateworkflowinputwithvalidation.md) | :heavy_check_mark:                                                                                                           | The request object to use for the request.                                                                                   |
| `opts`                                                                                                                       | [][operations.Option](../../models/operations/option.md)                                                                     | :heavy_minus_sign:                                                                                                           | The options for this request.                                                                                                |

### Response

**[*operations.CreateCampaignResponse](../../models/operations/createcampaignresponse.md), error**

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
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"github.com/thetradedesk/ttd-workflows-go/types"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflowsgo.New(
        ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.Campaigns.Update(ctx, &components.CampaignUpdateWorkflowInputWithValidation{
        ID: ttdworkflowsgo.String("<id>"),
        PrimaryInput: &components.CampaignUpdateWorkflowPrimaryInput{
            Description: ttdworkflowsgo.String("yahoo whether frail but into form sway neck notwithstanding"),
            TimeZone: ttdworkflowsgo.String("Asia/Amman"),
            CustomCPAClickWeight: ttdworkflowsgo.Float64(1380.93),
            CustomCPAViewthroughWeight: ttdworkflowsgo.Float64(3991.98),
            CustomCPAType: components.CustomCPATypeClickViewthroughWeighting.ToPointer(),
            ImpressionsOnlyBudgetingCpm: ttdworkflowsgo.Float64(126.57),
            Budget: &components.CampaignWorkflowBudgetInput{
                PacingMode: components.CampaignPacingModePaceAsSoonAsPossible,
                BudgetInAdvertiserCurrency: 6974.82,
                BudgetInImpressions: ttdworkflowsgo.Int64(834352),
                DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(8583.49),
                DailyTargetInImpressions: ttdworkflowsgo.Int64(746941),
            },
            EndDateInUtc: types.MustNewTimeFromString("2024-07-09T17:14:23.542Z"),
            SeedID: ttdworkflowsgo.String("<id>"),
            CampaignConversionReportingColumns: []components.CampaignWorkflowCampaignConversionReportingColumnInput{
                components.CampaignWorkflowCampaignConversionReportingColumnInput{
                    TrackingTagID: "<id>",
                    IncludeInCustomCPA: false,
                    ReportingColumnID: 716444,
                    ROASConfig: &components.CustomROASConfig{
                        IncludeInCustomROAS: true,
                        CustomROASWeight: ttdworkflowsgo.Float64(8307.9),
                        CustomROASClickWeight: ttdworkflowsgo.Float64(129.65),
                        CustomROASViewthroughWeight: ttdworkflowsgo.Float64(2890.82),
                    },
                    Weight: ttdworkflowsgo.Float64(5187.48),
                    CrossDeviceAttributionModelID: nil,
                },
            },
            Name: ttdworkflowsgo.String("<value>"),
            PrimaryChannel: components.CampaignChannelTypeDisplay.ToPointer(),
            PrimaryGoal: &components.CampaignWorkflowROIGoalInput{
                MaximizeReach: ttdworkflowsgo.Bool(false),
                MaximizeLtvIncrementalReach: ttdworkflowsgo.Bool(true),
                CpcInAdvertiserCurrency: ttdworkflowsgo.Float64(8835.54),
                CtrInPercent: ttdworkflowsgo.Float64(4975.78),
                NielsenOTPInPercent: ttdworkflowsgo.Float64(6033.78),
                CpaInAdvertiserCurrency: nil,
                ReturnOnAdSpendPercent: ttdworkflowsgo.Float64(5696.08),
                VcrInPercent: ttdworkflowsgo.Float64(8315.31),
                ViewabilityInPercent: ttdworkflowsgo.Float64(1059.68),
                VcpmInAdvertiserCurrency: ttdworkflowsgo.Float64(4588.07),
                CpcvInAdvertiserCurrency: ttdworkflowsgo.Float64(2202.71),
                MiaozhenOTPInPercent: ttdworkflowsgo.Float64(2682.12),
            },
            StartDateInUtc: types.MustNewTimeFromString("2024-02-29T10:31:50.069Z"),
        },
        AdvancedInput: &components.CampaignWorkflowAdvancedInput{
            Flights: []components.CampaignWorkflowFlightInput{
                components.CampaignWorkflowFlightInput{
                    StartDateInclusiveUTC: types.MustTimeFromString("2025-11-09T04:11:39.432Z"),
                    EndDateExclusiveUTC: types.MustNewTimeFromString("2025-09-10T20:38:51.701Z"),
                    BudgetInAdvertiserCurrency: 6534.57,
                    BudgetInImpressions: ttdworkflowsgo.Int64(865481),
                    DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(1033.72),
                    DailyTargetInImpressions: nil,
                },
            },
            PurchaseOrderNumber: ttdworkflowsgo.String("<value>"),
        },
        ValidateInputOnly: ttdworkflowsgo.Bool(true),
    })
    if err != nil {
        log.Fatal(err)
    }
    if res.CampaignPayload != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                                                                                    | Type                                                                                                                         | Required                                                                                                                     | Description                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `ctx`                                                                                                                        | [context.Context](https://pkg.go.dev/context#Context)                                                                        | :heavy_check_mark:                                                                                                           | The context to use for the request.                                                                                          |
| `request`                                                                                                                    | [components.CampaignUpdateWorkflowInputWithValidation](../../models/components/campaignupdateworkflowinputwithvalidation.md) | :heavy_check_mark:                                                                                                           | The request object to use for the request.                                                                                   |
| `opts`                                                                                                                       | [][operations.Option](../../models/operations/option.md)                                                                     | :heavy_minus_sign:                                                                                                           | The options for this request.                                                                                                |

### Response

**[*operations.UpdateCampaignResponse](../../models/operations/updatecampaignresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400                           | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## BulkCreate

Create multiple new campaigns with required fields

### Example Usage

```go
package main

import(
	"context"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"github.com/thetradedesk/ttd-workflows-go/types"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflowsgo.New(
        ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.Campaigns.BulkCreate(ctx, &components.CampaignBulkCreateWorkflowInputWithValidation{
        Input: []components.CampaignCreateWorkflowInput{
            components.CampaignCreateWorkflowInput{
                PrimaryInput: components.CampaignCreateWorkflowPrimaryInput{
                    Description: nil,
                    TimeZone: ttdworkflowsgo.String("America/North_Dakota/Center"),
                    CustomCPAClickWeight: ttdworkflowsgo.Float64(9662.9),
                    CustomCPAViewthroughWeight: ttdworkflowsgo.Float64(3558.78),
                    CustomCPAType: components.CustomCPATypeClickViewthroughWeighting.ToPointer(),
                    ImpressionsOnlyBudgetingCpm: ttdworkflowsgo.Float64(4427.56),
                    Budget: &components.CampaignWorkflowBudgetInput{
                        PacingMode: components.CampaignPacingModePaceAhead,
                        BudgetInAdvertiserCurrency: 5501.96,
                        BudgetInImpressions: ttdworkflowsgo.Int64(629784),
                        DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(2524.41),
                        DailyTargetInImpressions: ttdworkflowsgo.Int64(726807),
                    },
                    EndDateInUtc: types.MustNewTimeFromString("2023-12-21T01:12:20.772Z"),
                    SeedID: ttdworkflowsgo.String("<id>"),
                    CampaignConversionReportingColumns: []components.CampaignWorkflowCampaignConversionReportingColumnInput{
                        components.CampaignWorkflowCampaignConversionReportingColumnInput{
                            TrackingTagID: "<id>",
                            IncludeInCustomCPA: false,
                            ReportingColumnID: 356532,
                            ROASConfig: &components.CustomROASConfig{
                                IncludeInCustomROAS: false,
                                CustomROASWeight: ttdworkflowsgo.Float64(1483.03),
                                CustomROASClickWeight: ttdworkflowsgo.Float64(5286.76),
                                CustomROASViewthroughWeight: ttdworkflowsgo.Float64(8906.82),
                            },
                            Weight: nil,
                            CrossDeviceAttributionModelID: ttdworkflowsgo.String("<id>"),
                        },
                    },
                    AdvertiserID: "<id>",
                    Name: "<value>",
                    PrimaryChannel: components.CampaignChannelTypeNativeVideo,
                    PrimaryGoal: components.CampaignWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflowsgo.Bool(false),
                        MaximizeLtvIncrementalReach: ttdworkflowsgo.Bool(false),
                        CpcInAdvertiserCurrency: ttdworkflowsgo.Float64(25.32),
                        CtrInPercent: ttdworkflowsgo.Float64(4889.32),
                        NielsenOTPInPercent: ttdworkflowsgo.Float64(5258.8),
                        CpaInAdvertiserCurrency: ttdworkflowsgo.Float64(2553.01),
                        ReturnOnAdSpendPercent: ttdworkflowsgo.Float64(1142.91),
                        VcrInPercent: ttdworkflowsgo.Float64(1152.77),
                        ViewabilityInPercent: ttdworkflowsgo.Float64(6711.38),
                        VcpmInAdvertiserCurrency: ttdworkflowsgo.Float64(4528.37),
                        CpcvInAdvertiserCurrency: ttdworkflowsgo.Float64(9833.69),
                        MiaozhenOTPInPercent: ttdworkflowsgo.Float64(1951.58),
                    },
                    StartDateInUtc: types.MustNewTimeFromString("2025-09-26T21:06:42.946Z"),
                },
                AdvancedInput: &components.CampaignWorkflowAdvancedInput{
                    Flights: []components.CampaignWorkflowFlightInput{
                        components.CampaignWorkflowFlightInput{
                            StartDateInclusiveUTC: types.MustTimeFromString("2024-09-20T06:04:19.345Z"),
                            EndDateExclusiveUTC: types.MustNewTimeFromString("2024-01-18T07:43:56.299Z"),
                            BudgetInAdvertiserCurrency: 8219.9,
                            BudgetInImpressions: ttdworkflowsgo.Int64(76925),
                            DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(9309.03),
                            DailyTargetInImpressions: ttdworkflowsgo.Int64(152838),
                        },
                    },
                    PurchaseOrderNumber: ttdworkflowsgo.String("<value>"),
                },
                AdGroups: []components.CampaignCreateWorkflowAdGroupInput{
                    components.CampaignCreateWorkflowAdGroupInput{
                        PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
                            IsEnabled: ttdworkflowsgo.Bool(true),
                            Description: ttdworkflowsgo.String("scenario dish gracefully through tame yahoo pension husband as atop"),
                            Budget: &components.AdGroupWorkflowBudgetInput{
                                AllocationType: components.AllocationTypeMaximum.ToPointer(),
                                BudgetInAdvertiserCurrency: ttdworkflowsgo.Float64(2283.06),
                                BudgetInImpressions: ttdworkflowsgo.Int64(301691),
                                DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(9268.18),
                                DailyTargetInImpressions: ttdworkflowsgo.Int64(851470),
                            },
                            BaseBidCPMInAdvertiserCurrency: ttdworkflowsgo.Float64(694.78),
                            MaxBidCPMInAdvertiserCurrency: ttdworkflowsgo.Float64(6084.4),
                            AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                                AudienceID: ttdworkflowsgo.String("<id>"),
                                AudienceAcceleratorExclusionsEnabled: ttdworkflowsgo.Bool(true),
                                AudienceBoosterEnabled: ttdworkflowsgo.Bool(false),
                                AudienceExcluderEnabled: ttdworkflowsgo.Bool(true),
                                AudiencePredictorEnabled: ttdworkflowsgo.Bool(false),
                                CrossDeviceVendorListForAudience: []int{
                                    497890,
                                    566253,
                                },
                                RecencyExclusionWindowInMinutes: ttdworkflowsgo.Int(742665),
                                TargetTrackableUsersEnabled: ttdworkflowsgo.Bool(true),
                                UseMcIDAsPrimary: ttdworkflowsgo.Bool(true),
                            },
                            RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                                MaximizeReach: ttdworkflowsgo.Bool(false),
                                MaximizeLtvIncrementalReach: ttdworkflowsgo.Bool(true),
                                CpcInAdvertiserCurrency: ttdworkflowsgo.Float64(9062.02),
                                CtrInPercent: ttdworkflowsgo.Float64(7192.99),
                                NielsenOTPInPercent: ttdworkflowsgo.Float64(2823.22),
                                CpaInAdvertiserCurrency: ttdworkflowsgo.Float64(3140.25),
                                ReturnOnAdSpendPercent: ttdworkflowsgo.Float64(6857.21),
                                VcrInPercent: ttdworkflowsgo.Float64(2704.73),
                                ViewabilityInPercent: ttdworkflowsgo.Float64(2247.4),
                                VcpmInAdvertiserCurrency: ttdworkflowsgo.Float64(8383.69),
                                CpcvInAdvertiserCurrency: ttdworkflowsgo.Float64(4755.8),
                                MiaozhenOTPInPercent: ttdworkflowsgo.Float64(4575.86),
                            },
                            CreativeIds: []string{
                                "<value 1>",
                                "<value 2>",
                            },
                            AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                                components.AdGroupWorkflowAssociateBidListInput{
                                    BidListID: "<id>",
                                    IsEnabled: ttdworkflowsgo.Bool(true),
                                    IsDefaultForDimension: ttdworkflowsgo.Bool(false),
                                },
                            },
                            Name: ttdworkflowsgo.String("<value>"),
                            Channel: components.AdGroupChannelDisplay,
                            FunnelLocation: components.AdGroupFunnelLocationAwareness,
                            ProgrammaticGuaranteedPrivateContractID: ttdworkflowsgo.String("<id>"),
                        },
                        AdvancedInput: &components.CampaignCreateWorkflowAdGroupAdvancedInput{
                            KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                                AreFutureKoaFeaturesEnabled: ttdworkflowsgo.Bool(true),
                                PredictiveClearingEnabled: ttdworkflowsgo.Bool(false),
                            },
                            ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                                IsEnabled: false,
                                PopulationID: ttdworkflowsgo.Int(559587),
                                DemographicMemberIds: []int{
                                    139340,
                                    129935,
                                },
                                MobileDemographicMemberIds: nil,
                            },
                            ContractTargeting: &components.AdGroupWorkflowContractTargetingInput{
                                AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflowsgo.Bool(true),
                            },
                            DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                                []components.DimensionalBiddingDimensions{
                                    components.DimensionalBiddingDimensionsHasAudienceReachPercentageTierID,
                                },
                                []components.DimensionalBiddingDimensions{},
                            },
                            IsUseClicksAsConversionsEnabled: ttdworkflowsgo.Bool(false),
                            IsUseSecondaryConversionsEnabled: ttdworkflowsgo.Bool(true),
                            NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
                                EnhancedReportingOption: components.EnhancedNielsenReportingOptionsNone.ToPointer(),
                                Gender: components.TargetingGenderFemale,
                                StartAge: components.TargetingStartAgeThirtyFive,
                                EndAge: components.TargetingEndAgeTwentyFour,
                                Countries: []string{
                                    "<value 1>",
                                    "<value 2>",
                                },
                            },
                            NewFrequencyConfigs: nil,
                            Flights: []components.CampaignCreateWorkflowAdGroupFlightInput{
                                components.CampaignCreateWorkflowAdGroupFlightInput{
                                    AllocationType: components.AllocationTypeMaximum.ToPointer(),
                                    BudgetInAdvertiserCurrency: ttdworkflowsgo.Float64(4838.47),
                                    BudgetInImpressions: ttdworkflowsgo.Int64(420224),
                                    DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(1513.78),
                                    DailyTargetInImpressions: ttdworkflowsgo.Int64(735500),
                                },
                            },
                        },
                    },
                },
            },
        },
        ValidateInputOnly: ttdworkflowsgo.Bool(true),
        CallbackInput: &components.WorkflowCallbackInput{
            CallbackURL: "https://impeccable-pick.com/",
            CallbackHeaders: map[string]string{
                "key": "<value>",
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

| Parameter                                                                                                                            | Type                                                                                                                                 | Required                                                                                                                             | Description                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                                                                | :heavy_check_mark:                                                                                                                   | The context to use for the request.                                                                                                  |
| `request`                                                                                                                            | [components.CampaignBulkCreateWorkflowInputWithValidation](../../models/components/campaignbulkcreateworkflowinputwithvalidation.md) | :heavy_check_mark:                                                                                                                   | The request object to use for the request.                                                                                           |
| `opts`                                                                                                                               | [][operations.Option](../../models/operations/option.md)                                                                             | :heavy_minus_sign:                                                                                                                   | The options for this request.                                                                                                        |

### Response

**[*operations.CreateCampaignsJobResponse](../../models/operations/createcampaignsjobresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 403                      | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## BulkUpdate

Only the fields provided in the request payload for each specific campaign will be updated.

### Example Usage

```go
package main

import(
	"context"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"github.com/thetradedesk/ttd-workflows-go/types"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflowsgo.New(
        ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.Campaigns.BulkUpdate(ctx, &components.CampaignBulkUpdateWorkflowInputWithValidation{
        Input: []components.CampaignUpdateWorkflowInput{
            components.CampaignUpdateWorkflowInput{
                ID: ttdworkflowsgo.String("<id>"),
                PrimaryInput: &components.CampaignUpdateWorkflowPrimaryInput{
                    Description: ttdworkflowsgo.String("hmph energetically yet surprisingly swift knight swear multicolored absent"),
                    TimeZone: ttdworkflowsgo.String("America/Argentina/San_Juan"),
                    CustomCPAClickWeight: nil,
                    CustomCPAViewthroughWeight: ttdworkflowsgo.Float64(8361.84),
                    CustomCPAType: components.CustomCPATypePixelWeighting.ToPointer(),
                    ImpressionsOnlyBudgetingCpm: ttdworkflowsgo.Float64(2706.4),
                    Budget: &components.CampaignWorkflowBudgetInput{
                        PacingMode: components.CampaignPacingModePaceAsSoonAsPossible,
                        BudgetInAdvertiserCurrency: 2564.89,
                        BudgetInImpressions: ttdworkflowsgo.Int64(659726),
                        DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(6514.48),
                        DailyTargetInImpressions: ttdworkflowsgo.Int64(892097),
                    },
                    EndDateInUtc: types.MustNewTimeFromString("2023-11-11T21:39:56.025Z"),
                    SeedID: ttdworkflowsgo.String("<id>"),
                    CampaignConversionReportingColumns: []components.CampaignWorkflowCampaignConversionReportingColumnInput{
                        components.CampaignWorkflowCampaignConversionReportingColumnInput{
                            TrackingTagID: "<id>",
                            IncludeInCustomCPA: true,
                            ReportingColumnID: 809247,
                            ROASConfig: &components.CustomROASConfig{
                                IncludeInCustomROAS: false,
                                CustomROASWeight: nil,
                                CustomROASClickWeight: nil,
                                CustomROASViewthroughWeight: ttdworkflowsgo.Float64(6784.9),
                            },
                            Weight: ttdworkflowsgo.Float64(2260.69),
                            CrossDeviceAttributionModelID: ttdworkflowsgo.String("<id>"),
                        },
                    },
                    Name: ttdworkflowsgo.String("<value>"),
                    PrimaryChannel: components.CampaignChannelTypeNone.ToPointer(),
                    PrimaryGoal: &components.CampaignWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflowsgo.Bool(true),
                        MaximizeLtvIncrementalReach: ttdworkflowsgo.Bool(false),
                        CpcInAdvertiserCurrency: ttdworkflowsgo.Float64(3354.68),
                        CtrInPercent: ttdworkflowsgo.Float64(7716.49),
                        NielsenOTPInPercent: nil,
                        CpaInAdvertiserCurrency: ttdworkflowsgo.Float64(381.7),
                        ReturnOnAdSpendPercent: ttdworkflowsgo.Float64(8461.44),
                        VcrInPercent: ttdworkflowsgo.Float64(4170.61),
                        ViewabilityInPercent: ttdworkflowsgo.Float64(5364.85),
                        VcpmInAdvertiserCurrency: ttdworkflowsgo.Float64(1107.08),
                        CpcvInAdvertiserCurrency: nil,
                        MiaozhenOTPInPercent: ttdworkflowsgo.Float64(4584.96),
                    },
                    StartDateInUtc: types.MustNewTimeFromString("2023-01-13T23:06:05.083Z"),
                },
                AdvancedInput: &components.CampaignWorkflowAdvancedInput{
                    Flights: []components.CampaignWorkflowFlightInput{
                        components.CampaignWorkflowFlightInput{
                            StartDateInclusiveUTC: types.MustTimeFromString("2023-08-14T13:47:31.198Z"),
                            EndDateExclusiveUTC: types.MustNewTimeFromString("2024-07-07T14:46:57.378Z"),
                            BudgetInAdvertiserCurrency: 1874.95,
                            BudgetInImpressions: ttdworkflowsgo.Int64(207094),
                            DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(7255.71),
                            DailyTargetInImpressions: ttdworkflowsgo.Int64(760981),
                        },
                    },
                    PurchaseOrderNumber: ttdworkflowsgo.String("<value>"),
                },
            },
        },
        ValidateInputOnly: ttdworkflowsgo.Bool(true),
        CallbackInput: &components.WorkflowCallbackInput{
            CallbackURL: "https://soggy-apparatus.org/",
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

| Parameter                                                                                                                            | Type                                                                                                                                 | Required                                                                                                                             | Description                                                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| `ctx`                                                                                                                                | [context.Context](https://pkg.go.dev/context#Context)                                                                                | :heavy_check_mark:                                                                                                                   | The context to use for the request.                                                                                                  |
| `request`                                                                                                                            | [components.CampaignBulkUpdateWorkflowInputWithValidation](../../models/components/campaignbulkupdateworkflowinputwithvalidation.md) | :heavy_check_mark:                                                                                                                   | The request object to use for the request.                                                                                           |
| `opts`                                                                                                                               | [][operations.Option](../../models/operations/option.md)                                                                             | :heavy_minus_sign:                                                                                                                   | The options for this request.                                                                                                        |

### Response

**[*operations.UpdateCampaignsJobResponse](../../models/operations/updatecampaignsjobresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 403                      | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## Archive

**NOTE**: Once archived, campaigns cannot be un-archived.

### Example Usage

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

    res, err := s.Campaigns.Archive(ctx, ttdworkflowsgo.Bool(false), []string{
        "<value 1>",
        "<value 2>",
        "<value 3>",
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

**[*operations.ArchiveCampaignsResponse](../../models/operations/archivecampaignsresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 403                      | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |

## GetCampaignVersion

Get a campaign's version

### Example Usage

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

    res, err := s.Campaigns.GetCampaignVersion(ctx, "<id>")
    if err != nil {
        log.Fatal(err)
    }
    if res.CampaignVersionWorkflow != nil {
        // handle response
    }
}
```

### Parameters

| Parameter                                                | Type                                                     | Required                                                 | Description                                              |
| -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- |
| `ctx`                                                    | [context.Context](https://pkg.go.dev/context#Context)    | :heavy_check_mark:                                       | The context to use for the request.                      |
| `id`                                                     | *string*                                                 | :heavy_check_mark:                                       | N/A                                                      |
| `opts`                                                   | [][operations.Option](../../models/operations/option.md) | :heavy_minus_sign:                                       | The options for this request.                            |

### Response

**[*operations.GetCampaignVersionResponse](../../models/operations/getcampaignversionresponse.md), error**

### Errors

| Error Type                    | Status Code                   | Content Type                  |
| ----------------------------- | ----------------------------- | ----------------------------- |
| apierrors.ProblemDetailsError | 400, 401, 403, 404            | application/json              |
| apierrors.APIError            | 4XX, 5XX                      | \*/\*                         |