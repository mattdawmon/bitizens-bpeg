# BITIZENS (BPEG)

A 10,000-supply generative pixel-art NFT collection with a 1:1 token↔NFT bond mechanism, deployed on **BNB Smart Chain (BSC, Chain ID 56)**. **First Uniswap v4 Hook project on BNB Chain.**

Website: https://www.bpeg.art

## Technology Stack

- **Blockchain**: BNB Smart Chain (BSC) mainnet
- **Smart Contracts**: Solidity ^0.8.24, deployed and verified on BscScan
- **DeFi Integration**: Uniswap v4 with a custom Hook (BNB as native currency0)
- **Frontend**: React + Vite + wagmi v2 + viem (single chain: `bsc`)
- **Development**: Foundry (Forge), OpenZeppelin libraries, SSTORE2 for on-chain pixel data
- **Standards**: ERC-20 (BPEG token), ERC-721 (Wrapped Bitizen for marketplace compatibility), EIP-712 (off-chain order book)

## Supported Networks

- **BNB Smart Chain Mainnet** (Chain ID: **56**)

Single-chain deployment by design — every contract, the Uniswap v4 Hook, the AMM pool, and the on-chain SVG renderer all live on BSC mainnet. No testnet phase, no multi-chain bridging.

## Contract Addresses

All contracts are deployed and verified on BscScan (BNB Smart Chain, Chain ID 56).

| Contract | Address | Role |
|----------|---------|------|
| BPEG Token (ERC-20) | `0xd775017BA639234d3EB94Ed24e43e51A7B1C5535` | Bonded ERC-20, 10,000 supply |
| Bitizen Registry | `0x09313de0B072DBD548394f47A1F7c5bE08f5bc8E` | Owns the underlying NFT state, enforces the 1:1 bond |
| Uniswap v4 Hook | `0x097cA33924Ad253EF9FC8471c4490566E0eF1000` | Mints/burns NFTs on every pool swap |
| Marketplace | `0xBb5248fF0fb70dFA8e19415e96f4e652A970977C` | EIP-712 off-chain order book settlement |
| On-Chain Renderer | `0xE13bd285b6dda023386553603B0831524b9F0d7e` | Pure-Solidity SVG renderer (no IPFS) |
| Wrapped Bitizen (ERC-721) | `0x3dd42faD063C6076Ef64952e8893e6940564819e` | Optional ERC-721 wrapper for Element / OpenSea |
| Wrap Escrow | `0x8545a3b74962e694B75eA4420F61cd1284011805` | Trustless wrap/unwrap between bonded and standalone NFT |
| Uniswap v4 PoolManager | `0x28e2Ea090877bF75740558f6BFB36A5ffeE9e9dF` | Canonical BSC v4 PoolManager (BPEG/BNB pool with custom hook) |

ABI files for each contract are in [`abis/`](./abis).

## Features

- **First Uniswap v4 Hook project on BNB Chain** — BPEG ships a custom v4 Hook that enforces the 1:1 token↔NFT bond on every pool swap (`beforeSwap` / `afterSwap` lifecycle).
- **AMM-backed NFT floor price on BNB Chain** — buying 1 BPEG via the v4 BNB/BPEG pool automatically mints a unique on-chain Human NFT; selling 1 BPEG automatically burns your most-recent NFT (LIFO). The floor price is set by the AMM, not by marketplace listings.
- **Optional ERC-721 unwrap** — holders can unwrap a bonded BPEG into a standalone ERC-721 NFT to list on **Element**, OpenSea, or any ERC-721 marketplace, and re-wrap it back into BPEG at any time to access pool liquidity. Fully reversible and trustless via the on-chain escrow contract.
- **Fully on-chain SVG renderer** — `tokenURI` returns a complete SVG generated in pure Solidity from on-chain pixel libraries (SSTORE2). No IPFS, no Arweave, no off-chain art server. Renderer fits within BSC's 50M gas block cap (~31M gas per `tokenURI`).
- **Off-chain EIP-712 order book** — peer-to-peer NFT trades at any price, gas-paid only on fill. Settlement on chain via the `HumansMarket` contract (EIP-712 domain `"HumansMarket"`).
- **12-trait generative art** — body + 11 cosmetic slots (hair, eyes, mouth, accessories, companion, etc.), 8 curated Notable Sets (Minimal Palette, Full Spectrum, Chromatic Apex, Monochrome Mood, Two-Tone, Full Loadout, Bare, Companion Club).
- **10,000 hard cap, fair launch** — entire supply seeded into the Uniswap v4 BPEG/BNB pool at launch, no team allocation, no presale, no allowlist.

## License

All Rights Reserved. See [LICENSE](./LICENSE).

## Security

To report a vulnerability, see [SECURITY.md](./SECURITY.md).
