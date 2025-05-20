---
icon: btc
---

# Smart Contracts

## Contract Addresses

* **LPLaunch**: `0x120A3961590f887A99C2E144b89Ab904740697d1`
* **LPLaunchState**: `0xd3D4702d2D6D8E18B6B9c3C829194e3C06061697`
* **LiquidityManager**: `0x6cAb1674ea5392bB357B011024D3dB18ba6c4030`
* **Hooks**: `0xB301A7ec48412E31dCCdD7cE0Eb37711a87ac0cc`
* **LPLaunchData**: `0xba65D9F9B6dc4531F8eB6582794ACF546e39c0B4`
* **Uniswap Contracts**:
  * State View: `0xa3c0c9b65bad0b08107aa264b0f3db444b867a71`
  * Position Manager: `0x7c5f5a4bbd8fd63184577525326123b519429bdc`
  * Pool Manager: `0x498581ff718922c3f8e6a244956af099b2652b2b`
  * Universal Router: `0x6ff5693b99212da76ad316178a184ab56d299b43`

## Contract Overview

The LiqCoin platform relies on three primary contracts:

* **LPLaunch**: Manages coin launches, fundraising, and liquidity pool creation.
* **LPLaunchState**: Stores coin metadata and launch configurations.
* **LiquidityManager**: Handles liquidity pool interactions with Uniswap v4.
* **LPLaunchData**: referral relationships, referral reward data, and claim feature.

Key functionalities include:

* **createLaunch**: Initiates a new coin launch with specified parameters.
* **invest**: Allows users to contribute ETH to a launch.
* **divest**: Enables investors to exit before launch completion.
* **removeLiquidity**: Withdraws liquidity after the lockup period.
* **claimFees**: Claims accumulated LP fees.

## Community Scripting Guide

To interact with LiqCoin contracts, developers can use JavaScript with ethers.js. Below is an example script demonstrating how to call the main functions. Ensure you have a provider (e.g., Infura, Alchemy) and a wallet with ETH on the Base mainnet.

```javascript
const { ethers } = require("ethers");

// Configuration
const provider = new ethers.providers.JsonRpcProvider("https://basemain.infura.io/v3/YOUR_INFURA_KEY");
const wallet = new ethers.Wallet("YOUR_PRIVATE_KEY", provider);
const lpLaunchAddress = "0xDb859ee3713a8619CDd58Fdf33B23A99F2c49F5A";
const lpLaunchABI = [ /* ABI from contract compilation, or use ethers.getContractAt */ ];

// Initialize contract
const lpLaunchContract = new ethers.Contract(lpLaunchAddress, lpLaunchABI, wallet);

// 1. createLaunch
async function createLaunch() {
  const targetAmount = ethers.utils.parseEther("1"); // 1 ETH
  const poolLockDays = 30; // 30 days lockup
  const devLpRatio = 1000; // 10% LP share for dev
  const poolFee = 3000; // 0.3% fee
  const initialTick = 0; // Initial price tick
  const tokenInfo = {
    name: "MyMemeCoin",
    symbol: "MMC",
    description: "",
    image: "",
    twitter: "",
    telegram: "",
    discord: "",
    youtube: "",
    website: "",
    link: "",
    github: "",
    instagram: "",
    tiktok: "",
    linkedin: ""
  };

  const tx = await lpLaunchContract.createLaunch(
    targetAmount,
    poolLockDays,
    devLpRatio,
    poolFee,
    initialTick,
    tokenInfo,
    { value: ethers.utils.parseEther("0.005") } // Creation fee
  );
  await tx.wait();
  console.log("Launch created:", tx.hash);
}

// 2. invest
async function invest(launchId) {
  const amount = ethers.utils.parseEther("0.1"); // 0.1 ETH
  const tx = await lpLaunchContract.invest(launchId, { value: amount });
  await tx.wait();
  console.log("Invested:", tx.hash);
}

// 3. divest
async function divest(launchId) {
  const tx = await lpLaunchContract.divest(launchId);
  await tx.wait();
  console.log("Divested:", tx.hash);
}

// 4. removeLiquidity
async function removeLiquidity(launchId) {
  const tx = await lpLaunchContract.removeLiquidity(launchId);
  await tx.wait();
  console.log("Liquidity removed:", tx.hash);
}

// 5. claimFees
async function claimFees(launchId) {
  const tx = await lpLaunchContract.claimFees(launchId);
  await tx.wait();
  console.log("Fees claimed:", tx.hash);
}

// Example usage
async function main() {
  await createLaunch();
  await invest(1); // Assuming launchId = 1
  await divest(1);
  await removeLiquidity(1);
  await claimFees(1);
}

main().catch(console.error);
```

#### Contract ABI

The script uses the following ABI, which includes the necessary functions and events for interacting with the `LPLaunch` contract. You can listen for events like `CreateLaunch`, `Invest`, `Divest`, `RemoveLiquidity`, and `ClaimFees` to monitor transaction outcomes.

For the complete ABI definitions of these contracts, visit our GitHub ABI Repository.

[https://github.com/LiqCoin/abis?tab=readme-ov-file](https://github.com/LiqCoin/abis?tab=readme-ov-file)

**Prerequisites**:

* Install ethers.js: `npm install ethers`.
* Replace `YOUR_INFURA_KEY` and `YOUR_PRIVATE_KEY` with your credentials.
* Obtain the contract ABI from the compiled contract or use a tool like Hardhat.
* Ensure the wallet has sufficient ETH for gas and transaction fees.

**GraphQL** : \
Use the GraphQL endpoint ([`https://api.studio.thegraph.com/query/55427/liqcoin-sepolia/version/latest`](https://api.studio.thegraph.com/query/55427/liqcoin-base-main/version/latest)) to query launch data, such as active launches, funding progress, and LP details.\


```javascript
query {
  launches(first: 1, orderBy: launchDoneTime, orderDirection: desc) {
    id
    launchToken
    poolId
    fundTotal
    launchDoneTime
  }
}
```
