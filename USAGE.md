<!-- Start SDK Example Usage [usage] -->
```go
package main

import (
	"context"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := ttdworkflows.New(
		ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
	)

	res, err := s.AdGroups.Create(ctx, &components.AdGroupCreateWorkflowInputWithValidation{
		PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
			IsEnabled:   ttdworkflows.Pointer(false),
			Description: ttdworkflows.Pointer("twine from gosh poor safely editor astride vice lost and"),
			Budget: &components.AdGroupWorkflowBudgetInput{
				AllocationType:                  components.AllocationTypeMaximum.ToPointer(),
				BudgetInAdvertiserCurrency:      ttdworkflows.Pointer[float64](3786.02),
				BudgetInImpressions:             ttdworkflows.Pointer[int64](783190),
				DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](9747.02),
				DailyTargetInImpressions:        ttdworkflows.Pointer[int64](985999),
			},
			BaseBidCPMInAdvertiserCurrency: ttdworkflows.Pointer[float64](3785.04),
			MaxBidCPMInAdvertiserCurrency:  ttdworkflows.Pointer[float64](7447.3),
			AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
				AudienceID:                           ttdworkflows.Pointer("<id>"),
				AudienceAcceleratorExclusionsEnabled: ttdworkflows.Pointer(true),
				AudienceBoosterEnabled:               ttdworkflows.Pointer(true),
				AudienceExcluderEnabled:              ttdworkflows.Pointer(true),
				AudiencePredictorEnabled:             ttdworkflows.Pointer(false),
				CrossDeviceVendorListForAudience: []int{
					107263,
				},
				RecencyExclusionWindowInMinutes: ttdworkflows.Pointer[int](90062),
				TargetTrackableUsersEnabled:     ttdworkflows.Pointer(true),
				UseMcIDAsPrimary:                ttdworkflows.Pointer(true),
			},
			RoiGoal: &components.AdGroupWorkflowROIGoalInput{
				MaximizeReach:               ttdworkflows.Pointer(true),
				MaximizeLtvIncrementalReach: ttdworkflows.Pointer(false),
				CpcInAdvertiserCurrency:     ttdworkflows.Pointer[float64](2280.31),
				CtrInPercent:                nil,
				NielsenOTPInPercent:         ttdworkflows.Pointer[float64](5175.21),
				CpaInAdvertiserCurrency:     ttdworkflows.Pointer[float64](2544.37),
				ReturnOnAdSpendPercent:      ttdworkflows.Pointer[float64](8201.47),
				VcrInPercent:                ttdworkflows.Pointer[float64](4846.08),
				ViewabilityInPercent:        nil,
				VcpmInAdvertiserCurrency:    ttdworkflows.Pointer[float64](4649.53),
				CpcvInAdvertiserCurrency:    ttdworkflows.Pointer[float64](313.95),
				MiaozhenOTPInPercent:        ttdworkflows.Pointer[float64](4704.1),
			},
			CreativeIds: nil,
			AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
				components.AdGroupWorkflowAssociateBidListInput{
					BidListID:             "<id>",
					IsEnabled:             ttdworkflows.Pointer(false),
					IsDefaultForDimension: ttdworkflows.Pointer(true),
				},
			},
			Name:                                    ttdworkflows.Pointer("<value>"),
			Channel:                                 components.AdGroupChannelDisplay,
			FunnelLocation:                          components.AdGroupFunnelLocationConsideration,
			ProgrammaticGuaranteedPrivateContractID: ttdworkflows.Pointer("<id>"),
		},
		CampaignID: ttdworkflows.Pointer("<id>"),
		AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
			KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
				AreFutureKoaFeaturesEnabled: ttdworkflows.Pointer(false),
				PredictiveClearingEnabled:   ttdworkflows.Pointer(false),
			},
			ComscoreSettings: &components.AdGroupWorkflowComscoreSettingsInput{
				IsEnabled:    false,
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
			IsUseClicksAsConversionsEnabled:  ttdworkflows.Pointer(false),
			IsUseSecondaryConversionsEnabled: ttdworkflows.Pointer(false),
			NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
				EnhancedReportingOption: components.EnhancedNielsenReportingOptionsInputSite.ToPointer(),
				Gender:                  components.TargetingGenderInputMale,
				StartAge:                components.TargetingStartAgeInputTwentyFive,
				EndAge:                  components.TargetingEndAgeInputSeventeen,
				Countries: []string{
					"<value 1>",
					"<value 2>",
					"<value 3>",
				},
			},
			NewFrequencyConfigs: []components.AdGroupWorkflowNewFrequencyConfigInput{
				components.AdGroupWorkflowNewFrequencyConfigInput{
					CounterName:            nil,
					FrequencyCap:           ttdworkflows.Pointer[int](375286),
					FrequencyGoal:          ttdworkflows.Pointer[int](534735),
					ResetIntervalInMinutes: ttdworkflows.Pointer[int](788122),
				},
			},
			Flights: []components.AdGroupWorkflowFlightInput{
				components.AdGroupWorkflowFlightInput{
					AllocationType:                  components.AllocationTypeMaximum.ToPointer(),
					BudgetInAdvertiserCurrency:      ttdworkflows.Pointer[float64](4070.96),
					BudgetInImpressions:             ttdworkflows.Pointer[int64](901477),
					DailyTargetInAdvertiserCurrency: ttdworkflows.Pointer[float64](5847.35),
					DailyTargetInImpressions:        ttdworkflows.Pointer[int64](257517),
					CampaignFlightID:                874887,
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
<!-- End SDK Example Usage [usage] -->