# GraphQlQueryJobInput

Fields for executing a GraphQL query job


## Fields

| Field                                                                                             | Type                                                                                              | Required                                                                                          | Description                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `Query`                                                                                           | *string*                                                                                          | :heavy_check_mark:                                                                                | The GraphQL query to execute                                                                      |
| `CallbackInput`                                                                                   | [*components.GraphQlBulkJobCallbackInput](../../models/components/graphqlbulkjobcallbackinput.md) | :heavy_minus_sign:                                                                                | Input class for providing a callback's url and any headers needed for the callback.               |
| `BetaFeatures`                                                                                    | **string*                                                                                         | :heavy_minus_sign:                                                                                | Beta features to be enabled for this GraphQL query (passed as TTD-GQL-Beta header)                |