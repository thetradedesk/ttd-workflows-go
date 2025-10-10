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
            Description: ttdworkflows.Pointer("woot furthermore mentor"),
            CampaignGroupID: ttdworkflows.Pointer[int64](86586),
            TimeZone: ttdworkflows.Pointer("Europe/Ulyanovsk"),
            CustomCPAClickWeight: ttdworkflows.Pointer[float64](2561.01),
            CustomCPAViewthroughWeight: ttdworkflows.Pointer[float64](5604.35),
            CustomCPAType: components.CustomCPATypeClickViewthroughWeighting.ToPointer(),
            CustomRoasType: components.CustomROASTypeDisabled.ToPointer(),
            ImpressionsOnlyBudgetingCpm: ttdworkflows.Pointer[float64](1502.33),
            Budget: &components.CampaignWorkflowBudgetInput{
                PacingMode: components.CampaignPacingModePaceAsSoonAsPossible,
                BudgetInAdvertiserCurrency: 6363.35,
                BudgetInImpressions: ttdworkflows.Pointer[int64](836518),
                DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](7814.79),
                DailyTargetInImpressions: ttdworkflows.Pointer[int64](784985),
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
                        CustomROASWeight: ttdworkflows.Pointer[float64](4766.9),
                        CustomROASClickWeight: ttdworkflows.Pointer[float64](3310.24),
                        CustomROASViewthroughWeight: ttdworkflows.Pointer[float64](2919.37),
                    },
                    Weight: ttdworkflows.Pointer[float64](5369.43),
                    CrossDeviceAttributionModelID: ttdworkflows.Pointer("<id>"),
                },
            },
            IsManagedByTTD: nil,
            SecondaryGoal: &components.CampaignWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Pointer(false),
                MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
                CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](4128.35),
                CtrInPercent: ttdworkflows.Pointer[float64](4434.91),
                NielsenOTPInPercent: ttdworkflows.Pointer[float64](7433.37),
                CpaInAdvertiserCurrency: nil,
                ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](2367.04),
                VcrInPercent: ttdworkflows.Pointer[float64](2333.15),
                ViewabilityInPercent: ttdworkflows.Pointer[float64](5018.08),
                VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](6070.6),
                CpcvInAdvertiserCurrency: nil,
                MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](4324.01),
                IqviaAudienceQualityIndex: ttdworkflows.Pointer(true),
                CrossixAudienceQualityIndex: ttdworkflows.Pointer(true),
                IqviaAudienceQualityIndexAndCostPerTarget: ttdworkflows.Pointer(false),
                CrossixCostPerTarget: ttdworkflows.Pointer(true),
            },
            TertiaryGoal: &components.CampaignWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Pointer(false),
                MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
                CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](7814.79),
                CtrInPercent: ttdworkflows.Pointer[float64](7849.85),
                NielsenOTPInPercent: nil,
                CpaInAdvertiserCurrency: nil,
                ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](9519.81),
                VcrInPercent: ttdworkflows.Pointer[float64](6125.66),
                ViewabilityInPercent: ttdworkflows.Pointer[float64](4766.9),
                VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](3310.24),
                CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](2919.37),
                MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](5369.43),
                IqviaAudienceQualityIndex: ttdworkflows.Pointer(false),
                CrossixAudienceQualityIndex: ttdworkflows.Pointer(false),
                IqviaAudienceQualityIndexAndCostPerTarget: nil,
                CrossixCostPerTarget: ttdworkflows.Pointer(false),
            },
            AdvertiserID: "<id>",
            Name: "<value>",
            PrimaryChannel: components.CampaignChannelTypeDooh,
            PrimaryGoal: components.CampaignWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Pointer(false),
                MaximizeLtvIncrementalReach: nil,
                CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](6678.34),
                CtrInPercent: ttdworkflows.Pointer[float64](5357.4),
                NielsenOTPInPercent: ttdworkflows.Pointer[float64](2741.6),
                CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](4220.63),
                ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](8572.83),
                VcrInPercent: ttdworkflows.Pointer[float64](8294.92),
                ViewabilityInPercent: ttdworkflows.Pointer[float64](8592.21),
                VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](8388.8),
                CpcvInAdvertiserCurrency: nil,
                MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](3033.14),
                IqviaAudienceQualityIndex: ttdworkflows.Pointer(false),
                CrossixAudienceQualityIndex: ttdworkflows.Pointer(true),
                IqviaAudienceQualityIndexAndCostPerTarget: ttdworkflows.Pointer(true),
                CrossixCostPerTarget: ttdworkflows.Pointer(false),
            },
            StartDateInUtc: nil,
            CampaignIncrementalReachSetting: &components.CampaignCreateWorkflowIncrementalReachCampaignSetting{
                ISpotReachSetting: &components.IncrementalReachBrandInput{
                    ID: ttdworkflows.Pointer[int](787894),
                    Name: ttdworkflows.Pointer("<value>"),
                    IsActive: ttdworkflows.Pointer(false),
                },
                RealyticsReachSetting: &components.RealyticsReachSettingInput{
                    ID: ttdworkflows.Pointer[int](859221),
                    Name: ttdworkflows.Pointer("<value>"),
                    IsActive: ttdworkflows.Pointer(false),
                    Products: nil,
                    RealyticsEntertainmentInput: components.RealyticsEntertainmentTypeTvs.ToPointer(),
                },
                TvSquaredReachSetting: &components.IncrementalReachBrandInput{
                    ID: ttdworkflows.Pointer[int](303314),
                    Name: nil,
                    IsActive: ttdworkflows.Pointer(false),
                },
                SambaAuReachSetting: &components.IncrementalReachBrandInput{
                    ID: ttdworkflows.Pointer[int](505888),
                    Name: ttdworkflows.Pointer("<value>"),
                    IsActive: ttdworkflows.Pointer(true),
                },
            },
        },
        AdvancedInput: &components.CampaignCreateWorkflowAdvancedInput{
            Flights: []components.CampaignWorkflowFlightInput{
                components.CampaignWorkflowFlightInput{
                    StartDateInclusiveUTC: types.MustTimeFromString("2024-07-08T10:52:56.944Z"),
                    EndDateExclusiveUTC: types.MustNewTimeFromString("2023-05-12T16:41:56.386Z"),
                    BudgetInAdvertiserCurrency: 5904.11,
                    BudgetInImpressions: nil,
                    DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](6112.24),
                    DailyTargetInImpressions: ttdworkflows.Pointer[int64](333131),
                },
            },
            PurchaseOrderNumber: nil,
            IncludeDefaultsFromAdvertiser: ttdworkflows.Pointer(false),
            PassThroughFeeCard: &components.CampaignCreateWorkflowPassThroughFeeCardInput{
                StartDateUtc: types.MustNewTimeFromString("2023-03-18T04:39:08.387Z"),
                PassThroughFees: []components.CampaignCreatePassThroughFeesInput{
                    components.CampaignCreatePassThroughFeesInput{
                        Type: components.PassThroughFeeTypeFeeCpm.ToPointer(),
                        Description: ttdworkflows.Pointer("fairly gah mortally freight since"),
                        Amount: ttdworkflows.Pointer[float64](2122.11),
                    },
                },
            },
        },
        AdGroups: []components.CampaignCreateWorkflowAdGroupInput{
            components.CampaignCreateWorkflowAdGroupInput{
                PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
                    IsEnabled: ttdworkflows.Pointer(false),
                    Description: ttdworkflows.Pointer("quash lightly rot bashfully slope"),
                    Budget: &components.AdGroupWorkflowBudgetInput{
                        AllocationType: components.AllocationTypeMinimum.ToPointer(),
                        BudgetInAdvertiserCurrency: ttdworkflows.Pointer[float64](4043.98),
                        BudgetInImpressions: ttdworkflows.Pointer[int64](907414),
                        DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](49.95),
                        DailyTargetInImpressions: ttdworkflows.Pointer[int64](62363),
                    },
                    BaseBidCPMInAdvertiserCurrency: ttdworkflows.Pointer[float64](1136.89),
                    MaxBidCPMInAdvertiserCurrency: ttdworkflows.Pointer[float64](6950.27),
                    AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                        AudienceID: ttdworkflows.Pointer("<id>"),
                        AudienceAcceleratorExclusionsEnabled: ttdworkflows.Pointer(false),
                        AudienceBoosterEnabled: ttdworkflows.Pointer(true),
                        AudienceExcluderEnabled: ttdworkflows.Pointer(false),
                        AudiencePredictorEnabled: ttdworkflows.Pointer(true),
                        CrossDeviceVendorListForAudience: []int{
                            458524,
                            284141,
                        },
                        RecencyExclusionWindowInMinutes: ttdworkflows.Pointer[int](982426),
                        TargetTrackableUsersEnabled: ttdworkflows.Pointer(false),
                        UseMcIDAsPrimary: ttdworkflows.Pointer(true),
                    },
                    RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                        MaximizeReach: nil,
                        MaximizeLtvIncrementalReach: ttdworkflows.Pointer(true),
                        CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](8782.74),
                        CtrInPercent: nil,
                        NielsenOTPInPercent: ttdworkflows.Pointer[float64](7930.85),
                        CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](4606.89),
                        ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](2522.83),
                        VcrInPercent: ttdworkflows.Pointer[float64](5828.49),
                        ViewabilityInPercent: ttdworkflows.Pointer[float64](6824.44),
                        VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](7123.95),
                        CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](6233.72),
                        MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](8437.22),
                    },
                    CreativeIds: []string{
                        "<value 1>",
                    },
                    AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                        components.AdGroupWorkflowAssociateBidListInput{
                            BidListID: "<id>",
                            IsEnabled: ttdworkflows.Pointer(true),
                            IsDefaultForDimension: ttdworkflows.Pointer(false),
                        },
                    },
                    Name: ttdworkflows.Pointer("<value>"),
                    Channel: components.AdGroupChannelNativeVideo,
                    FunnelLocation: components.AdGroupFunnelLocationNone,
                    ProgrammaticGuaranteedPrivateContractID: ttdworkflows.Pointer("<id>"),
                },
                AdvancedInput: &components.CampaignCreateWorkflowAdGroupAdvancedInput{
                    KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                        AreFutureKoaFeaturesEnabled: ttdworkflows.Pointer(true),
                        PredictiveClearingEnabled: ttdworkflows.Pointer(true),
                    },
                    ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                        IsEnabled: false,
                        PopulationID: ttdworkflows.Pointer[int](523753),
                        DemographicMemberIds: nil,
                        MobileDemographicMemberIds: nil,
                    },
                    ContractTargeting: &components.AdGroupWorkflowContractTargetingInput{
                        AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflows.Pointer(true),
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
                    IsUseSecondaryConversionsEnabled: ttdworkflows.Pointer(true),
                    NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
                        EnhancedReportingOption: components.EnhancedNielsenReportingOptionsInputSite.ToPointer(),
                        Gender: components.TargetingGenderInputFemale,
                        StartAge: components.TargetingStartAgeInputThirtyFive,
                        EndAge: components.TargetingEndAgeInputFortyNine,
                        Countries: []string{},
                    },
                    NewFrequencyConfigs: []components.AdGroupWorkflowNewFrequencyConfigInput{
                        components.AdGroupWorkflowNewFrequencyConfigInput{
                            CounterName: ttdworkflows.Pointer("<value>"),
                            FrequencyCap: ttdworkflows.Pointer[int](391231),
                            FrequencyGoal: ttdworkflows.Pointer[int](499235),
                            ResetIntervalInMinutes: ttdworkflows.Pointer[int](587736),
                        },
                    },
                    Flights: []components.CampaignCreateWorkflowAdGroupFlightInput{
                        components.CampaignCreateWorkflowAdGroupFlightInput{
                            AllocationType: components.AllocationTypeFixed.ToPointer(),
                            BudgetInAdvertiserCurrency: ttdworkflows.Pointer[float64](5340.32),
                            BudgetInImpressions: ttdworkflows.Pointer[int64](492382),
                            DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](5622.5),
                            DailyTargetInImpressions: ttdworkflows.Pointer[int64](398919),
                        },
                    },
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Pointer(false),
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
        ID: ttdworkflows.Pointer("<id>"),
        PrimaryInput: &components.CampaignUpdateWorkflowPrimaryInput{
            Description: ttdworkflows.Pointer("yahoo whether frail but into form sway neck notwithstanding"),
            CampaignGroupID: ttdworkflows.Pointer[int64](760468),
            TimeZone: ttdworkflows.Pointer("Asia/Amman"),
            CustomCPAClickWeight: ttdworkflows.Pointer[float64](1380.93),
            CustomCPAViewthroughWeight: ttdworkflows.Pointer[float64](3991.98),
            CustomCPAType: components.CustomCPATypeClickViewthroughWeighting.ToPointer(),
            CustomRoasType: components.CustomROASTypeDisabled.ToPointer(),
            ImpressionsOnlyBudgetingCpm: ttdworkflows.Pointer[float64](126.57),
            Budget: &components.CampaignWorkflowBudgetInput{
                PacingMode: components.CampaignPacingModePaceAsSoonAsPossible,
                BudgetInAdvertiserCurrency: 6974.82,
                BudgetInImpressions: ttdworkflows.Pointer[int64](834352),
                DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](8583.49),
                DailyTargetInImpressions: ttdworkflows.Pointer[int64](746941),
            },
            EndDateInUtc: types.MustNewTimeFromString("2024-07-09T17:14:23.542Z"),
            SeedID: ttdworkflows.Pointer("<id>"),
            CampaignConversionReportingColumns: []components.CampaignWorkflowCampaignConversionReportingColumnInput{
                components.CampaignWorkflowCampaignConversionReportingColumnInput{
                    TrackingTagID: "<id>",
                    IncludeInCustomCPA: false,
                    ReportingColumnID: 716444,
                    ROASConfig: &components.CustomROASConfig{
                        IncludeInCustomROAS: true,
                        CustomROASWeight: ttdworkflows.Pointer[float64](8307.9),
                        CustomROASClickWeight: ttdworkflows.Pointer[float64](129.65),
                        CustomROASViewthroughWeight: ttdworkflows.Pointer[float64](2890.82),
                    },
                    Weight: ttdworkflows.Pointer[float64](5187.48),
                    CrossDeviceAttributionModelID: nil,
                },
            },
            IsManagedByTTD: ttdworkflows.Pointer(false),
            SecondaryGoal: &components.CampaignWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Pointer(true),
                MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
                CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](1165.14),
                CtrInPercent: ttdworkflows.Pointer[float64](5157.73),
                NielsenOTPInPercent: ttdworkflows.Pointer[float64](3855.93),
                CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](5164.28),
                ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](8554.35),
                VcrInPercent: ttdworkflows.Pointer[float64](9569.97),
                ViewabilityInPercent: ttdworkflows.Pointer[float64](9650.33),
                VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](5268.69),
                CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](7216.52),
                MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](6966.26),
                IqviaAudienceQualityIndex: ttdworkflows.Pointer(true),
                CrossixAudienceQualityIndex: ttdworkflows.Pointer(true),
                IqviaAudienceQualityIndexAndCostPerTarget: ttdworkflows.Pointer(true),
                CrossixCostPerTarget: ttdworkflows.Pointer(true),
            },
            TertiaryGoal: &components.CampaignWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Pointer(true),
                MaximizeLtvIncrementalReach: ttdworkflows.Pointer(true),
                CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](5149.5),
                CtrInPercent: ttdworkflows.Pointer[float64](5602.97),
                NielsenOTPInPercent: ttdworkflows.Pointer[float64](3514.56),
                CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](1.97),
                ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](3177.79),
                VcrInPercent: ttdworkflows.Pointer[float64](5564.63),
                ViewabilityInPercent: ttdworkflows.Pointer[float64](472.11),
                VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](4614.14),
                CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](8553.51),
                MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](5511.72),
                IqviaAudienceQualityIndex: ttdworkflows.Pointer(false),
                CrossixAudienceQualityIndex: ttdworkflows.Pointer(false),
                IqviaAudienceQualityIndexAndCostPerTarget: nil,
                CrossixCostPerTarget: ttdworkflows.Pointer(false),
            },
            Name: ttdworkflows.Pointer("<value>"),
            PrimaryChannel: components.CampaignChannelTypeDisplay.ToPointer(),
            PrimaryGoal: &components.CampaignWorkflowROIGoalInput{
                MaximizeReach: ttdworkflows.Pointer(false),
                MaximizeLtvIncrementalReach: ttdworkflows.Pointer(true),
                CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](8835.54),
                CtrInPercent: ttdworkflows.Pointer[float64](4975.78),
                NielsenOTPInPercent: ttdworkflows.Pointer[float64](6033.78),
                CpaInAdvertiserCurrency: nil,
                ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](5696.08),
                VcrInPercent: ttdworkflows.Pointer[float64](8315.31),
                ViewabilityInPercent: ttdworkflows.Pointer[float64](1059.68),
                VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](4588.07),
                CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](2202.71),
                MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](2682.12),
                IqviaAudienceQualityIndex: ttdworkflows.Pointer(false),
                CrossixAudienceQualityIndex: ttdworkflows.Pointer(true),
                IqviaAudienceQualityIndexAndCostPerTarget: ttdworkflows.Pointer(true),
                CrossixCostPerTarget: ttdworkflows.Pointer(true),
            },
            StartDateInUtc: types.MustNewTimeFromString("2024-02-29T10:31:50.069Z"),
        },
        AdvancedInput: &components.CampaignUpdateWorkflowAdvancedInput{
            Flights: []components.CampaignWorkflowFlightInput{
                components.CampaignWorkflowFlightInput{
                    StartDateInclusiveUTC: types.MustTimeFromString("2025-11-09T04:11:39.432Z"),
                    EndDateExclusiveUTC: types.MustNewTimeFromString("2025-09-10T20:38:51.701Z"),
                    BudgetInAdvertiserCurrency: 6534.57,
                    BudgetInImpressions: ttdworkflows.Pointer[int64](865481),
                    DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](1033.72),
                    DailyTargetInImpressions: nil,
                },
            },
            PurchaseOrderNumber: ttdworkflows.Pointer("<value>"),
        },
        ValidateInputOnly: ttdworkflows.Pointer(true),
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
                    CampaignGroupID: ttdworkflows.Pointer[int64](657704),
                    TimeZone: ttdworkflows.Pointer("America/North_Dakota/Center"),
                    CustomCPAClickWeight: ttdworkflows.Pointer[float64](9662.9),
                    CustomCPAViewthroughWeight: ttdworkflows.Pointer[float64](3558.78),
                    CustomCPAType: components.CustomCPATypeClickViewthroughWeighting.ToPointer(),
                    CustomRoasType: components.CustomROASTypeCompositeWeighting.ToPointer(),
                    ImpressionsOnlyBudgetingCpm: ttdworkflows.Pointer[float64](4427.56),
                    Budget: &components.CampaignWorkflowBudgetInput{
                        PacingMode: components.CampaignPacingModePaceAhead,
                        BudgetInAdvertiserCurrency: 5501.96,
                        BudgetInImpressions: ttdworkflows.Pointer[int64](629784),
                        DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](2524.41),
                        DailyTargetInImpressions: ttdworkflows.Pointer[int64](726807),
                    },
                    EndDateInUtc: types.MustNewTimeFromString("2023-12-21T01:12:20.772Z"),
                    SeedID: ttdworkflows.Pointer("<id>"),
                    CampaignConversionReportingColumns: []components.CampaignWorkflowCampaignConversionReportingColumnInput{
                        components.CampaignWorkflowCampaignConversionReportingColumnInput{
                            TrackingTagID: "<id>",
                            IncludeInCustomCPA: false,
                            ReportingColumnID: 356532,
                            ROASConfig: &components.CustomROASConfig{
                                IncludeInCustomROAS: false,
                                CustomROASWeight: ttdworkflows.Pointer[float64](1483.03),
                                CustomROASClickWeight: ttdworkflows.Pointer[float64](5286.76),
                                CustomROASViewthroughWeight: ttdworkflows.Pointer[float64](8906.82),
                            },
                            Weight: nil,
                            CrossDeviceAttributionModelID: ttdworkflows.Pointer("<id>"),
                        },
                    },
                    IsManagedByTTD: ttdworkflows.Pointer(true),
                    SecondaryGoal: &components.CampaignWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflows.Pointer(true),
                        MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
                        CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](3558.78),
                        CtrInPercent: ttdworkflows.Pointer[float64](2407.01),
                        NielsenOTPInPercent: ttdworkflows.Pointer[float64](2349.25),
                        CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](7778.32),
                        ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](6752.02),
                        VcrInPercent: ttdworkflows.Pointer[float64](5019.36),
                        ViewabilityInPercent: ttdworkflows.Pointer[float64](5781.75),
                        VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](1696.34),
                        CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](5609.2),
                        MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](5842.09),
                        IqviaAudienceQualityIndex: ttdworkflows.Pointer(true),
                        CrossixAudienceQualityIndex: ttdworkflows.Pointer(false),
                        IqviaAudienceQualityIndexAndCostPerTarget: ttdworkflows.Pointer(false),
                        CrossixCostPerTarget: nil,
                    },
                    TertiaryGoal: &components.CampaignWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflows.Pointer(false),
                        MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
                        CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](6123.61),
                        CtrInPercent: ttdworkflows.Pointer[float64](25.32),
                        NielsenOTPInPercent: ttdworkflows.Pointer[float64](4889.32),
                        CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](5258.8),
                        ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](2553.01),
                        VcrInPercent: ttdworkflows.Pointer[float64](1142.91),
                        ViewabilityInPercent: ttdworkflows.Pointer[float64](1152.77),
                        VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](6711.38),
                        CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](4528.37),
                        MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](9833.69),
                        IqviaAudienceQualityIndex: ttdworkflows.Pointer(true),
                        CrossixAudienceQualityIndex: ttdworkflows.Pointer(false),
                        IqviaAudienceQualityIndexAndCostPerTarget: ttdworkflows.Pointer(false),
                        CrossixCostPerTarget: ttdworkflows.Pointer(true),
                    },
                    AdvertiserID: "<id>",
                    Name: "<value>",
                    PrimaryChannel: components.CampaignChannelTypeNativeVideo,
                    PrimaryGoal: components.CampaignWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflows.Pointer(false),
                        MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
                        CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](25.32),
                        CtrInPercent: ttdworkflows.Pointer[float64](4889.32),
                        NielsenOTPInPercent: ttdworkflows.Pointer[float64](5258.8),
                        CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](2553.01),
                        ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](1142.91),
                        VcrInPercent: ttdworkflows.Pointer[float64](1152.77),
                        ViewabilityInPercent: ttdworkflows.Pointer[float64](6711.38),
                        VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](4528.37),
                        CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](9833.69),
                        MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](1951.58),
                        IqviaAudienceQualityIndex: ttdworkflows.Pointer(true),
                        CrossixAudienceQualityIndex: nil,
                        IqviaAudienceQualityIndexAndCostPerTarget: ttdworkflows.Pointer(false),
                        CrossixCostPerTarget: ttdworkflows.Pointer(true),
                    },
                    StartDateInUtc: types.MustNewTimeFromString("2025-09-26T21:06:42.946Z"),
                    CampaignIncrementalReachSetting: &components.CampaignCreateWorkflowIncrementalReachCampaignSetting{
                        ISpotReachSetting: &components.IncrementalReachBrandInput{
                            ID: ttdworkflows.Pointer[int](178346),
                            Name: ttdworkflows.Pointer("<value>"),
                            IsActive: ttdworkflows.Pointer(true),
                        },
                        RealyticsReachSetting: &components.RealyticsReachSettingInput{
                            ID: ttdworkflows.Pointer[int](268786),
                            Name: ttdworkflows.Pointer("<value>"),
                            IsActive: ttdworkflows.Pointer(false),
                            Products: []components.IncrementalReachProductInput{
                                components.IncrementalReachProductInput{
                                    ID: ttdworkflows.Pointer[int](106975),
                                    Name: ttdworkflows.Pointer("<value>"),
                                },
                            },
                            RealyticsEntertainmentInput: components.RealyticsEntertainmentTypeTvs.ToPointer(),
                        },
                        TvSquaredReachSetting: &components.IncrementalReachBrandInput{
                            ID: ttdworkflows.Pointer[int](772731),
                            Name: ttdworkflows.Pointer("<value>"),
                            IsActive: ttdworkflows.Pointer(false),
                        },
                        SambaAuReachSetting: &components.IncrementalReachBrandInput{
                            ID: ttdworkflows.Pointer[int](403863),
                            Name: nil,
                            IsActive: ttdworkflows.Pointer(true),
                        },
                    },
                },
                AdvancedInput: &components.CampaignCreateWorkflowAdvancedInput{
                    Flights: []components.CampaignWorkflowFlightInput{
                        components.CampaignWorkflowFlightInput{
                            StartDateInclusiveUTC: types.MustTimeFromString("2024-09-20T06:04:19.345Z"),
                            EndDateExclusiveUTC: types.MustNewTimeFromString("2024-01-18T07:43:56.299Z"),
                            BudgetInAdvertiserCurrency: 8219.9,
                            BudgetInImpressions: ttdworkflows.Pointer[int64](76925),
                            DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](9309.03),
                            DailyTargetInImpressions: ttdworkflows.Pointer[int64](152838),
                        },
                    },
                    PurchaseOrderNumber: ttdworkflows.Pointer("<value>"),
                    IncludeDefaultsFromAdvertiser: ttdworkflows.Pointer(false),
                    PassThroughFeeCard: &components.CampaignCreateWorkflowPassThroughFeeCardInput{
                        StartDateUtc: types.MustNewTimeFromString("2024-07-24T11:58:59.190Z"),
                        PassThroughFees: []components.CampaignCreatePassThroughFeesInput{
                            components.CampaignCreatePassThroughFeesInput{
                                Type: components.PassThroughFeeTypeDataCostPercentage.ToPointer(),
                                Description: ttdworkflows.Pointer("sweetly absent fortunately forenenst earnest who solidly wherever step-mother"),
                                Amount: ttdworkflows.Pointer[float64](2888.48),
                            },
                        },
                    },
                },
                AdGroups: []components.CampaignCreateWorkflowAdGroupInput{
                    components.CampaignCreateWorkflowAdGroupInput{
                        PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
                            IsEnabled: ttdworkflows.Pointer(true),
                            Description: ttdworkflows.Pointer("scenario dish gracefully through tame yahoo pension husband as atop"),
                            Budget: &components.AdGroupWorkflowBudgetInput{
                                AllocationType: components.AllocationTypeMaximum.ToPointer(),
                                BudgetInAdvertiserCurrency: ttdworkflows.Pointer[float64](2283.06),
                                BudgetInImpressions: ttdworkflows.Pointer[int64](301691),
                                DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](9268.18),
                                DailyTargetInImpressions: ttdworkflows.Pointer[int64](851470),
                            },
                            BaseBidCPMInAdvertiserCurrency: ttdworkflows.Pointer[float64](694.78),
                            MaxBidCPMInAdvertiserCurrency: ttdworkflows.Pointer[float64](6084.4),
                            AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
                                AudienceID: ttdworkflows.Pointer("<id>"),
                                AudienceAcceleratorExclusionsEnabled: ttdworkflows.Pointer(true),
                                AudienceBoosterEnabled: ttdworkflows.Pointer(false),
                                AudienceExcluderEnabled: ttdworkflows.Pointer(true),
                                AudiencePredictorEnabled: ttdworkflows.Pointer(false),
                                CrossDeviceVendorListForAudience: []int{
                                    497890,
                                    566253,
                                },
                                RecencyExclusionWindowInMinutes: ttdworkflows.Pointer[int](742665),
                                TargetTrackableUsersEnabled: ttdworkflows.Pointer(true),
                                UseMcIDAsPrimary: ttdworkflows.Pointer(true),
                            },
                            RoiGoal: &components.AdGroupWorkflowROIGoalInput{
                                MaximizeReach: ttdworkflows.Pointer(false),
                                MaximizeLtvIncrementalReach: ttdworkflows.Pointer(true),
                                CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](9062.02),
                                CtrInPercent: ttdworkflows.Pointer[float64](7192.99),
                                NielsenOTPInPercent: ttdworkflows.Pointer[float64](2823.22),
                                CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](3140.25),
                                ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](6857.21),
                                VcrInPercent: ttdworkflows.Pointer[float64](2704.73),
                                ViewabilityInPercent: ttdworkflows.Pointer[float64](2247.4),
                                VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](8383.69),
                                CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](4755.8),
                                MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](4575.86),
                            },
                            CreativeIds: []string{
                                "<value 1>",
                                "<value 2>",
                            },
                            AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
                                components.AdGroupWorkflowAssociateBidListInput{
                                    BidListID: "<id>",
                                    IsEnabled: ttdworkflows.Pointer(true),
                                    IsDefaultForDimension: ttdworkflows.Pointer(false),
                                },
                            },
                            Name: ttdworkflows.Pointer("<value>"),
                            Channel: components.AdGroupChannelDisplay,
                            FunnelLocation: components.AdGroupFunnelLocationAwareness,
                            ProgrammaticGuaranteedPrivateContractID: ttdworkflows.Pointer("<id>"),
                        },
                        AdvancedInput: &components.CampaignCreateWorkflowAdGroupAdvancedInput{
                            KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
                                AreFutureKoaFeaturesEnabled: ttdworkflows.Pointer(true),
                                PredictiveClearingEnabled: ttdworkflows.Pointer(false),
                            },
                            ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
                                IsEnabled: false,
                                PopulationID: ttdworkflows.Pointer[int](559587),
                                DemographicMemberIds: []int{
                                    139340,
                                    129935,
                                },
                                MobileDemographicMemberIds: nil,
                            },
                            ContractTargeting: &components.AdGroupWorkflowContractTargetingInput{
                                AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflows.Pointer(true),
                            },
                            DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
                                []components.DimensionalBiddingDimensions{
                                    components.DimensionalBiddingDimensionsHasAudienceReachPercentageTierID,
                                },
                                []components.DimensionalBiddingDimensions{},
                            },
                            IsUseClicksAsConversionsEnabled: ttdworkflows.Pointer(false),
                            IsUseSecondaryConversionsEnabled: ttdworkflows.Pointer(true),
                            NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
                                EnhancedReportingOption: components.EnhancedNielsenReportingOptionsInputNone.ToPointer(),
                                Gender: components.TargetingGenderInputFemale,
                                StartAge: components.TargetingStartAgeInputThirtyFive,
                                EndAge: components.TargetingEndAgeInputTwentyFour,
                                Countries: []string{
                                    "<value 1>",
                                    "<value 2>",
                                },
                            },
                            NewFrequencyConfigs: nil,
                            Flights: []components.CampaignCreateWorkflowAdGroupFlightInput{
                                components.CampaignCreateWorkflowAdGroupFlightInput{
                                    AllocationType: components.AllocationTypeMaximum.ToPointer(),
                                    BudgetInAdvertiserCurrency: ttdworkflows.Pointer[float64](4838.47),
                                    BudgetInImpressions: ttdworkflows.Pointer[int64](420224),
                                    DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](1513.78),
                                    DailyTargetInImpressions: ttdworkflows.Pointer[int64](735500),
                                },
                            },
                        },
                    },
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Pointer(true),
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
                ID: ttdworkflows.Pointer("<id>"),
                PrimaryInput: &components.CampaignUpdateWorkflowPrimaryInput{
                    Description: ttdworkflows.Pointer("hmph energetically yet surprisingly swift knight swear multicolored absent"),
                    CampaignGroupID: ttdworkflows.Pointer[int64](645576),
                    TimeZone: ttdworkflows.Pointer("America/Argentina/San_Juan"),
                    CustomCPAClickWeight: nil,
                    CustomCPAViewthroughWeight: ttdworkflows.Pointer[float64](8361.84),
                    CustomCPAType: components.CustomCPATypePixelWeighting.ToPointer(),
                    CustomRoasType: components.CustomROASTypeClickViewthroughWeighting.ToPointer(),
                    ImpressionsOnlyBudgetingCpm: ttdworkflows.Pointer[float64](2706.4),
                    Budget: &components.CampaignWorkflowBudgetInput{
                        PacingMode: components.CampaignPacingModePaceAsSoonAsPossible,
                        BudgetInAdvertiserCurrency: 2564.89,
                        BudgetInImpressions: ttdworkflows.Pointer[int64](659726),
                        DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](6514.48),
                        DailyTargetInImpressions: ttdworkflows.Pointer[int64](892097),
                    },
                    EndDateInUtc: types.MustNewTimeFromString("2023-11-11T21:39:56.025Z"),
                    SeedID: ttdworkflows.Pointer("<id>"),
                    CampaignConversionReportingColumns: []components.CampaignWorkflowCampaignConversionReportingColumnInput{
                        components.CampaignWorkflowCampaignConversionReportingColumnInput{
                            TrackingTagID: "<id>",
                            IncludeInCustomCPA: true,
                            ReportingColumnID: 809247,
                            ROASConfig: &components.CustomROASConfig{
                                IncludeInCustomROAS: false,
                                CustomROASWeight: nil,
                                CustomROASClickWeight: nil,
                                CustomROASViewthroughWeight: ttdworkflows.Pointer[float64](6784.9),
                            },
                            Weight: ttdworkflows.Pointer[float64](2260.69),
                            CrossDeviceAttributionModelID: ttdworkflows.Pointer("<id>"),
                        },
                    },
                    IsManagedByTTD: ttdworkflows.Pointer(true),
                    SecondaryGoal: &components.CampaignWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflows.Pointer(false),
                        MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
                        CpcInAdvertiserCurrency: nil,
                        CtrInPercent: nil,
                        NielsenOTPInPercent: ttdworkflows.Pointer[float64](5546.51),
                        CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](7735.11),
                        ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](5459.4),
                        VcrInPercent: ttdworkflows.Pointer[float64](7724.91),
                        ViewabilityInPercent: nil,
                        VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](9927),
                        CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](1852.41),
                        MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](2827.93),
                        IqviaAudienceQualityIndex: ttdworkflows.Pointer(false),
                        CrossixAudienceQualityIndex: nil,
                        IqviaAudienceQualityIndexAndCostPerTarget: ttdworkflows.Pointer(false),
                        CrossixCostPerTarget: ttdworkflows.Pointer(true),
                    },
                    TertiaryGoal: &components.CampaignWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflows.Pointer(false),
                        MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
                        CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](7329.7),
                        CtrInPercent: ttdworkflows.Pointer[float64](9103.24),
                        NielsenOTPInPercent: ttdworkflows.Pointer[float64](2359.55),
                        CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](6489.19),
                        ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](8265.87),
                        VcrInPercent: nil,
                        ViewabilityInPercent: ttdworkflows.Pointer[float64](6404.44),
                        VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](1278.49),
                        CpcvInAdvertiserCurrency: ttdworkflows.Pointer[float64](9238.19),
                        MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](8948.48),
                        IqviaAudienceQualityIndex: ttdworkflows.Pointer(true),
                        CrossixAudienceQualityIndex: ttdworkflows.Pointer(false),
                        IqviaAudienceQualityIndexAndCostPerTarget: ttdworkflows.Pointer(false),
                        CrossixCostPerTarget: ttdworkflows.Pointer(true),
                    },
                    Name: ttdworkflows.Pointer("<value>"),
                    PrimaryChannel: components.CampaignChannelTypeNone.ToPointer(),
                    PrimaryGoal: &components.CampaignWorkflowROIGoalInput{
                        MaximizeReach: ttdworkflows.Pointer(true),
                        MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
                        CpcInAdvertiserCurrency: ttdworkflows.Pointer[float64](3354.68),
                        CtrInPercent: ttdworkflows.Pointer[float64](7716.49),
                        NielsenOTPInPercent: nil,
                        CpaInAdvertiserCurrency: ttdworkflows.Pointer[float64](381.7),
                        ReturnOnAdSpendPercent: ttdworkflows.Pointer[float64](8461.44),
                        VcrInPercent: ttdworkflows.Pointer[float64](4170.61),
                        ViewabilityInPercent: ttdworkflows.Pointer[float64](5364.85),
                        VcpmInAdvertiserCurrency: ttdworkflows.Pointer[float64](1107.08),
                        CpcvInAdvertiserCurrency: nil,
                        MiaozhenOTPInPercent: ttdworkflows.Pointer[float64](4584.96),
                        IqviaAudienceQualityIndex: ttdworkflows.Pointer(true),
                        CrossixAudienceQualityIndex: ttdworkflows.Pointer(false),
                        IqviaAudienceQualityIndexAndCostPerTarget: ttdworkflows.Pointer(true),
                        CrossixCostPerTarget: ttdworkflows.Pointer(true),
                    },
                    StartDateInUtc: types.MustNewTimeFromString("2023-01-13T23:06:05.083Z"),
                },
                AdvancedInput: &components.CampaignUpdateWorkflowAdvancedInput{
                    Flights: []components.CampaignWorkflowFlightInput{
                        components.CampaignWorkflowFlightInput{
                            StartDateInclusiveUTC: types.MustTimeFromString("2023-08-14T13:47:31.198Z"),
                            EndDateExclusiveUTC: types.MustNewTimeFromString("2024-07-07T14:46:57.378Z"),
                            BudgetInAdvertiserCurrency: 1874.95,
                            BudgetInImpressions: ttdworkflows.Pointer[int64](207094),
                            DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](7255.71),
                            DailyTargetInImpressions: ttdworkflows.Pointer[int64](760981),
                        },
                    },
                    PurchaseOrderNumber: ttdworkflows.Pointer("<value>"),
                },
            },
        },
        ValidateInputOnly: ttdworkflows.Pointer(true),
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
    if res.CampaignPayload != nil {
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

    res, err := s.Campaigns.Archive(ctx, ttdworkflows.Pointer(false), []string{
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