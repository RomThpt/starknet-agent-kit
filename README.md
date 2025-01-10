<h1 align="center">
  <img src="https://pbs.twimg.com/profile_images/1834202903189618688/N4J8emeY_400x400.png" width="40"><br>
  starknet-agent-kit (alpha)
</h1>

<p align="center">
  <a href="https://www.npmjs.com/package/starknet-agent-kit">
    <img src="https://img.shields.io/npm/v/starknet-agent-kit.svg" alt="NPM Version" />
  </a>
  <a href="https://github.com/kasarlabs/starknet-agent-kit/blob/main/LICENSE">
    <img src="https://img.shields.io/npm/l/starknet-agent-kit.svg" alt="License" />
  </a>
  <a href="https://github.com/kasarlabs/starknet-agent-kit/stargazers">
    <img src="https://img.shields.io/github/stars/kasarlabs/starknet-agent-kit.svg" alt="GitHub Stars" />
  </a>
  <a href="https://nodejs.org">
    <img src="https://img.shields.io/node/v/starknet-agent-kit.svg" alt="Node Version" />
  </a>
</p>

A NestJS-based toolkit for creating AI agents that can interact with the Starknet blockchain.

> ⚠️ **Warning**: This kit is currently under development. Please note that sharing sensitive information (private keys, personal data, etc.) with AI models involves inherent security risks.

## Getting Started

```bash
npm install @nestjs/common @nestjs/core @nestjs/platform-fastify starknet @langchain/anthropic
```

You will need two things:
- A Starknet wallet private key (you can get one from [Argent X](https://www.argent.xyz/argent-x))
- An Anthropic API key

### Basic Usage

```typescript
import { StarknetAgent } from 'starknet-agent-kit';

const agent = new StarknetAgent({
  anthropicApiKey: process.env.ANTHROPIC_API_KEY,
  walletPrivateKey: process.env.STARKNET_PRIVATE_KEY,
});

// Execute commands in natural language
await agent.execute(
  'Transfer 0.1 ETH to 0x123...'
);

// Get balance
await agent.execute(
  'What is my ETH balance?'
);

// Swap tokens
await agent.execute(
  'Swap 5 USDC for ETH'
);

// Create account
await agent.execute(
  'Create a new Argent account'
);
```

## Features

- Natural language interactions with Starknet blockchain
- ERC20 token transfers
- Token swaps using Avnu
- Balance checking
- Account creation (Argent & OpenZeppelin)
- Account deployment
- RPC interactions (getBlockNumber, getStorageAt, etc.)

## Environment Variables

Create a `.env` file with the following variables:

```env
STARKNET_PRIVATE_KEY=your_private_key
PUBLIC_ADDRESS=your_public_address
ANTHROPIC_API_KEY=your_anthropic_api_key
RPC_URL=your_rpc_url
```

## Local Development

1. Clone the repository:
```bash
git clone https://github.com/yourusername/starknet-agent-kit.git
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run start:dev
```

The API will be available at `http://localhost:3000/api`.

## API Endpoints

### POST /api/agent/request

Make requests to the Starknet agent.

Request body:
```json
{
  "request": "Your natural language request here"
}
```

Headers:
```
x-api-key: your_api_key
```

## Supported Tokens

- ETH
- USDC
- USDT
- STRK

## Tools

All Langchain tools are available to be imported and used directly:

```typescript
import { getBalance, TransferERC20, swapTokens } from 'starknet-agent-kit';
```

## Testing

To run tests:

```bash
npm run test
```

For E2E tests:

```bash
npm run test:e2e
```