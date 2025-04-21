# Token Sale and Refund System via Foundry on Sepolia

This repository implements an ERC20 token sale with a refund mechanism using Solidity on the **Sepolia testnet** via `Foundry` framework. It includes the deployment of various smart contracts, including an ERC20 token with special features for the owner and the users of the token sale platform.

The primary components of this project include:

1. [**ERC20 God Mode Token**](#1-erc20-god-mode-token)  
2. [**ERC20 Sanctions Token**](#2-erc20-sanctions-token)  
3. [**Token Sale Contract**](#3-token-sale-contract)  
4. [**Token Sale Refund Contract**](#4-token-sale-refund-contract)  

Each contract is deployed on **Sepolia** to ensure minimal gas costs, allowing for testing and experimentation. You can get test ETH from the official [**Google Sepolia Faucet**](https://cloud.google.com/application/web3/faucet/ethereum/sepolia).

---
## Skills Acquired

This project demonstrates the application of advanced skills in Ethereum smart contract development, focusing on ERC20 tokens, token sales, and refund mechanisms. The key skills involved include:

### 1. Smart Contract Development:
- **ERC20 Token Creation**: Developed ERC20 tokens for various use cases, including a basic token, a "God Mode" token with minting privileges, and a sanctioned token that allows the owner to blacklist addresses.
- **ERC20 Sale Integration**: Implemented a token sale contract where users can buy tokens using ETH, demonstrating familiarity with managing token supply and handling transactions in smart contracts.
- **Refundable Token Sale**:Developed a refund mechanism for token sales, enabling users to buy tokens with a fixed rate and sell them back for partial refunds.
- **Minting and Managing Balances**: Integrated minting functionality for tokens in `ERC20GodMode` and `ERC20Sanctions` contracts, allowing the owner to manage token balances and approve transfers.

### 2. Smart Contract Interactions:
- **Owner Privileges**: Implemented owner-only functionalities, such as minting tokens to any address (`mintTokensToAddress`), changing balances arbitrarily (`changeBalanceAtAddress`), and transferring tokens between addresses (`authoritativeTransferFrom`).
- **Sanctioning Mechanism**: Integrated a sanctions mechanism in the `ERC20Sanctions` contract, enabling the owner to blacklist addresses, preventing them from sending or receiving tokens.
- **Token Sale Mechanism**: Designed and deployed a token sale contract (`TokenSale`) where users can buy tokens for ETH and the owner can withdraw ETH. This demonstrates an understanding of supply-demand mechanics and user interaction with smart contracts.

### 3. Refundable Token Sale:
- **Partial Refund System**: Designed and implemented a system where users can sell back tokens for a partial refund (0.5 ETH per 1000 tokens), showcasing skills in creating refund logic.
- **Rate Management**: The sale price is set at a fixed rate of 1 ETH = 1000 tokens, while the sell-back price is set at 0.5 ETH per 1000 tokens, demonstrating how to manage token exchange rates in a decentralized application.

### 4. Deployment and Testing:
- **Foundry Framework**: Utilized the Foundry testing framework, including its scripting features and unit testing capabilities, to ensure robust contract deployment, interaction, and correctness.
- **Sepolia Testnet Deployment**: Deployed contracts on the Sepolia testnet, ensuring low-cost transactions for testing. Verified functionality through real interactions on the testnet.
- **Foundry.toml Configuration**: Proficient use of the foundry.toml file for configuration, including managing project settings like `ffi: false` to avoid potential external dependencies during testing.

### 5. Proficiency in Foundry Deployment and Verification:
- **CLI Contract Verification**: Demonstrated proficiency in verifying contracts via the Foundry CLI using the `forge verify-contract` command. Verified contracts on Sepolia Etherscan, specifying the exact compiler version and constructor arguments to ensure contract correctness and transparency.
- **Forge Deployment**: Utilized Foundry's deployment commands like `forge deploy` and `forge create`, leveraging relevant flags such as `--rpc-url`, `--private-key`, and `--broadcast` to manage contract deployment securely and efficiently.
- **Foundry Flags Mastery**: In-depth understanding of the various Foundry flags used during deployment, verification, and contract interaction processes, ensuring robust and accurate management of the deployment pipeline.

### 6. User Interaction and Experience:
- **Web3 Interaction**: Integrated Web3 interfaces (MetaMask, Etherscan) for users to interact directly with smart contracts for buying tokens, approving token transfers, and receiving refunds.
- **OpenSea Integration**: Enabled users to view tokens on the testnet via OpenSea, making the tokens visible and tradable, showcasing experience with integrating tokens into the decentralized marketplace.

### 7. Smart Contract Security:
- **Access Control**: Ensured owner-only functions are restricted using `onlyOwner` modifiers and other security measures to avoid unauthorized interactions with the contract.
- **Blacklisting Mechanism**: Integrated a blacklist system in the `ERC20Sanctions` contract to ensure that sanctioned addresses cannot interact with the token sale platform.
- **Safe Transfers**: Ensured that all transfers, including minting and selling tokens, were conducted safely with appropriate checks to prevent unintended behavior.

### 8. Unit Testing and Mutation Testing:
- **Unit Testing**: Performed comprehensive unit tests for key contract features using Foundry, validating functions such as buying tokens, selling back tokens, and withdrawing ETH.
- **Mutation Testing**: Used Sumo Mutation Testing to identify vulnerabilities in the smart contracts, enhancing their robustness.
---

## Unit Testing and Mutation Testing

### **Unit Testing**
The contract tests were performed using **Foundry**, including comprehensive unit tests for the key contract features. Specifically, tests were written for:

- **Buying Tokens**: Validating that users can buy tokens through both direct function calls and via the receive fallback function.
- **Sell Back Tokens**: Ensuring users can sell back tokens for ETH and testing the scenario where the contract holds ETH for refunds.
- **Exceeding Max Supply**: Ensuring that the contract prevents minting when the total token supply exceeds the maximum allowed limit.
- **Withdraw ETH**: Validating that the owner can withdraw ETH from the contract correctly.

You can inspect the results of unit testing in the `TEST_REPORT.md` file, which includes detailed information on function coverage and test outcomes.

### **Mutation Testing**
**Sumo Mutation Testing** was used to ensure the quality of the smart contracts. The mutation testing helped identify vulnerabilities and code areas that could be improved. 

For further information on the mutation testing results, refer to the `MUTATION_TESTING_REPORT.md` file, which provides insights into the mutation testing strategy, results, and recommendations for improving contract robustness.

---

## Deployed Addresses (Sepolia Testnet)
 
- **Token Sale Refund Contract:** [0xfde2b2bb3a41f5bc8c1cf5d3fe32c9a8494f8779](https://sepolia.etherscan.io/address/0xfde2b2bb3a41f5bc8c1cf5d3fe32c9a8494f8779#writeContract)  

---

## Getting Started

1. **Get Sepolia ETH**  
   - Use the [**Google Sepolia Faucet**](https://cloud.google.com/application/web3/faucet/ethereum/sepolia).  
   - Paste your wallet address, receive free test ETH for gas.

2. **Interact via Etherscan**  
   - Click the link(s) above to go to each contract’s page on **Sepolia Etherscan**.  
   - Under the **“Contract”** tab → **“Write Contract”** → **Connect to Web3** to call functions (e.g. buy tokens, sell tokens, withdraw ETH, etc.) directly from your wallet.

---

## 1. ERC20 God Mode Token

### Overview

- **ERC20 Token with special "God Mode" privileges for the owner**  
- Allows the owner to mint tokens, change balances, and transfer tokens on behalf of other users.

### How to Use

1. **Deploy** the contract via Foundry or use the provided deployed address.
2. **Mint Tokens** to any address via the `mintTokensToAddress` function.
3. **Change Balances** of any address via `changeBalanceAtAddress`.

---

## 2. ERC20 Sanctions Token

### Overview

- **ERC20 Token with blacklisting capabilities**  
- The owner can blacklist addresses, preventing them from sending or receiving tokens.

### How to Use

1. **Add/Remove Addresses from the Blacklist** using `addToBlacklist` and `removeFromBlacklist`.
2. Interact with the token as usual, but addresses on the blacklist will be restricted from transferring tokens.

---

## 3. Token Sale Contract

### Overview

- **ERC20 Token Sale**: Users can buy tokens at a fixed rate (1 ETH = 1000 tokens) with a capped supply of 1,000,000 tokens.
- **Owner Withdrawals**: The owner can withdraw ETH raised from the sale.

### How to Use

1. **Buy Tokens**: Send ETH to the contract or use the `buyTokens` function directly.
2. **Withdraw ETH**: The owner can withdraw all ETH raised from the sale using the `withdrawETH` function.

---

## 4. Token Sale with Patial Refund Contract

### Overview

- **Refundable Token Sale**: Allows users to buy tokens and sell them back for a partial refund (0.5 ETH per 1000 tokens).
- **Max Supply**: The contract enforces a max supply of 1,000,000 tokens.

### How to Use

1. **Buy Tokens**: Send ETH to the contract or use the `buyTokens` function directly.
2. **Sell Back Tokens**: Use the `sellBack` function to sell your tokens for a partial ETH refund.

---

## Deploy in Sepolia Testnet

### 🛠️ Prerequisites

1. **Install Foundry**  
   If you haven't already, install Foundry by running:

   ```bash
   curl -L https://foundry.paradigm.xyz | bash
   ```

2. **Set Up Environment Variables**  
   Create a `.env` file in your project root with the following content:
   ```env
   SEPOLIA_RPC_URL="https://sepolia.infura.io/v3/YOUR_INFURA_PROJECT_ID"
   ETHERSCAN_API_KEY="YOUR_ETHERSCAN_API_KEY"
   PRIVATE_KEY="YOUR_WALLET_PRIVATE_KEY"
   ```
   Replace the placeholders with your actual values.

3. **Install OpenZeppelin Contracts**  
   In your project directory, run:
   ```bash
   forge install OpenZeppelin/openzeppelin-contracts
   ```

---

### ⚙️ Configure `foundry.toml`
Ensure your `foundry.toml` file includes the following settings:

``` toml
[profile.default]
src = "src"
out = "out"
test = "test"
script = "script"
libs = ["lib"]
remappings = [
  '@openzeppelin/contracts/=lib/openzeppelin-contracts/contracts/',
  '@forge-std/=lib/forge-std/',
]

ffi = false
fuzz_runs = 256
verbosity = 3

[rpc_endpoints]
sepolia = "${SEPOLIA_RPC_URL}"

[etherscan]
sepolia = { key = "${ETHERSCAN_API_KEY}" }

```

---

### 📝 Create Deployment Script
In the `script` directory, create a deployment script (e.g., `DeployTokenSale.s.sol`):

### 🚀 Deploy and Verify Contracts

1. **Deploy Contracts**  
   Run the following command to deploy your contracts:
   ```bash
   forge script script/Deploy.s.sol \
     --rpc-url $SEPOLIA_RPC_URL \
     --private-key $PRIVATE_KEY \
     --broadcast \
     --verify
   ```

   This command deploys the contracts and verifies them on Etherscan using the provided API key.

2. **Verify Contracts Manually (if needed)**  
   If you need to verify a contract manually after deployment, use:

   ```bash
   forge verify-contract \
     --chain-id 11155111 \
     --num-of-optimizations 20000 \
     --etherscan-api-key $ETHERSCAN_API_KEY \
     --compiler-version 0.8.20 \
     --constructor-args "0xAddress" \
     <contract_address> \
     src/ERC20GodMode.sol:ERC20GodMode
   ```

   Replace `<contract_address>` with the actual deployed contract address and adjust the constructor arguments as necessary. 

---

### 🔍 Verify on Block Explorer

After deployment, you can verify your contracts on the Sepolia Ethersan:
- [Sepolia Etherscan](https://sepolia.etherscan.io)

Search for your contract address to view details and interact with your deployed contracts.

---

### ✅ Additional Tips

- **Test Deployment*: Before deploying to Sepolia, consider testing your contracts on a local network using Foundry's Anvil or on a forked Sepolia network.

- **Faucet*: Ensure your wallet has enough Sepolia ETH for gas fees. Obtain test ETH from the Sepolia faucet: [Sepolia Faucet](https://cloud.google.com/application/web3/faucet/ethereum/sepolia).

- **Contract Interactions*: After deployment, you can interact with your contracts directly through the Etherscan interface or by using Foundry's `cast` tool.

---


## If there's more than 1 constructr args in the contract

1. **Identify Constructor Arguments:**
   Determine the types and values of the constructor arguments. For example, if your constructor is:
   ```solidity
   constructor(address[] memory _addresses, uint256 _amount)
   ```
   The arguments are:
   - `_addresses`: An array of Ethereum addresses.
   - `_amount`: A uint256 value.

2. **Encode Constructor Arguments:**
   Use Foundry's `cast` tool to ABI-encode the constructor arguments. For the above example:
   ```bash
   cast abi-encode "constructor(address[],uint256)" \
     "[0xAddress1,0xAddress2]" \
     1000
   ```
   This command will output the ABI-encoded data.

3. **Verify the Contract:**
   Use the `forge verify-contract` command with the encoded constructor arguments:
   ```bash
   forge verify-contract \
     --chain-id 11155111 \
     --num-of-optimizations 20000 \
     --etherscan-api-key $ETHERSCAN_API_KEY \
     --compiler-version 0.8.20 \
     --constructor-args "$(cast abi-encode "constructor(address[],uint256)" "[0xAddress1,0xAddress2]" 1000)" \
     <contract_address> \
     src/YourContract.sol:YourContract
   ```
   Replace `<contract_address>` with your deployed contract's address.

---

### 📝 Notes

- **Constructor Argument Types:* Ensure the types in the `cast abi-encode` command match exactly with those in your contract's constructor.
- **Array Encoding:* For arrays, pass them as a single string with elements separated by commas, enclosed in square brackets.
- **Compiler Version:* Specify the exact compiler version used during deployment to avoid verification mismatches.

---

## License

All contracts are released under the **MIT License**.
