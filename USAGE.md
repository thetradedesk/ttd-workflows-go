<!-- Start SDK Example Usage [usage] -->
```go
package main

import (
	"context"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := ttdworkflowsgo.New(
		ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
	)

	res, err := s.AdGroups.Create(ctx, &components.AdGroupCreateWorkflowInputWithValidation{
		PrimaryInput: components.AdGroupCreateWorkflowPrimaryInput{
			IsEnabled:   ttdworkflowsgo.Bool(false),
			Description: ttdworkflowsgo.String("twine from gosh poor safely editor astride vice lost and"),
			Budget: &components.AdGroupWorkflowBudgetInput{
				AllocationType:                  components.AllocationTypeMaximum.ToPointer(),
				BudgetInAdvertiserCurrency:      ttdworkflowsgo.Float64(3786.02),
				BudgetInImpressions:             ttdworkflowsgo.Int64(783190),
				DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(9747.02),
				DailyTargetInImpressions:        ttdworkflowsgo.Int64(985999),
			},
			BaseBidCPMInAdvertiserCurrency: ttdworkflowsgo.Float64(3785.04),
			MaxBidCPMInAdvertiserCurrency:  ttdworkflowsgo.Float64(7447.3),
			AudienceTargeting: &components.AdGroupWorkflowAudienceTargetingInput{
				AudienceID:                           ttdworkflowsgo.String("<id>"),
				AudienceAcceleratorExclusionsEnabled: ttdworkflowsgo.Bool(true),
				AudienceBoosterEnabled:               ttdworkflowsgo.Bool(true),
				AudienceExcluderEnabled:              ttdworkflowsgo.Bool(true),
				AudiencePredictorEnabled:             ttdworkflowsgo.Bool(false),
				CrossDeviceVendorListForAudience: []int{
					107263,
				},
				RecencyExclusionWindowInMinutes: ttdworkflowsgo.Int(90062),
				TargetTrackableUsersEnabled:     ttdworkflowsgo.Bool(true),
				UseMcIDAsPrimary:                ttdworkflowsgo.Bool(true),
			},
			RoiGoal: &components.AdGroupWorkflowROIGoalInput{
				MaximizeReach:               ttdworkflowsgo.Bool(true),
				MaximizeLtvIncrementalReach: ttdworkflowsgo.Bool(false),
				CpcInAdvertiserCurrency:     ttdworkflowsgo.Float64(2280.31),
				CtrInPercent:                nil,
				NielsenOTPInPercent:         ttdworkflowsgo.Float64(5175.21),
				CpaInAdvertiserCurrency:     ttdworkflowsgo.Float64(2544.37),
				ReturnOnAdSpendPercent:      ttdworkflowsgo.Float64(8201.47),
				VcrInPercent:                ttdworkflowsgo.Float64(4846.08),
				ViewabilityInPercent:        nil,
				VcpmInAdvertiserCurrency:    ttdworkflowsgo.Float64(4649.53),
				CpcvInAdvertiserCurrency:    ttdworkflowsgo.Float64(313.95),
				MiaozhenOTPInPercent:        ttdworkflowsgo.Float64(4704.1),
			},
			CreativeIds: nil,
			AssociatedBidLists: []components.AdGroupWorkflowAssociateBidListInput{
				components.AdGroupWorkflowAssociateBidListInput{
					BidListID:             "<id>",
					IsEnabled:             ttdworkflowsgo.Bool(false),
					IsDefaultForDimension: ttdworkflowsgo.Bool(true),
				},
			},
			Name:                                    ttdworkflowsgo.String("<value>"),
			Channel:                                 components.AdGroupChannelDisplay,
			FunnelLocation:                          components.AdGroupFunnelLocationConsideration,
			ProgrammaticGuaranteedPrivateContractID: ttdworkflowsgo.String("<id>"),
		},
		CampaignID: ttdworkflowsgo.String("<id>"),
		AdvancedInput: &components.AdGroupWorkflowAdvancedInput{
			KoaOptimizationSettings: &components.AdGroupWorkflowKoaOptimizationSettingsInput{
				AreFutureKoaFeaturesEnabled: ttdworkflowsgo.Bool(false),
				PredictiveClearingEnabled:   ttdworkflowsgo.Bool(false),
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
				AllowOpenMarketBiddingWhenTargetingContracts: ttdworkflowsgo.Bool(true),
			},
			DimensionalBiddingAutoOptimizationSettings: [][]components.DimensionalBiddingDimensions{
				[]components.DimensionalBiddingDimensions{},
				[]components.DimensionalBiddingDimensions{},
			},
			IsUseClicksAsConversionsEnabled:  ttdworkflowsgo.Bool(false),
			IsUseSecondaryConversionsEnabled: ttdworkflowsgo.Bool(false),
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
					FrequencyCap:           ttdworkflowsgo.Int(375286),
					FrequencyGoal:          ttdworkflowsgo.Int(534735),
					ResetIntervalInMinutes: ttdworkflowsgo.Int(788122),
				},
			},
			Flights: []components.AdGroupWorkflowFlightInput{
				components.AdGroupWorkflowFlightInput{
					AllocationType:                  components.AllocationTypeMaximum.ToPointer(),
					BudgetInAdvertiserCurrency:      ttdworkflowsgo.Float64(4070.96),
					BudgetInImpressions:             ttdworkflowsgo.Int64(901477),
					DailyTargetInAdvertiserCurrency: ttdworkflowsgo.Float64(5847.35),
					DailyTargetInImpressions:        ttdworkflowsgo.Int64(257517),
					CampaignFlightID:                874887,
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
<!-- End SDK Example Usage [usage] -->