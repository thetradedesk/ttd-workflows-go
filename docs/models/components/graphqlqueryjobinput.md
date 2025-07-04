# GraphQlQueryJobInput

Required fields for executing a GraphQL query job


## Fields

| Field                                                                                     | Type                                                                                      | Required                                                                                  | Description                                                                               |
| ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `Query`                                                                                   | *string*                                                                                  | :heavy_check_mark:                                                                        | The GraphQL query to execute                                                              |
| `CallbackInput`                                                                           | [*components.GraphQlJobCallbackInput](../../models/components/graphqljobcallbackinput.md) | :heavy_minus_sign:                                                                        | Input class for providing a callback's url and any headers needed for the callback.       |