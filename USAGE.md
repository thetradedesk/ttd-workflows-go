<!-- Start SDK Example Usage [usage] -->
```go
package main

import (
	"context"
	"log"
	"os"
	ttdworkflows "ttd-workflows"
	"ttd-workflows/models/components"
)

func main() {
	ctx := context.Background()

	s := ttdworkflows.New(
		ttdworkflows.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
	)

	res, err := s.AdGroups.Create(ctx, &components.AdGroupCreateWorkflowInputWithValidation{
		PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
			IsEnabled:   ttdworkflows.Bool(false),
			Description: ttdworkflows.String("twine from gosh poor safely editor astride vice lost and"),
			Budget: &components.AdGroupWorkflowBudgetInput{
				AllocationType:                  components.AllocationTypeMaximum.ToPointer(),
				BudgetInAdvertiserCurrency:      ttdworkflows.Float64(3786.02),
				BudgetInImpressions:             ttdworkflows.Int64(783190),
				DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(9747.02),
				DailyTargetInImpressions:        ttdworkflows.Int64(985999),
			},
			BaseBidCPMInAdvertiserCurrency: ttdworkflows.Float64(3785.04),
			MaxBidCPMInAdvertiserCurrency:  ttdworkflows.Float64(7447.3),
			AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
				AudienceID:                           ttdworkflows.String("<id>"),
				AudienceAcceleratorExclusionsEnabled: ttdworkflows.Bool(true),
				AudienceBoosterEnabled:               ttdworkflows.Bool(true),
				AudienceExcluderEnabled:              ttdworkflows.Bool(true),
				AudiencePredictorEnabled:             ttdworkflows.Bool(false),
				CrossDeviceVendorListForAudience: []int{
					107263,
				},
				RecencyExclusionWindowInMinutes: ttdworkflows.Int(90062),
				TargetTrackableUsersEnabled:     ttdworkflows.Bool(true),
				UseMcIDAsPrimary:                ttdworkflows.Bool(true),
			},
			RoiGoal: &components.AdGroupWorkflowROIGoalInput{
				MaximizeReach:               ttdworkflows.Bool(true),
				MaximizeLtvIncrementalReach: ttdworkflows.Bool(false),
				CpcInAdvertiserCurrency:     ttdworkflows.Float64(2280.31),
				CtrInPercent:                nil,
				NielsenOTPInPercent:         ttdworkflows.Float64(5175.21),
				CpaInAdvertiserCurrency:     ttdworkflows.Float64(2544.37),
				ReturnOnAdSpendPercent:      ttdworkflows.Float64(8201.47),
				VcrInPercent:                ttdworkflows.Float64(4846.08),
				ViewabilityInPercent:        nil,
				VcpmInAdvertiserCurrency:    ttdworkflows.Float64(4649.53),
				CpcvInAdvertiserCurrency:    ttdworkflows.Float64(313.95),
				MiaozhenOTPInPercent:        ttdworkflows.Float64(4704.1),
			},
			CreativeIds: nil,
			AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
				components.AdGroupWorkflowAssociateBidListInput{
					BidListID:             "<id>",
					IsEnabled:             ttdworkflows.Bool(false),
					IsDefaultForDimension: ttdworkflows.Bool(true),
				},
			},
			Name:                                    ttdworkflows.String("<value>"),
			Channel:                                 components.AdGroupChannelDisplay,
			FunnelLocation:                          components.AdGroupFunnelLocationConsideration,
			ProgrammaticGuaranteedPrivateContractID: ttdworkflows.String("<id>"),
		},
		CampaignID: ttdworkflows.String("<id>"),
		AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
			KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
				AreFutureKoaFeaturesEnabled: ttdworkflows.Bool(false),
				PredictiveClearingEnabled:   ttdworkflows.Bool(false),
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
				AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflows.Bool(true),
			},
			DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
				[]components.DimensionalBiddingDimensions{},
				[]components.DimensionalBiddingDimensions{},
			},
			IsUseClicksAsConversionsEnabled:  ttdworkflows.Bool(false),
			IsUseSecondaryConversionsEnabled: ttdworkflows.Bool(false),
			NielsenTrackingAttributes: &components.AdGroupWorkflowNielsenTrackingAttributesInput{
				EnhancedReportingOption: components.EnhancedNielsenReportingOptionsSite.ToPointer(),
				Gender:                  components.TargetingGenderMale,
				StartAge:                components.TargetingStartAgeTwentyFive,
				EndAge:                  components.TargetingEndAgeSeventeen,
				Countries: []string{
					"<value 1>",
					"<value 2>",
					"<value 3>",
				},
			},
			NewFrequencyConfigs: []components.AdGroupWorkflowNewFrequencyConfigInput{
				components.AdGroupWorkflowNewFrequencyConfigInput{
					CounterName:            nil,
					FrequencyCap:           ttdworkflows.Int(375286),
					FrequencyGoal:          ttdworkflows.Int(534735),
					ResetIntervalInMinutes: ttdworkflows.Int(788122),
				},
			},
			Flights: []components.AdGroupWorkflowFlightInput{
				components.AdGroupWorkflowFlightInput{
					AllocationType:                  components.AllocationTypeMaximum.ToPointer(),
					BudgetInAdvertiserCurrency:      ttdworkflows.Float64(4070.96),
					BudgetInImpressions:             ttdworkflows.Int64(901477),
					DailyTargetInAdvertiserCurrency: ttdworkflows.Float64(5847.35),
					DailyTargetInImpressions:        ttdworkflows.Int64(257517),
					CampaignFlightID:                874887,
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
<!-- End SDK Example Usage [usage] -->