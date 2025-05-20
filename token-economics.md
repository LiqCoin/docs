---
icon: memory
---

# Token Economics

The $LIQ token is the native currency of the LiqCoin platform, a revolutionary token launchpad on the **Base mainnet** designed for fair and sustainable token launches. This document outlines the token economics model for $LIQ, covering its supply, pricing, liquidity strategy, utility, and role in platform revenue.

## Token Details

* **Token Name**: $LIQ
* **Total Supply**: 1,000,000,000 $LIQ
* **Token Price**: 0.0000002 ETH per $LIQ
* **Fundraising Goal**: 200 ETH
* **Minimum Investment Amount**: 0.001 ETH
* **Launch Date**: May 20, 2025, 2:00 PM UTC
* **Platform**: Base mainnet, integrated with Uniswap V4 pools and the `LPLaunch` contract (`0x120A3961590f887A99C2E144b89Ab904740697d1`).

The fundraising goal of 200 ETH will be used to pair 100% of raised ETH with $LIQ tokens in a Uniswap V4 liquidity pool, ensuring immediate tradability upon launch.

## Liquidity Strategy

* **Allocation**: 100% of the raised ETH (200 ETH) and an equivalent value of $LIQ tokens will be paired and locked in a Uniswap V4 liquidity pool.
* **Lock-up Period**: 6 months (from May 20, 2025, to November 20, 2025), preventing dumps and ensuring market stability.
* **LP Fee Sharing**: During the lock-up, investors and creators earn liquidity pool fees (1% trading fee, as per the referral program, see Referrals).
* **Post-Unlock**: After 6 months, liquidity is split and returned to contributors (ETH + $LIQ tokens), reducing exit risk and aligning incentives.

This strategy, managed by the `LiquidityManager` contract (`0x6cAb1674ea5392bB357B011024D3dB18ba6c4030`), ensures a safer trading environment by locking liquidity and distributing fees transparently.

## Utility and Incentives

Holding $LIQ provides access to premium features and rewards within the LiqCoin ecosystem, fostering community engagement and long-term value:

* **Platform Access**: Use $LIQ to unlock premium features, such as advanced analytics or priority token launch participation.
* **Governance**: Vote on protocol upgrades, including future DAO governance implementations (see Operational Roadmap).
* **Revenue Sharing**: Earn a share of platform fees and liquidity pool rewards, distributed to $LIQ holders based on their stake.
* **Community Incentives**: Early holders qualify for:
  * Future airdrops of new tokens launched on LiqCoin.
  * Whitelist spots for exclusive launches.
  * Governance privileges in the upcoming on-chain DAO.
* **Investment Benefits**: Holders benefit from token price appreciation and LP fee revenue during the lock-up period, protected by LiqCoin’s anti-dump mechanisms.

## Platform Revenue Integration

The $LIQ token is integral to LiqCoin’s revenue model, which sustains the platform and rewards stakeholders:

* **Pool Creation Fee**: $10 (payable in ETH) per token launch, contributing to platform operations.
* **Fundraising Fee**: 1% of ETH raised per project, shared with $LIQ holders and the protocol treasury.
* **Transaction Fee**: 0.1% fee on liquidity pool trades, with a portion allocated to $LIQ holders via the `LaunchData` contract (`0xba65D9F9B6dc4531F8eB6582794ACF546e39c0B4`).
* **Referral Program**: $LIQ holders participating in the referral program (see Referrals) earn additional ETH rewards (8% for direct referrals, 2% for indirect referrals, based on 1% trading fee × 0.001).

Revenue data can be queried via the GraphQL indexer: `https://api.studio.thegraph.com/query/55427/liqcoin-base-main/version/latest`.

## Why Hold $LIQ?

* **Utility-Driven Rewards**: Access premium features, vote on upgrades, and share in platform revenue.
* **High Upside Potential**: Benefit from token price appreciation and LP fee income, protected by a 6-month liquidity lock.
* **Community-First Ecosystem**: Qualify for airdrops, whitelist spots, and governance roles, fostering a fair and transparent DeFi environment.
* **Risk Mitigation**: Avoid rug pulls and insider dumps through LiqCoin’s locked liquidity and aligned incentives.

The $LIQ token empowers builders, investors, and traders to participate in a safer, more rewarding token launch ecosystem. For technical details, explore our Smart Contracts guide or contract ABIs at the [GitHub ABI Repository](https://github.com/LiqCoin/abis?tab=readme-ov-file).
