---
icon: calendar-users
---

# Referrals

Earn passive income by inviting friends to trade on LiqCoin, the revolutionary token launch platform on the **Base mainnet**. By sharing your unique referral link, you can build your network, grow the DeFi ecosystem, and earn commissions on trading fees from meme coin launches and liquidity pool interactions.

## Multi-Level Referral System

LiqCoin’s referral program rewards you for both direct and indirect referrals, making it easy to earn while expanding the community.

### Level 1: Direct Referrals

* **Commission**: 8% of the calculated referral reward (1% trading fee × 0.001) from your direct referrals.
* **Who Qualifies**: Users who sign up using your referral code or link and trade on LiqCoin (e.g., via `invest` or `createLaunch` functions on the `LPLaunch` contract).

### Level 2: Indirect Referrals

* **Commission**: 2% of the calculated referral reward (1% trading fee × 0.001) from your direct referrals’ referrals.
* **Who Qualifies**: Users referred by your direct referrals who trade on LiqCoin.

## Reward Calculation

* **Trading Fee**: A 1% fee is applied to trades on LiqCoin-launched tokens (e.g., via Uniswap v4 pools).
* **Referral Base**: The fee is multiplied by 0.001 to determine the referral reward pool.
* **Distribution**:
  * **Direct Referrals (Level 1)**: You earn 8% of the referral reward pool.
  * **Indirect Referrals (Level 2)**: You earn 2% of the referral reward pool.
* **Example**:
  * A trade incurs a $100 trading fee.
  * Referral reward pool = $100 × 1% × 0.001 = $0.001.
  * Level 1 commission = $0.001 × 8% = $0.00008 (in ETH).
  * Level 2 commission = $0.001 × 2% = $0.00002 (in ETH).

## How It Works

1. **Get Your Referral Link**:
   * Sign up on the LiqCoin platform (Base mainnet) and connect your wallet.
   * Access your unique referral code or link in your LiqCoin dashboard.
2. **Share with Friends**:
   * Share your referral link via social media, Telegram, Discord, or direct messages.
   * Encourage friends to join LiqCoin and trade meme coins like LiqSurge.
3. **Build Your Network**:
   * Friends who sign up with your link become **direct referrals** (Level 1).
   * Their referrals become **indirect referrals** (Level 2).
4. **Earn Commissions**:
   * Earn 8% of the referral reward pool from your direct referrals’ trading fees.
   * Earn 2% of the referral reward pool from your indirect referrals’ trading fees.
   * Commissions are paid in ETH, automatically credited to your wallet on a weekly basis via the `LaunchData` contract.
5. **Track and Claim Rewards**:
   * Monitor referral activity and earnings via the LiqCoin dashboard.
   * Query reward data using the GraphQL indexer: `https://api.studio.thegraph.com/query/55427/liqcoin-base-main/version/latest`.
   * Claim your rewards by interacting with the `LaunchData` contract at `0xba65D9F9B6dc4531F8eB6582794ACF546e39c0B4` (see Smart Contracts for scripting examples).

## Benefits of the Referral Program

* **Passive Income**: Earn ETH without active trading by leveraging your network.
* **Scalable Rewards**: The more users you refer, the higher your potential earnings.
* **Community Growth**: Contribute to LiqCoin’s mission to outshine platforms like Pump.fun by building a vibrant DeFi ecosystem.
* **Transparency**: All transactions and rewards are on-chain, verifiable via the `LaunchData` contract (`0xba65D9F9B6dc4531F8eB6582794ACF546e39c0B4`).

## Terms and Conditions

* **Eligibility**: Open to all LiqCoin users with a connected Base mainnet wallet.
* **Trading Fees**: Commissions are derived from the 1% trading fee on LiqCoin-launched tokens, adjusted by the 0.001 multiplier.
* **Payouts**: ETH commissions are distributed weekly, subject to a minimum threshold of 0.001 ETH to cover gas fees.
* **Fair Use**: Abuse (e.g., self-referrals, spam) may result in disqualification from the program.
* **Mainnet Context**: Rewards are paid in Base mainnet ETH, reflecting real economic value.

## Get Started

1. Connect your wallet to LiqCoin on the Base mainnet.
2. Grab your referral link from the dashboard.
3. Share it with friends, developers, and meme coin enthusiasts.
4. Track and claim your earnings via the `LaunchData` contract!

Join the LiqCoin referral program today and help power the future of decentralized meme coin launches! For technical details, check out our Smart Contracts guide or explore the contract ABIs on our [GitHub ABI Repository](https://github.com/LiqCoin/abis?tab=readme-ov-file).
