# EIP-7702 Account Abstraction with Viem and Candide

This example demonstrates how to upgrade an EOA (Externally Owned Account) to a Smart Account using EIP-7702 delegation, with a local viem wallet signing and Candide providing the Account Abstraction infrastructure.

## What This Example Does

1. Creates a new EOA
2. Upgrades the EOA to a Smart Account using EIP-7702 delegation
3. Signs the EIP-7702 authorization
4. Creates a UserOperation to mint an NFT
5. Uses a paymaster to sponsor gas fees (gasless transaction)
6. Submits the UserOperation to the bundler for execution

## What is EIP-7702?

[EIP-7702](https://eips.ethereum.org/EIPS/eip-7702) is a proposal that allows EOAs to temporarily delegate their code execution to a smart contract. This enables:

- Smart Account features for regular wallets (multisig, social recovery, spending limits, etc.)
- Gasless transactions via paymasters
- Batch transactions (multiple operations in one)
- Temporary delegation - the EOA can revert back anytime

Unlike smart contract wallets, EIP-7702 allows existing EOAs to gain smart account capabilities without migration.

## Prerequisites

- Node.js v18 or higher
- Candide account for bundler and paymaster access ([Sign up here](https://dashboard.candide.dev))
- Ethereum RPC endpoint (RPC node)

## Setup

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure Environment Variables

Copy the `.env.example` file to `.env` and fill in your values:

```bash
cp .env.example .env
```

Then edit `.env` with your RPC endpoint, and Candide configuration if you would like to monitor your logs. Otherwise, use the provided public endpoints. 

### Getting Candide API and Gas Sponsorship

1. Go to [Candide Dashboard](https://dashboard.candide.dev)
2. Create an account and project
3. Get your Bundler URL from the project settings
4. Get your Paymaster URL and create a Sponsorship Policy
5. Add the policy ID to your `.env` file

## Running the Example

```bash
npm start
```

Or with ts-node:

```bash
ts-node index.ts
```

## Configuration Options

### Supported Networks

This example runs on Arbtrum Sepolia testnet by default. To use other networks:

1. Update `CHAIN_ID` in `.env`
2. Update `NODE_URL` to the appropriate RPC endpoint
3. Update `BUNDLER_URL` and `PAYMASTER_URL` for the target network

## Resources

### Candide
- [Candide Documentation](https://docs.candide.dev/)
- [EIP-7702 Getting Started](https://docs.candide.dev/wallet/guides/getting-started-eip-7702/)
- [Candide Dashboard](https://dashboard.candide.dev)

### Account Abstraction
- [EIP-7702 Specification](https://eips.ethereum.org/EIPS/eip-7702)
- [ERC-4337 Overview](https://eips.ethereum.org/EIPS/eip-4337)

## License

MIT
