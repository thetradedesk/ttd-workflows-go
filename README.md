# github.com/thetradedesk/ttd-workflows-go

Developer-friendly & type-safe Go SDK specifically catered to leverage *github.com/thetradedesk/ttd-workflows-go* API.

<div align="left">
    <a href="https://www.speakeasy.com/?utm_source=github-com/thetradedesk/ttd-workflows-go&utm_campaign=go"><img src="https://custom-icon-badges.demolab.com/badge/-Built%20By%20Speakeasy-212015?style=for-the-badge&logoColor=FBE331&logo=speakeasy&labelColor=545454" /></a>
    <a href="https://opensource.org/licenses/MIT">
        <img src="https://img.shields.io/badge/License-MIT-blue.svg" style="width: 100px; height: 28px;" />
    </a>
</div>

<!-- Start Summary [summary] -->
## Summary

Workflows Service: 
This service provides operations for commonly used workflows on The Trade Desk's platform.
In addition, this service provides generic operations for submitting:

- GraphQL API requests
- REST API requests

For further explanation on the entities encountered in this documentation (e.g.,
[campaigns](https://partner.thetradedesk.com/v3/portal/api/doc/Campaigns) and
[ad groups](https://partner.thetradedesk.com/v3/portal/api/doc/AdGroup)), visit the
[Partner Portal](https://partner.thetradedesk.com/v3/portal/api/doc/ApiUseCases).
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [github.com/thetradedesk/ttd-workflows-go](#githubcomthetradedeskttd-workflows-go)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Retries](#retries)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
  * [Custom HTTP Client](#custom-http-client)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

To add the SDK as a dependency to your project:
```bash
go get github.com/thetradedesk/ttd-workflows-go
```
<!-- End SDK Installation [installation] -->

## SDK Example Usage

### Example: Submit job to retrieve third-party data

```go
package main

import (
	"context"
	"fmt"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"log"
)

func main() {
	ctx := context.Background()

	s := ttdworkflowsgo.New(
		ttdworkflowsgo.WithServer("sandbox"),
		ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
	)
	res, err := s.Dmps.GetThirdPartyDataJob(ctx, &components.ThirdPartyDataInput{
		PartnerID: "<id>",
		QueryShape: ttdworkflowsgo.String("nodes {id name}"),
	})
	if err != nil {
		log.Fatal(err)
	}
	if res.StandardJobSubmitResponse != nil {
		if jobPtr := res.StandardJobSubmitResponse.GetID(); jobPtr != 0 {
			fmt.Println("Submitted job ID:", jobPtr)
		} else {
			fmt.Println("Job ID is nil")
		}
	} else {
		fmt.Println("Job submission failed")
	}
}
```

([Reference](https://ttd-workflows.apidocumentation.com/reference#tag/dmp/post/standardjob/thirdpartydata))

### Example: Check status for third-party data retrieval job using job ID returned from submit job

```go
package main

import (
	"context"
	"fmt"
	"log"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
)

func main() {
	ctx := context.Background()

	s := ttdworkflowsgo.New(
		ttdworkflowsgo.WithServer("sandbox"),
		ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
	)

	res, err := s.JobStatus.Get(ctx, <id>)
	if err != nil {
		log.Fatal(err)
	}
	if res.StandardJobStatusResponse != nil {
		if completionPtr := res.StandardJobStatusResponse.CompletionPercentage; completionPtr != nil {
			fmt.Println("Job completion percentage:", *completionPtr)
			} else {
			fmt.Println("Job completion percentage is nil")
		}
	} else {
		fmt.Println("Getting job completion status failed")
	}
}
```

([Reference](https://ttd-workflows.apidocumentation.com/reference#tag/job-status/get/standardjob/{id}/status))

### Example: Create campaign with minimal configuration

```go
package main

import (
	"context"
	"fmt"
	"log"
	"os"
	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"github.com/thetradedesk/ttd-workflows-go/types"
)

func main() {
	ctx := context.Background()

	s := ttdworkflowsgo.New(
		ttdworkflowsgo.WithServer("sandbox"),
		ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
	)

	var seedID = "<id>"

	res, err := s.Campaigns.CreateCampaign(ctx, &components.CampaignCreateWorkflowInputWithValidation{
		PrimaryInput: components.CampaignCreateWorkflowPrimaryInput{
			Name: "<value>",
			AdvertiserID: "<id>",
			SeedID: &seedID, // required, unless the advertiser has a default seed defined
			StartDateInUtc: types.MustNewTimeFromString("2026-07-08T10:52:56.944Z"),
			PrimaryChannel: components.CampaignChannelTypeDooh,
			PrimaryGoal: components.CampaignWorkflowROIGoalInput{
				MaximizeReach: ttdworkflowsgo.Bool(true),
			},
		},
	})
	if err != nil {
		log.Fatal(err)
	}
	if res.CampaignPayload != nil {
		if idPtr := res.CampaignPayload.GetCampaign().ID; idPtr != nil {
			fmt.Println("Campaign ID: ", *idPtr)
		} else {
			fmt.Println("Campaign ID is nil")
		}
	} else {
		fmt.Println("Campaign creation failed")
	}
}
```

([Reference](https://ttd-workflows.apidocumentation.com/reference#tag/campaign/post/campaign))

### Example: Submit GraphQL request

```go
package main

import (
	"context"
	"fmt"
	"log"
	"os"

	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
)

func main() {
	ctx := context.Background()

	s := ttdworkflowsgo.New(
		ttdworkflowsgo.WithServer("sandbox"),
		ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
	)

	query := `
query Advertiser($id: ID!) {
	advertiser(id: $id) {
		name
		totalCampaignChannelCount
		totalFunnelLocationCount
		useImpressionsOnlyBudgeting
		vettingStatus
		suggestedMeasurementProviderCategories
	}
}
`

	res, err := s.GraphQlRequests.Submit(ctx, &components.GraphQLRequestInput{
		Request: query,
		Variables: map[string]any{
			"id": "<id>",
		},
	})
	if err != nil {
		log.Fatal(err)
	}
	if res.Object != nil {
		fmt.Println(res.Object)
	}
}
```

([Reference](https://ttd-workflows.apidocumentation.com/reference#tag/graphql-request/post/graphqlrequest))

### Example: Submit bulk GraphQL query job

Note: If you submit a GraphQL bulk query job (instead of a standard GraphQL request as shown above), any paginated and nested data is fully iterated and returned in a single output file.

```go
package main

import (
	"context"
	"fmt"
	"log"
	"os"

	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
)

func main() {
	ctx := context.Background()

	s := ttdworkflowsgo.New(
		ttdworkflowsgo.WithServer("sandbox"),
		ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
	)

	query := `
query AudiencesAcrossAdvertisers {
  partner(id: "<id>") {
	id
	name
	advertisers {
	  nodes {
		id
		name
		adGroups {
		  nodes {
			id
			name
			audience {
			  id
			  name
			  activeUniques {
				householdCount
				idsConnectedTvCount
				idsCount
				idsInAppCount
				idsWebCount
				lastUpdated
				personsCount
			  }
			}
		  }
		}
	  }
	}
  }
}
`

	res, err := s.GraphQlRequests.SubmitBulkQueryJob(ctx, &components.GraphQlQueryJobInput{
		Query: query,
	})
	if err != nil {
		log.Fatal(err)
	}
	if res.GraphQlQueryJobResponse != nil {
		if jobPtr := res.GraphQlQueryJobResponse.GetPayload(); jobPtr != nil {
			fmt.Println(jobPtr.Data.ID);
		} else {
			fmt.Println("Job ID is nil")
		}
	} else {
		fmt.Println("Job submission failed")
	}
}
```

([Reference](https://ttd-workflows.apidocumentation.com/reference#tag/graphql-request/post/graphqlqueryjob))

### Example: Check status for bulk GraphQL query job

```go
package main

import (
	"context"
	"fmt"
	"log"
	"os"

	ttdworkflowsgo "github.com/thetradedesk/ttd-workflows-go"
)

func main() {
	ctx := context.Background()

	s := ttdworkflowsgo.New(
		ttdworkflowsgo.WithServer("sandbox"),
		ttdworkflowsgo.WithSecurity(os.Getenv("WORKFLOWS_TTD_AUTH")),
	)

	res, err := s.Jobs.GetStatus(ctx, "<id>")
	if err != nil {
		log.Fatal(err)
	}
	if res.GraphQLQueryJobRetrievalResponse != nil {
		if jobPtr := res.GraphQLQueryJobRetrievalResponse.GetJob(); jobPtr != nil {
			fmt.Printf("Job completion: %.1f%%\n", *jobPtr.CompletionPercentage)
			if *jobPtr.CompletionPercentage == 100 {
				fmt.Println("\nResult URL:", *jobPtr.URL)
				fmt.Println("\nRaw result:", *jobPtr.RawResult)
			}
		}
	}
}
```

([Reference](https://ttd-workflows.apidocumentation.com/reference#tag/job-status/get/graphqlqueryjob/{id}))

<!-- No SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name      | Type   | Scheme  | Environment Variable |
| --------- | ------ | ------- | -------------------- |
| `TTDAuth` | apiKey | API key | `WORKFLOWS_TTD_AUTH` |

You can configure it using the `WithSecurity` option when initializing the SDK client instance. For example:
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
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [AdGroups](docs/sdks/adgroups/README.md)

* [Create](docs/sdks/adgroups/README.md#create) - Create a new ad group with required fields
* [Update](docs/sdks/adgroups/README.md#update) - Update an ad group with specified fields
* [Archive](docs/sdks/adgroups/README.md#archive) - Archive multiple ad groups
* [BulkCreate](docs/sdks/adgroups/README.md#bulkcreate) - Create multiple new ad groups with required fields
* [BulkUpdate](docs/sdks/adgroups/README.md#bulkupdate) - Update multiple ad groups with specified fields

### [Campaigns](docs/sdks/campaigns/README.md)

* [CreateCampaign](docs/sdks/campaigns/README.md#createcampaign) - Create a new campaign with required fields
* [Update](docs/sdks/campaigns/README.md#update) - Update a campaign with specified fields
* [BulkCreate](docs/sdks/campaigns/README.md#bulkcreate) - Create multiple new campaigns with required fields
* [BulkUpdate](docs/sdks/campaigns/README.md#bulkupdate) - Update multiple campaigns with specified fields
* [Archive](docs/sdks/campaigns/README.md#archive) - Archive multiple campaigns
* [GetCampaignVersion](docs/sdks/campaigns/README.md#getcampaignversion) - Get a campaign's version

### [Dmps](docs/sdks/dmps/README.md)

* [GetFirstPartyDataJob](docs/sdks/dmps/README.md#getfirstpartydatajob) - Submit a job for first-party data retrieval for an advertiser
* [GetThirdPartyDataJob](docs/sdks/dmps/README.md#getthirdpartydatajob) - Submit a job for third-party data retrieval for a partner

### [GraphQlRequests](docs/sdks/graphqlrequests/README.md)

* [Submit](docs/sdks/graphqlrequests/README.md#submit) - Submit a valid GraphQL query or mutation
* [SubmitBulkQueryJob](docs/sdks/graphqlrequests/README.md#submitbulkqueryjob) - Submit a valid bulk GraphQL query

### [Jobs](docs/sdks/jobs/README.md)

* [GetStatus](docs/sdks/jobs/README.md#getstatus) - Get the status of a previously submitted GraphQL query job.

### [JobStatus](docs/sdks/jobstatus/README.md)

* [Get](docs/sdks/jobstatus/README.md#get) - Get the status of a previously submitted job

### [RestRequests](docs/sdks/restrequests/README.md)

* [Submit](docs/sdks/restrequests/README.md#submit) - Submit a valid REST request


</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Retries [retries] -->
## Retries

Some of the endpoints in this SDK support retries. If you use the SDK without any configuration, it will fall back to the default retry strategy provided by the API. However, the default retry strategy can be overridden on a per-operation basis, or across the entire SDK.

To change the default retry strategy for a single API call, simply provide a `retry.Config` object to the call by using the `WithRetries` option:
```go
package main

import (
	"context"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"github.com/thetradedesk/ttd-workflows-go/retry"
	"log"
	"models/operations"
	"os"
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
	}, operations.WithRetries(
		retry.Config{
			Strategy: "backoff",
			Backoff: &retry.BackoffStrategy{
				InitialInterval: 1,
				MaxInterval:     50,
				Exponent:        1.1,
				MaxElapsedTime:  100,
			},
			RetryConnectionErrors: false,
		}))
	if err != nil {
		log.Fatal(err)
	}
	if res.AdGroupPayload != nil {
		// handle response
	}
}

```

If you'd like to override the default retry strategy for all operations that support retries, you can use the `WithRetryConfig` option at SDK initialization:
```go
package main

import (
	"context"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/components"
	"github.com/thetradedesk/ttd-workflows-go/retry"
	"log"
	"os"
)

func main() {
	ctx := context.Background()

	s := ttdworkflows.New(
		ttdworkflows.WithRetryConfig(
			retry.Config{
				Strategy: "backoff",
				Backoff: &retry.BackoffStrategy{
					InitialInterval: 1,
					MaxInterval:     50,
					Exponent:        1.1,
					MaxElapsedTime:  100,
				},
				RetryConnectionErrors: false,
			}),
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
<!-- End Retries [retries] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or an error, they will never return both.

By Default, an API error will return `apierrors.APIError`. When custom error responses are specified for an operation, the SDK may also return their associated error. You can refer to respective *Errors* tables in SDK docs for more details on possible error types for each operation.

For example, the `Create` function may return the following errors:

| Error Type                    | Status Code | Content Type     |
| ----------------------------- | ----------- | ---------------- |
| apierrors.ProblemDetailsError | 400, 403    | application/json |
| apierrors.APIError            | 4XX, 5XX    | \*/\*            |

### Example

```go
package main

import (
	"context"
	"errors"
	ttdworkflows "github.com/thetradedesk/ttd-workflows-go"
	"github.com/thetradedesk/ttd-workflows-go/models/apierrors"
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

		var e *apierrors.ProblemDetailsError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}

		var e *apierrors.APIError
		if errors.As(err, &e) {
			// handle error
			log.Fatal(e.Error())
		}
	}
}

```
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Select Server by Name

You can override the default server globally using the `WithServer(server string)` option when initializing the SDK client instance. The selected server will then be used as the default on the operations that use it. This table lists the names associated with the available servers:

| Name      | Server                                          | Description                          |
| --------- | ----------------------------------------------- | ------------------------------------ |
| `prod`    | `https://api.thetradedesk.com/workflows`        | The production environment.          |
| `sandbox` | `https://ext-api.sb.thetradedesk.com/workflows` | The sandbox environment for testing. |

#### Example

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
		ttdworkflows.WithServer("sandbox"),
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

### Override Server URL Per-Client

The default server can also be overridden globally using the `WithServerURL(serverURL string)` option when initializing the SDK client instance. For example:
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
		ttdworkflows.WithServerURL("https://api.thetradedesk.com/workflows"),
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
<!-- End Server Selection [server] -->

<!-- Start Custom HTTP Client [http-client] -->
## Custom HTTP Client

The Go SDK makes API calls that wrap an internal HTTP client. The requirements for the HTTP client are very simple. It must match this interface:

```go
type HTTPClient interface {
	Do(req *http.Request) (*http.Response, error)
}
```

The built-in `net/http` client satisfies this interface and a default client based on the built-in is provided by default. To replace this default with a client of your own, you can implement this interface yourself or provide your own client configured as desired. Here's a simple example, which adds a client with a 30 second timeout.

```go
import (
	"net/http"
	"time"

	"github.com/thetradedesk/ttd-workflows-go"
)

var (
	httpClient = &http.Client{Timeout: 30 * time.Second}
	sdkClient  = ttdworkflows.New(ttdworkflows.WithClient(httpClient))
)
```

This can be a convenient way to configure timeouts, cookies, proxies, custom headers, and other low-level configuration.
<!-- End Custom HTTP Client [http-client] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=github-com/thetradedesk/ttd-workflows-go&utm_campaign=go)
