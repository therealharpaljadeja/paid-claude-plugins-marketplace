---
name: thirdweb
description: Use when the user wants to interact with the thirdweb blockchain platform. Enables wallet management, contract deployment and interaction, token operations, NFT handling, cross-chain bridging, and crypto payments. Requires thirdweb MCP server to be configured.
---

# thirdweb MCP Integration

This skill provides guidance on using the thirdweb MCP server to interact with blockchain infrastructure through natural language commands.

## Prerequisites

### 1. Check Environment Variable

First, check if the `THIRDWEB_SECRET_KEY` environment variable is already set:

```bash
echo ${THIRDWEB_SECRET_KEY:+THIRDWEB_SECRET_KEY is set}
```

If the variable is not set, ask the user to:
1. Go to https://thirdweb.com/dashboard/settings/api-keys
2. Create or copy their secret key
3. Set it as an environment variable: `export THIRDWEB_SECRET_KEY="your-secret-key"`

### 2. MCP Server Configuration

Ensure the thirdweb MCP server is configured in your `.mcp.json`:

```json
{
  "mcpServers": {
    "thirdweb-api": {
      "url": "https://api.thirdweb.com/mcp?secretKey=$THIRDWEB_SECRET_KEY"
    }
  }
}
```

## Available Capabilities

The thirdweb MCP server provides 43+ tools organized into the following categories:

### Authentication & Wallets
- `initiateAuthentication` - Start authentication flow
- `completeAuthentication` - Complete authentication
- `linkAuthentication` - Link authentication methods
- `unlinkAuthentication` - Unlink authentication methods
- `getMyWallet` - Get current wallet details
- `listUserWallets` - List all user wallets
- `createUserWallet` - Create a new user wallet
- `listServerWallets` - List server-managed wallets
- `createServerWallet` - Create a server wallet

### Wallet Operations
- `getWalletBalance` - Check wallet balance
- `getWalletTransactions` - View transaction history
- `getWalletTokens` - List tokens in wallet
- `getWalletNFTs` - List NFTs in wallet
- `signMessage` - Sign a message
- `signTypedData` - Sign typed data (EIP-712)
- `sendTokens` - Transfer tokens

### Contract Interactions
- `listContracts` - List deployed contracts
- `deployContract` - Deploy a new contract
- `readContract` - Read contract state
- `writeContract` - Execute contract functions
- `getContractTransactions` - View contract transactions
- `getContractEvents` - Get contract events
- `getContractMetadata` - Get contract metadata
- `getContractSignatures` - Get contract function signatures

### Transactions
- `getTransactionById` - Get transaction details
- `listTransactions` - List transactions
- `sendTransactions` - Send transactions

### Payments & Tokens
- `createPayment` - Create a payment
- `paymentsPurchase` - Make a purchase
- `getPaymentHistory` - View payment history
- `fetchWithPayment` - Fetch data requiring payment
- `listPayableServices` - List available services
- `createToken` - Create a new token
- `listTokens` - List tokens
- `getTokenOwners` - Get token ownership info

### Bridge & Conversion
- `getBridgeChains` - Get supported bridge chains
- `convertFiatToCrypto` - Convert fiat to crypto
- `bridgeSwap` - Swap tokens across chains

### Chat
- `chat` - Natural language interaction

## Example Prompts

Use these natural language prompts to interact with thirdweb:

### Managing Server Wallets
- "List my server wallets"
- "Create a server wallet called treasury"
- "What's the balance of treasury wallet?"
- "Show me the NFTs in my wallet"
- "What tokens do I have in my wallet?"

### Managing Contracts
- "List my contracts"
- "Deploy an ERC-20 token contract"
- "Read the total supply from contract 0x..."
- "Get the metadata for my contract"
- "Show me recent events from my contract"

### Executing Transactions
- "Approve 100 USDC from treasury wallet to executor wallet"
- "Send 0.1 ETH to 0x..."
- "Transfer 50 tokens to another address"
- "Sign this message with my wallet"

### Token Operations
- "Create a new token called MyToken with symbol MTK"
- "List all my tokens"
- "Who owns my tokens?"

### Bridge & Swap
- "What chains are supported for bridging?"
- "Bridge 100 USDC from Ethereum to Polygon"
- "Convert $100 USD to ETH"

### Payments
- "Create a payment for 10 USDC"
- "Show my payment history"
- "List available payable services"

## Usage Tips

1. **Be specific about wallets**: When you have multiple wallets, specify which one to use by name (e.g., "treasury wallet")
2. **Include amounts and addresses**: For transactions, clearly state the amount, token, and destination
3. **Chain specification**: If working across multiple chains, specify the chain (e.g., "on Ethereum", "on Polygon")
4. **Contract addresses**: Use full contract addresses when interacting with specific contracts

## Documentation

For more details, visit: https://portal.thirdweb.com/ai/mcp
