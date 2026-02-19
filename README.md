# HTLC Trade Skill

Atomic swap trading for inscriptions and NFTs on EVM chains.

## Description

HTLC (Hash Time Locked Contract) trading for inscriptions and NFTs on EVM chains - atomic swaps without intermediaries.

## Features

- Generate preimage/hash pairs for HTLC trades
- Lock ETH in BaseTimelock contract
- Reveal preimage to complete atomic swaps
- Full trade workflow automation
- Support for Base, Ethereum, Arbitrum and other EVM chains

## Quick Start

```bash
# Install dependencies
npm install

# Set environment
export PRIVATE_KEY=0x...
export BASE_ETH_RPC=https://mainnet.base.org

# Generate preimage
node scripts/htlc.js preimage

# Lock ETH (buyer)
node scripts/htlc.js lock <seller> <hash> <timeout> <amountETH>

# Reveal (seller)
node scripts/htlc.js reveal <lockHash> <preimage>

# Full trade
node scripts/htlc.js trade <seller> <inscriptionTx> <amountETH>
```

## Contract

**BaseTimelock:** `0xa7f9f88e753147d69baf8f2fef89a551680dbac1`

## How It Works

1. **Setup** - Seller generates a secret (preimage) and publishes its hash
2. **Lock** - Buyer deposits funds into smart contract, locked by hash + time limit
3. **Reveal** - Seller reveals the preimage to claim funds
4. **Complete** - Buyer learns the secret, transaction finalized
5. **Timeout** - If seller doesn't reveal in time, funds return to buyer

## Use Cases

- Peer-to-peer inscription trading
- NFT sales without marketplaces
- Cross-chain asset swaps
- Freelance payment escrow
- DAO treasury releases

## License

MIT
