# Apollo Rover Persisted Queries Publish

**IMPORTANT**: This action requires that you first install Rover into the PATH. To do so, please use the [`install-rover` GitHub Action](https://github.com/apollographql-gh-actions/install-rover) as shown below.

This is a GitHub Action to perform the [`rover persisted-queries publish`](https://www.apollographql.com/docs/rover/commands/persisted-queries#persisted-queries-publish) command.

## Inputs

| Name | Description | Required | Default |
| ---- | ----------- | :------: | :-----: |
| `apollo-key` | Your Apollo Studio API key | * | |
| `manifest` | The persisted query manifest file to publish | |
| `graph-ref` | `<NAME>@<VARIANT>` of graph in Apollo Studio | Yes, unless both `graph-id` and `list-id` are set | |
| `graph-id` | The ID of the graph | Yes, if not using `graph-ref` | |
| `list-id` | The persisted query list ID | Yes, if not using `graph-ref` | |
| `manifest-format` | The format of the persisted queries manifest file | | `apollo` |
| `for-client-name` | If provided, overrides the `clientName` field in all operations in the manifest file | | |
| `log` | Specify Rover's log level | | `info` |
| `format` | Specify Rover's log format type [`plain`, `json`] | | `plain` |
| `client-timeout` | Configure the timeout length (in seconds) when performing HTTP(S) requests | | `30` |

## Usage

_**Note**: You must first install the Rover CLI_

```yaml
- uses: apollographql-gh-actions/install-rover@v1
# using graph-ref
- uses: apollographql-gh-actions/rover-persisted-queries-publish@v1
  with:
    apollo-key: ${{ secrets.APOLLO_KEY }}
    graph-ref: ${{ vars.APOLLO_GRAPH_REF }}
    for-client-name: example-publish
    manifest: ./path/to/persisted-queries-manifest.json
# using graph-id and list-id
- uses: apollographql-gh-actions/rover-persisted-queries-publish@v1
  with:
    apollo-key: ${{ secrets.APOLLO_KEY }}
    graph-id: ${{ vars.APOLLO_GRAPH_ID }}
    list-id: 1234-5678
    for-client-name: example-publish
    manifest: ./path/to/persisted-queries-manifest.json
```