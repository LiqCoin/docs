---
icon: gear-complex-code
---

# Technical Implementation

## Core Problem Addressed

Platforms like Pump.fun, Virtuals, and Flaunch often result in a player-versus-player (PVP) structure post-launch, where builders, primary investors, and secondary market traders compete, leading to early project failures. This undermines the sustainability of application-layer projects.

## Launchpad Liquidity Mechanism

LiqCoin introduces a novel liquidity mechanism to address these issues:

* **Customizable Parameters**: Project creators define fundraising goals, LP fee rates, LP share ratios, and lockup periods.
* **Automated Liquidity Pool**: 100% of raised funds are injected into a Uniswap v4 liquidity pool upon successful funding.
* **Shared Benefits**:
  * **Builders**: Receive LP fee shares during the lockup period and proportional ETH/token shares post-lockup, incentivizing long-term engagement.
  * **Primary Investors**: Earn LP fees and have flexible exit options, enhancing safety.
  * **Secondary Market**: Locked liquidity prevents dumps and insider trading, ensuring stable prices.

## Profit Model

LiqCoin generates revenue through:

* **Pool Creation Fee**: A fixed fee (0.005 ETH) for launching a token.
* **Fundraising Fee**: 1% of raised ETH.
* **LP Fee Share**: 0.1% of liquidity pool fees.

### Price Dynamics

The following chart illustrates the expected token price behavior based on LiqCoin’s liquidity mechanism:\


<figure><img src=".gitbook/assets/liqcoin-token-price-chart (2).png" alt=""><figcaption></figcaption></figure>

The chart shows:

* Days 1–5: Price at 0 (fundraising).
* Day 6: Price jumps to 0.000001 ETH at launch.
* Days 6–15: Gradual increase during lockup, reflecting stability from locked liquidity.
* Days 16–60: Slight volatility post-lockup but continued growth due to incentives.
