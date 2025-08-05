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

<!-- UsageSnippet language="go" operationID="createCampaign" method="post" path="/campaign" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"github.com/thetradedesk/ttd-workflows-go/types"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.Campaigns.CreateCampaign(ctx, &components.CampaignCreateWorkflowInputWithValidation{
        PrimaryInput: components.CampaignCreateWorkflowPrimaryInput{
            Description: ttdworkflows.String("woot furthermore mentor"),
            CampaignGroupID: ttdworkflows.Int64(86586),
            TimeZone: ttdworkflows.String("Europe/Ulyanovsk"),
            CustomCPAClickWeight: ttdworkflows.Float64(2561.01),
            CustomCPAViewthroughWeight: ttdworkflows.Float64(5604.35),
            CustomCPAType: components.CustomCPATypeClickViewthroughWeighting.ToPointer(),
            ImpressionsOnlyBudgetingCpm: ttdworkflows.Float64(1502.33),
            Budget: &components.CampaignWorkflowBudgetInput{
                PacingMode: components.CampaignPacingModePaceAsSoonAsPossible,
                BudgetInAdvertiserCurrency: 6363.35,
                BudgetInImpressions: ttdworkflows.Int64(836518),
                DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(7814.79),
                DailyTargetInImpressions: ttdworkflows.Int64(784985),
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
                        CustomROASWeight: ttdworkflows.Float64(4766.9),
                        CustomROASClickWeight: ttdworkflows.Float64(3310.24),
                        CustomROASViewthroughWeight: ttdworkflows.Float64(2919.37),
                    },
                    Weight: ttdworkflows.Float64(5369.43),
                    CrossDeviceAttributionModelID: ttdworkflows.String("<id>"),
                },
            },
            AdvertiserID: "<id>",
            Name: "<value>",
            PrimaryChannel: components.CampaignChannelTypeDooh,
            PrimaryGoal: components.CampaignWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Bool(false),
                MaximizeLtvIncrementalReach: nil,
                CpcInAdvertiserCurrency: ttdworkflows.Float64(6678.34),
                CtrInPercent: ttdworkflows.Float64(5357.4),
                NielsenOTPInPercent: ttdworkflows.Float64(2741.6),
                CpaInAdvertiserCurrency: ttdworkflows.Float64(4220.63),
                ReturnOnAdSpendPercent: ttdworkflows.Float64(8572.83),
                VcrInPercent: ttdworkflows.Float64(8294.92),
                ViewabilityInPercent: ttdworkflows.Float64(8592.21),
                VcpmInAdvertiserCurrency: ttdworkflows.Float64(8388.8),
                CpcvInAdvertiserCurrency: nil,
                MiaozhenOTPInPercent: ttdworkflows.Float64(3033.14),
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
                    DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(6112.24),
                    DailyTargetInImpressions: ttdworkflows.Int64(333131),
                },
            },
            PurchaseOrderNumber: nil,
        },
        AdGroups: []components.CampaignCreateWorkflowAdGroupInput{
            components.CampaignCreateWorkflowAdGroupInput{
                PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
                    IsEnabled: ttdworkflows.Bool(false),
                    Description: ttdworkflows.String("quash lightly rot bashfully slope"),
                    Budget: &components.AdGroupWorkflowBudgetInput{
                        AllocationType: components.AllocationTypeMinimum.ToPointer(),
                        BudgetInAdvertiserCurrency: ttdworkflows.Float64(4043.98),
                        BudgetInImpressions: ttdworkflows.Int64(907414),
                        DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(49.95),
                        DailyTargetInImpressions: ttdworkflows.Int64(62363),
                    },
                    BaseBidCPMInAdvertiserCurrency: ttdworkflows.Float64(1136.89),
                    MaxBidCPMInAdvertiserCurrency: ttdworkflows.Float64(6950.27),
                    AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                        AudienceID: ttdworkflows.String("<id>"),
                        AudienceAcceleratorExclusionsEnabled: ttdworkflows.Bool(false),
                        AudienceBoosterEnabled: ttdworkflows.Bool(true),
                        AudienceExcluderEnabled: ttdworkflows.Bool(false),
                        AudiencePredictorEnabled: ttdworkflows.Bool(true),
                        CrossDeviceVendorListForAudience: []int{
                            458524,
                            284141,
                        },
                        RecencyExclusionWindowInMinutes: ttdworkflows.Int(982426),
                        TargetTrackableUsersEnabled: ttdworkflows.Bool(false),
                        UseMcIDAsPrimary: ttdworkflows.Bool(true),
                    },
                    RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                        MaximizeReach: nil,
                        MaximizeLtvIncrementalReach: ttdworkflows.Bool(true),
                        CpcInAdvertiserCurrency: ttdworkflows.Float64(8782.74),
                        CtrInPercent: nil,
                        NielsenOTPInPercent: ttdworkflows.Float64(7930.85),
                        CpaInAdvertiserCurrency: ttdworkflows.Float64(4606.89),
                        ReturnOnAdSpendPercent: ttdworkflows.Float64(2522.83),
                        VcrInPercent: ttdworkflows.Float64(5828.49),
                        ViewabilityInPercent: ttdworkflows.Float64(6824.44),
                        VcpmInAdvertiserCurrency: ttdworkflows.Float64(7123.95),
                        CpcvInAdvertiserCurrency: ttdworkflows.Float64(6233.72),
                        MiaozhenOTPInPercent: ttdworkflows.Float64(8437.22),
                    },
                    CreativeIds: []string{
                        "<value 1>",
                    },
                    AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                        components.AdGroupWorkflowAssociateBidListInput{
                            BidListID: "<id>",
                            IsEnabled: ttdworkflows.Bool(true),
                            IsDefaultForDimension: ttdworkflows.Bool(false),
                        },
                    },
                    Name: ttdworkflows.String("<value>"),
                    Channel: components.AdGroupChannelNativeVideo,
                    FunnelLocation: components.AdGroupFunnelLocationNone,
                    ProgrammaticGuaranteedPrivateContractID: ttdworkflows.String("<id>"),
                },
                AdvancedInput: &components.CampaignCreateWorkflowAdGroupAdvancedInput{
                    KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                        AreFutureKoaFeaturesEnabled: ttdworkflows.Bool(true),
                        PredictiveClearingEnabled: ttdworkflows.Bool(true),
                    },
                    ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                        IsEnabled: false,
                        PopulationID: ttdworkflows.Int(523753),
                        DemographicMemberIds: nil,
                        MobileDemographicMemberIds: nil,
                    },
                    ContractTargeting: &components.AdGroupWorkflowContractTargetingInput{
                        AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflows.Bool(true),
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
                    IsUseSecondaryConversionsEnabled: ttdworkflows.Bool(true),
                    NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
                        EnhancedReportingOption: components.EnhancedNielsenReportingOptionsSite.ToPointer(),
                        Gender: components.TargetingGenderFemale,
                        StartAge: components.TargetingStartAgeThirtyFive,
                        EndAge: components.TargetingEndAgeFortyNine,
                        Countries: []string{},
                    },
                    NewFrequencyConfigs: []components.AdGroupWorkflowNewFrequencyConfigInput{
                        components.AdGroupWorkflowNewFrequencyConfigInput{
                            CounterName: ttdworkflows.String("<value>"),
                            FrequencyCap: ttdworkflows.Int(391231),
                            FrequencyGoal: ttdworkflows.Int(499235),
                            ResetIntervalInMinutes: ttdworkflows.Int(587736),
                        },
                    },
                    Flights: []components.CampaignCreateWorkflowAdGroupFlightInput{
                        components.CampaignCreateWorkflowAdGroupFlightInput{
                            AllocationType: components.AllocationTypeFixed.ToPointer(),
                            BudgetInAdvertiserCurrency: ttdworkflows.Float64(5340.32),
                            BudgetInImpressions: ttdworkflows.Int64(492382),
                            DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(5622.5),
                            DailyTargetInImpressions: ttdworkflows.Int64(398919),
                        },
                    },
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Bool(false),
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

<!-- UsageSnippet language="go" operationID="updateCampaign" method="patch" path="/campaign" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"github.com/thetradedesk/ttd-workflows-go/types"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.Campaigns.Update(ctx, &components.CampaignUpdateWorkflowInputWithValidation{
        ID: ttdworkflows.String("<id>"),
        PrimaryInput: &components.CampaignUpdateWorkflowPrimaryInput{
            Description: ttdworkflows.String("yahoo whether frail but into form sway neck notwithstanding"),
            CampaignGroupID: ttdworkflows.Int64(760468),
            TimeZone: ttdworkflows.String("Asia/Amman"),
            CustomCPAClickWeight: ttdworkflows.Float64(1380.93),
            CustomCPAViewthroughWeight: ttdworkflows.Float64(3991.98),
            CustomCPAType: components.CustomCPATypeClickViewthroughWeighting.ToPointer(),
            ImpressionsOnlyBudgetingCpm: ttdworkflows.Float64(126.57),
            Budget: &components.CampaignWorkflowBudgetInput{
                PacingMode: components.CampaignPacingModePaceAsSoonAsPossible,
                BudgetInAdvertiserCurrency: 6974.82,
                BudgetInImpressions: ttdworkflows.Int64(834352),
                DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(8583.49),
                DailyTargetInImpressions: ttdworkflows.Int64(746941),
            },
            EndDateInUtc: types.MustNewTimeFromString("2024-07-09T17:14:23.542Z"),
            SeedID: ttdworkflows.String("<id>"),
            CampaignConversionReportingColumns: []components.CampaignWorkflowCampaignConversionReportingColumnInput{
                components.CampaignWorkflowCampaignConversionReportingColumnInput{
                    TrackingTagID: "<id>",
                    IncludeInCustomCPA: false,
                    ReportingColumnID: 716444,
                    ROASConfig: &components.CustomROASConfig{
                        IncludeInCustomROAS: true,
                        CustomROASWeight: ttdworkflows.Float64(8307.9),
                        CustomROASClickWeight: ttdworkflows.Float64(129.65),
                        CustomROASViewthroughWeight: ttdworkflows.Float64(2890.82),
                    },
                    Weight: ttdworkflows.Float64(5187.48),
                    CrossDeviceAttributionModelID: nil,
                },
            },
            Name: ttdworkflows.String("<value>"),
            PrimaryChannel: components.CampaignChannelTypeDisplay.ToPointer(),
            PrimaryGoal: &components.CampaignWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Bool(false),
                MaximizeLtvIncrementalReach: ttdworkflows.Bool(true),
                CpcInAdvertiserCurrency: ttdworkflows.Float64(8835.54),
                CtrInPercent: ttdworkflows.Float64(4975.78),
                NielsenOTPInPercent: ttdworkflows.Float64(6033.78),
                CpaInAdvertiserCurrency: nil,
                ReturnOnAdSpendPercent: ttdworkflows.Float64(5696.08),
                VcrInPercent: ttdworkflows.Float64(8315.31),
                ViewabilityInPercent: ttdworkflows.Float64(1059.68),
                VcpmInAdvertiserCurrency: ttdworkflows.Float64(4588.07),
                CpcvInAdvertiserCurrency: ttdworkflows.Float64(2202.71),
                MiaozhenOTPInPercent: ttdworkflows.Float64(2682.12),
            },
            StartDateInUtc: types.MustNewTimeFromString("2024-02-29T10:31:50.069Z"),
        },
        AdvancedInput: &components.CampaignWorkflowAdvancedInput{
            Flights: []components.CampaignWorkflowFlightInput{
                components.CampaignWorkflowFlightInput{
                    StartDateInclusiveUTC: types.MustTimeFromString("2025-11-09T04:11:39.432Z"),
                    EndDateExclusiveUTC: types.MustNewTimeFromString("2025-09-10T20:38:51.701Z"),
                    BudgetInAdvertiserCurrency: 6534.57,
                    BudgetInImpressions: ttdworkflows.Int64(865481),
                    DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(1033.72),
                    DailyTargetInImpressions: nil,
                },
            },
            PurchaseOrderNumber: ttdworkflows.String("<value>"),
        },
        ValidateInputOnly: ttdworkflows.Bool(true),
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

<!-- UsageSnippet language="go" operationID="createCampaignsJob" method="post" path="/standardjob/campaign/bulk" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"github.com/thetradedesk/ttd-workflows-go/types"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.Campaigns.BulkCreate(ctx, &components.CampaignBulkCreateWorkflowInputWithValidation{
        Input: []components.CampaignCreateWorkflowInput{
            components.CampaignCreateWorkflowInput{
                PrimaryInput: components.CampaignCreateWorkflowPrimaryInput{
                    Description: nil,
                    CampaignGroupID: ttdworkflows.Int64(657704),
                    TimeZone: ttdworkflows.String("America/North_Dakota/Center"),
                    CustomCPAClickWeight: ttdworkflows.Float64(9662.9),
                    CustomCPAViewthroughWeight: ttdworkflows.Float64(3558.78),
                    CustomCPAType: components.CustomCPATypeClickViewthroughWeighting.ToPointer(),
                    ImpressionsOnlyBudgetingCpm: ttdworkflows.Float64(4427.56),
                    Budget: &components.CampaignWorkflowBudgetInput{
                        PacingMode: components.CampaignPacingModePaceAhead,
                        BudgetInAdvertiserCurrency: 5501.96,
                        BudgetInImpressions: ttdworkflows.Int64(629784),
                        DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(2524.41),
                        DailyTargetInImpressions: ttdworkflows.Int64(726807),
                    },
                    EndDateInUtc: types.MustNewTimeFromString("2023-12-21T01:12:20.772Z"),
                    SeedID: ttdworkflows.String("<id>"),
                    CampaignConversionReportingColumns: []components.CampaignWorkflowCampaignConversionReportingColumnInput{
                        components.CampaignWorkflowCampaignConversionReportingColumnInput{
                            TrackingTagID: "<id>",
                            IncludeInCustomCPA: false,
                            ReportingColumnID: 356532,
                            ROASConfig: &components.CustomROASConfig{
                                IncludeInCustomROAS: false,
                                CustomROASWeight: ttdworkflows.Float64(1483.03),
                                CustomROASClickWeight: ttdworkflows.Float64(5286.76),
                                CustomROASViewthroughWeight: ttdworkflows.Float64(8906.82),
                            },
                            Weight: nil,
                            CrossDeviceAttributionModelID: ttdworkflows.String("<id>"),
                        },
                    },
                    AdvertiserID: "<id>",
                    Name: "<value>",
                    PrimaryChannel: components.CampaignChannelTypeNativeVideo,
                    PrimaryGoal: components.CampaignWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflows.Bool(false),
                        MaximizeLtvIncrementalReach: ttdworkflows.Bool(false),
                        CpcInAdvertiserCurrency: ttdworkflows.Float64(25.32),
                        CtrInPercent: ttdworkflows.Float64(4889.32),
                        NielsenOTPInPercent: ttdworkflows.Float64(5258.8),
                        CpaInAdvertiserCurrency: ttdworkflows.Float64(2553.01),
                        ReturnOnAdSpendPercent: ttdworkflows.Float64(1142.91),
                        VcrInPercent: ttdworkflows.Float64(1152.77),
                        ViewabilityInPercent: ttdworkflows.Float64(6711.38),
                        VcpmInAdvertiserCurrency: ttdworkflows.Float64(4528.37),
                        CpcvInAdvertiserCurrency: ttdworkflows.Float64(9833.69),
                        MiaozhenOTPInPercent: ttdworkflows.Float64(1951.58),
                    },
                    StartDateInUtc: types.MustNewTimeFromString("2025-09-26T21:06:42.946Z"),
                },
                AdvancedInput: &components.CampaignWorkflowAdvancedInput{
                    Flights: []components.CampaignWorkflowFlightInput{
                        components.CampaignWorkflowFlightInput{
                            StartDateInclusiveUTC: types.MustTimeFromString("2024-09-20T06:04:19.345Z"),
                            EndDateExclusiveUTC: types.MustNewTimeFromString("2024-01-18T07:43:56.299Z"),
                            BudgetInAdvertiserCurrency: 8219.9,
                            BudgetInImpressions: ttdworkflows.Int64(76925),
                            DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(9309.03),
                            DailyTargetInImpressions: ttdworkflows.Int64(152838),
                        },
                    },
                    PurchaseOrderNumber: ttdworkflows.String("<value>"),
                },
                AdGroups: []components.CampaignCreateWorkflowAdGroupInput{
                    components.CampaignCreateWorkflowAdGroupInput{
                        PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
                            IsEnabled: ttdworkflows.Bool(true),
                            Description: ttdworkflows.String("scenario dish gracefully through tame yahoo pension husband as atop"),
                            Budget: &components.AdGroupWorkflowBudgetInput{
                                AllocationType: components.AllocationTypeMaximum.ToPointer(),
                                BudgetInAdvertiserCurrency: ttdworkflows.Float64(2283.06),
                                BudgetInImpressions: ttdworkflows.Int64(301691),
                                DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(9268.18),
                                DailyTargetInImpressions: ttdworkflows.Int64(851470),
                            },
                            BaseBidCPMInAdvertiserCurrency: ttdworkflows.Float64(694.78),
                            MaxBidCPMInAdvertiserCurrency: ttdworkflows.Float64(6084.4),
                            AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                                AudienceID: ttdworkflows.String("<id>"),
                                AudienceAcceleratorExclusionsEnabled: ttdworkflows.Bool(true),
                                AudienceBoosterEnabled: ttdworkflows.Bool(false),
                                AudienceExcluderEnabled: ttdworkflows.Bool(true),
                                AudiencePredictorEnabled: ttdworkflows.Bool(false),
                                CrossDeviceVendorListForAudience: []int{
                                    497890,
                                    566253,
                                },
                                RecencyExclusionWindowInMinutes: ttdworkflows.Int(742665),
                                TargetTrackableUsersEnabled: ttdworkflows.Bool(true),
                                UseMcIDAsPrimary: ttdworkflows.Bool(true),
                            },
                            RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                                MaximizeReach: ttdworkflows.Bool(false),
                                MaximizeLtvIncrementalReach: ttdworkflows.Bool(true),
                                CpcInAdvertiserCurrency: ttdworkflows.Float64(9062.02),
                                CtrInPercent: ttdworkflows.Float64(7192.99),
                                NielsenOTPInPercent: ttdworkflows.Float64(2823.22),
                                CpaInAdvertiserCurrency: ttdworkflows.Float64(3140.25),
                                ReturnOnAdSpendPercent: ttdworkflows.Float64(6857.21),
                                VcrInPercent: ttdworkflows.Float64(2704.73),
                                ViewabilityInPercent: ttdworkflows.Float64(2247.4),
                                VcpmInAdvertiserCurrency: ttdworkflows.Float64(8383.69),
                                CpcvInAdvertiserCurrency: ttdworkflows.Float64(4755.8),
                                MiaozhenOTPInPercent: ttdworkflows.Float64(4575.86),
                            },
                            CreativeIds: []string{
                                "<value 1>",
                                "<value 2>",
                            },
                            AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                                components.AdGroupWorkflowAssociateBidListInput{
                                    BidListID: "<id>",
                                    IsEnabled: ttdworkflows.Bool(true),
                                    IsDefaultForDimension: ttdworkflows.Bool(false),
                                },
                            },
                            Name: ttdworkflows.String("<value>"),
                            Channel: components.AdGroupChannelDisplay,
                            FunnelLocation: components.AdGroupFunnelLocationAwareness,
                            ProgrammaticGuaranteedPrivateContractID: ttdworkflows.String("<id>"),
                        },
                        AdvancedInput: &components.CampaignCreateWorkflowAdGroupAdvancedInput{
                            KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                                AreFutureKoaFeaturesEnabled: ttdworkflows.Bool(true),
                                PredictiveClearingEnabled: ttdworkflows.Bool(false),
                            },
                            ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                                IsEnabled: false,
                                PopulationID: ttdworkflows.Int(559587),
                                DemographicMemberIds: []int{
                                    139340,
                                    129935,
                                },
                                MobileDemographicMemberIds: nil,
                            },
                            ContractTargeting: &components.AdGroupWorkflowContractTargetingInput{
                                AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflows.Bool(true),
                            },
                            DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                                []components.DimensionalBiddingDimensions{
                                    components.DimensionalBiddingDimensionsHasAudienceReachPercentageTierID,
                                },
                                []components.DimensionalBiddingDimensions{},
                            },
                            IsUseClicksAsConversionsEnabled: ttdworkflows.Bool(false),
                            IsUseSecondaryConversionsEnabled: ttdworkflows.Bool(true),
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
                                    BudgetInAdvertiserCurrency: ttdworkflows.Float64(4838.47),
                                    BudgetInImpressions: ttdworkflows.Int64(420224),
                                    DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(1513.78),
                                    DailyTargetInImpressions: ttdworkflows.Int64(735500),
                                },
                            },
                        },
                    },
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Bool(true),
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

<!-- UsageSnippet language="go" operationID="updateCampaignsJob" method="patch" path="/standardjob/campaign/bulk" -->
```go
package main

import(
	"context"
	"os"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"github.com/thetradedesk/ttd-workflows-go/types"
	"log"
)

func main() {
    ctx := context.Background()

    s := ttdworkflows.New(
        ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
    )

    res, err := s.Campaigns.BulkUpdate(ctx, &components.CampaignBulkUpdateWorkflowInputWithValidation{
        Input: []components.CampaignUpdateWorkflowInput{
            components.CampaignUpdateWorkflowInput{
                ID: ttdworkflows.String("<id>"),
                PrimaryInput: &components.CampaignUpdateWorkflowPrimaryInput{
                    Description: ttdworkflows.String("hmph energetically yet surprisingly swift knight swear multicolored absent"),
                    CampaignGroupID: ttdworkflows.Int64(645576),
                    TimeZone: ttdworkflows.String("America/Argentina/San_Juan"),
                    CustomCPAClickWeight: nil,
                    CustomCPAViewthroughWeight: ttdworkflows.Float64(8361.84),
                    CustomCPAType: components.CustomCPATypePixelWeighting.ToPointer(),
                    ImpressionsOnlyBudgetingCpm: ttdworkflows.Float64(2706.4),
                    Budget: &components.CampaignWorkflowBudgetInput{
                        PacingMode: components.CampaignPacingModePaceAsSoonAsPossible,
                        BudgetInAdvertiserCurrency: 2564.89,
                        BudgetInImpressions: ttdworkflows.Int64(659726),
                        DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(6514.48),
                        DailyTargetInImpressions: ttdworkflows.Int64(892097),
                    },
                    EndDateInUtc: types.MustNewTimeFromString("2023-11-11T21:39:56.025Z"),
                    SeedID: ttdworkflows.String("<id>"),
                    CampaignConversionReportingColumns: []components.CampaignWorkflowCampaignConversionReportingColumnInput{
                        components.CampaignWorkflowCampaignConversionReportingColumnInput{
                            TrackingTagID: "<id>",
                            IncludeInCustomCPA: true,
                            ReportingColumnID: 809247,
                            ROASConfig: &components.CustomROASConfig{
                                IncludeInCustomROAS: false,
                                CustomROASWeight: nil,
                                CustomROASClickWeight: nil,
                                CustomROASViewthroughWeight: ttdworkflows.Float64(6784.9),
                            },
                            Weight: ttdworkflows.Float64(2260.69),
                            CrossDeviceAttributionModelID: ttdworkflows.String("<id>"),
                        },
                    },
                    Name: ttdworkflows.String("<value>"),
                    PrimaryChannel: components.CampaignChannelTypeNone.ToPointer(),
                    PrimaryGoal: &components.CampaignWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflows.Bool(true),
                        MaximizeLtvIncrementalReach: ttdworkflows.Bool(false),
                        CpcInAdvertiserCurrency: ttdworkflows.Float64(3354.68),
                        CtrInPercent: ttdworkflows.Float64(7716.49),
                        NielsenOTPInPercent: nil,
                        CpaInAdvertiserCurrency: ttdworkflows.Float64(381.7),
                        ReturnOnAdSpendPercent: ttdworkflows.Float64(8461.44),
                        VcrInPercent: ttdworkflows.Float64(4170.61),
                        ViewabilityInPercent: ttdworkflows.Float64(5364.85),
                        VcpmInAdvertiserCurrency: ttdworkflows.Float64(1107.08),
                        CpcvInAdvertiserCurrency: nil,
                        MiaozhenOTPInPercent: ttdworkflows.Float64(4584.96),
                    },
                    StartDateInUtc: types.MustNewTimeFromString("2023-01-13T23:06:05.083Z"),
                },
                AdvancedInput: &components.CampaignWorkflowAdvancedInput{
                    Flights: []components.CampaignWorkflowFlightInput{
                        components.CampaignWorkflowFlightInput{
                            StartDateInclusiveUTC: types.MustTimeFromString("2023-08-14T13:47:31.198Z"),
                            EndDateExclusiveUTC: types.MustNewTimeFromString("2024-07-07T14:46:57.378Z"),
                            BudgetInAdvertiserCurrency: 1874.95,
                            BudgetInImpressions: ttdworkflows.Int64(207094),
                            DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(7255.71),
                            DailyTargetInImpressions: ttdworkflows.Int64(760981),
                        },
                    },
                    PurchaseOrderNumber: ttdworkflows.String("<value>"),
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Bool(true),
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

<!-- UsageSnippet language="go" operationID="archiveCampaigns" method="post" path="/campaign/archive" -->
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

    res, err := s.Campaigns.Archive(ctx, ttdworkflows.Bool(false), []string{
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

<!-- UsageSnippet language="go" operationID="getCampaignVersion" method="get" path="/campaign/{id}/version" -->
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