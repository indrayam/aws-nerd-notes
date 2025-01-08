# aws bedrock

## List of Foundation Models

```bash
aws bedrock list-foundation-models | jq '.modelSummaries[] | { id: .modelId, name: .modelName}'
```