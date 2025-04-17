---
icon: btc
---

# Smart Contracts

## Contract Addresses

* **LPLaunch**: `0xDb859ee3713a8619CDd58Fdf33B23A99F2c49F5A`
* **LPLaunchState**: `0x989BDd356e3d933a27111269eB37471A2420a3F1`
* **LiquidityManager**: `0xE54eaF9E2BB9cF71eD5FF783C149dD0B1Ec86878`
* **Hooks**: `0xc7cb6318c7A8A5B4B272AE70Ca44b09cB8710044`
* **Uniswap Contracts**:
  * State View: `0xe1dd9c3fa50edb962e442f60dfbc432e24537e4c`
  * Position Manager: `0x429ba70129df741B2Ca2a85BC3A2a3328e5c09b4`
  * Pool Manager: `0xE03A1074c86CFeDd5C142C4F04F1a1536e203543`
  * Universal Router: `0x3a9d48ab9751398bbfa63ad67599bb04e4bdf98b`

## Contract Overview

The LiqCoin platform relies on three primary contracts:

* **LPLaunch**: Manages coin launches, fundraising, and liquidity pool creation.
* **LPLaunchState**: Stores coin metadata and launch configurations.
* **LiquidityManager**: Handles liquidity pool interactions with Uniswap v4.

Key functionalities include:

* **createLaunch**: Initiates a new coin launch with specified parameters.
* **invest**: Allows users to contribute ETH to a launch.
* **divest**: Enables investors to exit before launch completion.
* **removeLiquidity**: Withdraws liquidity after the lockup period.
* **claimFees**: Claims accumulated LP fees.

## Community Scripting Guide

To interact with LiqCoin contracts, developers can use JavaScript with ethers.js. Below is an example script demonstrating how to call the main functions. Ensure you have a provider (e.g., Infura, Alchemy) and a wallet with ETH on the Sepolia testnet.

```javascript
const { ethers } = require("ethers");

// Configuration
const provider = new ethers.providers.JsonRpcProvider("https://sepolia.infura.io/v3/YOUR_INFURA_KEY");
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

```json
[
  {
    "inputs": [
      {
        "internalType": "uint256",
        "name": "_targetAmount",
        "type": "uint256"
      },
      {
        "internalType": "uint256",
        "name": "_poolLockDays",
        "type": "uint256"
      },
      {
        "internalType": "uint256",
        "name": "_devLpRatio",
        "type": "uint256"
      },
      {
        "internalType": "uint24",
        "name": "_poolFee",
        "type": "uint24"
      },
      {
        "internalType": "int24",
        "name": "_initialTick",
        "type": "int24"
      },
      {
        "components": [
          {
            "internalType": "string",
            "name": "name",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "symbol",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "description",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "image",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "twitter",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "telegram",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "discord",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "youtube",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "website",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "link",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "github",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "instagram",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "tiktok",
            "type": "string"
          },
          {
            "internalType": "string",
            "name": "linkedin",
            "type": "string"
          }
        ],
        "internalType": "struct ILPLaunchState.TokenInfo",
        "name": "_tokenInfo",
        "type": "tuple"
      }
    ],
    "name": "createLaunch",
    "outputs": [],
    "stateMutability": "payable",
    "type": "function"
  },
  {
    "inputs": [
      {
        "internalType": "uint256",
        "name": "launchId",
        "type": "uint256"
      }
    ],
    "name": "invest",
    "outputs": [],
    "stateMutability": "payable",
    "type": "function"
  },
  {
    "inputs": [
      {
        "internalType": "uint256",
        "name": "launchId",
        "type": "uint256"
      }
    ],
    "name": "divest",
    "outputs": [],
    "stateMutability": "nonpayable",
    "type": "function"
  },
  {
    "inputs": [
      {
        "internalType": "uint256",
        "name": "launchId",
        "type": "uint256"
      }
    ],
    "name": "removeLiquidity",
    "outputs": [],
    "stateMutability": "nonpayable",
    "type": "function"
  },
  {
    "inputs": [
      {
        "internalType": "uint256",
        "name": "launchId",
        "type": "uint256"
      }
    ],
    "name": "claimFees",
    "outputs": [],
    "stateMutability": "nonpayable",
    "type": "function"
  },
  {
    "anonymous": false,
    "inputs": [
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "_launchId",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "address",
        "name": "creator",
        "type": "address"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "_targetAmount",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "_poolLockDays",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "_devLpRatio",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "uint24",
        "name": "_poolFee",
        "type": "uint24"
      },
      {
        "indexed": false,
        "internalType": "int24",
        "name": "_initialTick",
        "type": "int24"
      }
    ],
    "name": "CreateLaunch",
    "type": "event"
  },
  {
    "anonymous": false,
    "inputs": [
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "_launchId",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "address",
        "name": "account",
        "type": "address"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "amount",
        "type": "uint256"
      }
    ],
    "name": "Invest",
    "type": "event"
  },
  {
    "anonymous": false,
    "inputs": [
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "_launchId",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "address",
        "name": "account",
        "type": "address"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "amount",
        "type": "uint256"
      }
    ],
    "name": "Divest",
    "type": "event"
  },
  {
    "anonymous": false,
    "inputs": [
      {
        "indexed": false,
        "internalType": "address",
        "name": "account",
        "type": "address"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "lpToken0",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "lpToken1",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "feeToken0",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "feeToken1",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "launchId",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "address",
        "name": "launchToken",
        "type": "address"
      }
    ],
    "name": "RemoveLiquidity",
    "type": "event"
  },
  {
    "anonymous": false,
    "inputs": [
      {
        "indexed": false,
        "internalType": "address",
        "name": "account",
        "type": "address"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "token0",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "token1",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "uint256",
        "name": "launchId",
        "type": "uint256"
      },
      {
        "indexed": false,
        "internalType": "address",
        "name": "launchToken",
        "type": "address"
      }
    ],
    "name": "ClaimFees",
    "type": "event"
  }
]
```

**Prerequisites**:

* Install ethers.js: `npm install ethers`.
* Replace `YOUR_INFURA_KEY` and `YOUR_PRIVATE_KEY` with your credentials.
* Obtain the contract ABI from the compiled contract or use a tool like Hardhat.
* Ensure the wallet has sufficient ETH for gas and transaction fees.

**GraphQL** : \
Use the GraphQL endpoint (`https://api.studio.thegraph.com/query/55427/liqcoin-sepolia/version/latest`) to query launch data, such as active launches, funding progress, and LP details.\


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
