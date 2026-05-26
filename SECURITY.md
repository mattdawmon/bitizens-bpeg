# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability in any BITIZENS (BPEG) smart contract,
the wrap/escrow layer, the Uniswap v4 Hook, or any supporting infrastructure,
please report it **privately** through one of the channels below. Do not open a
public GitHub issue for security reports.

**Preferred contact channels:**

- **Email:** mattdawmon@gmail.com
- **Telegram:** [@mattdawmon](https://t.me/mattdawmon)

Please include:

1. A clear description of the vulnerability and its impact.
2. Steps to reproduce (transaction hashes on BSC mainnet, contract calls, or
   a proof-of-concept script).
3. Your suggested fix or mitigation, if any.
4. Whether you wish to be credited publicly after disclosure.

## Scope

In scope:

- Deployed smart contracts on BNB Smart Chain (see the Contract Addresses table
  in [README.md](./README.md)).
- The Uniswap v4 Hook (`0x097cA33924Ad253EF9FC8471c4490566E0eF1000`).
- The Wrap Escrow (`0x8545a3b74962e694B75eA4420F61cd1284011805`) and
  Wrapped Bitizen ERC-721 (`0x3dd42faD063C6076Ef64952e8893e6940564819e`).
- The off-chain EIP-712 order book and its on-chain settlement contract.
- The frontend at https://www.bpeg.art (signing flows, RPC handling,
  wallet integration).

Out of scope:

- Third-party services (BscScan, wallet providers, RPC providers, Uniswap v4
  core contracts deployed by Uniswap Labs).
- Issues requiring physical access to a user's device or compromised private
  keys.
- Social engineering attacks against holders.

## Response Timeline

- **Initial acknowledgment:** within 48 hours.
- **Triage and severity assessment:** within 5 business days.
- **Coordinated disclosure timing:** agreed case by case based on severity and
  fix complexity.

Thank you for helping keep BITIZENS holders safe.
