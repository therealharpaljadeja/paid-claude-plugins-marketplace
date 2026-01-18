---
name: cdc-ai-agent
description: Query the Crypto.com AI Agent Service to interact with blockchain data, get token prices, wallet balances, transaction history, and more on Cronos chains. Use when the user wants to query blockchain/crypto data or interact with the Cronos ecosystem.
---

# CDC AI Agent Skill

This skill allows you to query the Crypto.com AI Agent Service API for blockchain data and AI-generated responses about the Cronos ecosystem.

## Prerequisites

The following environment variables must be set:

- `OPENAI_API_KEY` - Your OpenAI API key (required)
- `CRONOS_MAINNET_API_KEY` - Cronos mainnet explorer API key (optional)
- `CRONOS_TESTNET_API_KEY` - Cronos testnet explorer API key (optional)
- `CRONOS_ZKEVM_API_KEY` - Cronos zkEVM explorer API key (optional)
- `CRONOS_ZKEVM_TESTNET_API_KEY` - Cronos zkEVM testnet API key (optional)

## Supported Chains

| Chain ID | Network |
|----------|---------|
| 25 | Cronos Mainnet |
| 338 | Cronos Testnet |
| 388 | Cronos zkEVM |
| 240 | Cronos zkEVM Testnet |

## How to Use

When the user wants to query blockchain data, make a POST request to the CDC AI Agent API:

```bash
curl -X POST "https://ai-agent-api.crypto.com/api/v1/cdc-ai-agent-service/query" \
  -H "Content-Type: application/json" \
  -d '{
    "query": "<USER_QUERY>",
    "options": {
      "openAI": {
        "apiKey": "'"$OPENAI_API_KEY"'",
        "model": "gpt-4o"
      },
      "chainId": <CHAIN_ID>,
      "explorerKeys": {
        "cronosMainnetKey": "'"$CRONOS_MAINNET_API_KEY"'",
        "cronosTestnetKey": "'"$CRONOS_TESTNET_API_KEY"'",
        "cronosZkEvmKey": "'"$CRONOS_ZKEVM_API_KEY"'",
        "cronosZkEvmTestnetKey": "'"$CRONOS_ZKEVM_TESTNET_API_KEY"'"
      },
      "signerAppUrl": "https://cdc-signer-app.vercel.app",
      "context": []
    }
  }'
```

Replace:
- `<USER_QUERY>` with the user's natural language query
- `<CHAIN_ID>` with the appropriate chain ID (default: 25 for Cronos Mainnet)

## Example Queries

Users can ask questions like:
- "What is the current price of CRO?"
- "Get my wallet balance for 0x..."
- "Show recent transactions for address 0x..."
- "What are the top tokens on Cronos?"
- "Get the gas price on Cronos mainnet"

## Response Format

The response is a JSON object:

```json
{
  "status": "string",
  "message": "string",
  "hasErrors": false,
  "results": [
    {
      "status": "Success",
      "function": "string",
      "message": "string",
      "data": {}
    }
  ]
}
```

Present the results to the user in a clear, formatted way.

## Error Handling

If the query fails:
1. Check that `OPENAI_API_KEY` environment variable is set
2. Verify the chain ID is valid (25, 338, 388, or 240)
3. Check network connectivity
4. Review the error message in the response
