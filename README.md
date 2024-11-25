##About

FundMe
FundMe is a smart contract built on Ethereum using Foundry. It is a decentralized crowdfunding platform that enables users to securely send ETH contributions, ensuring that contributions meet a minimum USD value. The project integrates Chainlink price feeds to fetch live ETH/USD prices, providing accurate and dynamic value calculations.

##Features

- Decentralized Crowdfunding: Accepts ETH from multiple contributors.
-Chainlink Integration: Uses Chainlink oracles to validate contributions against a minimum USD threshold.
- Secure Fund Management: Only the owner can withdraw funds, ensuring safety and access control.
- Gas Optimization: Implements a cheaperWithdraw function for efficient handling of contributor data.

##Prerequisites

To use this project, ensure you have:

- Foundry installed for development, testing, and deployment.
- Node.js and npm for managing dependencies.
- Access to an Ethereum testnet or local blockchain environment like Anvil.
- A wallet and private key for deployment.

##installation

-Clone the repository:

git clone git@github.com:<your-username>/FundMe.git  

-Install Foundry dependencies:

forge install

-Initialize Chainlink submodule:

git submodule update --init --recursive  

##Project Structure

- src/: Solidity smart contracts.
   -FundMe.sol: The main crowdfunding contract.
    -PriceConverter.sol: A library for ETH-to-USD conversion using Chainlink price feeds.
- script/: Deployment scripts for deploying contracts on local and test networks.
    -DeployFundMe.s.sol: The deployment script for the FundMe contract.
- test/: Unit tests and integration tests for contract functionality.

##Usage

1. Compile the Contracts
Build the smart contracts using Foundry:
'''Solidity
forge build
'''  

2. Run Tests
Test the contract functionality with Foundry's testing framework:
'''Solidity
forge test 
''''

3. Deploy the Contract
Deploy the contract to a test network or local blockchain. Update the deployment script (script/DeployFundMe.s.sol) with the appropriate configurations:
'''Solidity
forge script script/DeployFundMe.s.sol --rpc-url <YOUR_RPC_URL> --private-key <YOUR_PRIVATE_KEY> --broadcast
'''

4. Interact with the Contract
Use Foundry's console to interact with the deployed contract:
'''Solidity
forge console --rpc-url <YOUR_RPC_URL>  
'''

##Contract Details

FundMe Contract

    -Purpose: Allows users to send ETH contributions, requiring them to meet a specified minimum USD value.
Key Functions:
    -fund(): Accepts ETH contributions.

    -withdraw(): Enables the contract owner to withdraw all funds.

    -cheaperWithdraw(): Optimized version for gas efficiency.

    -getAddressToAmountFunded(address): Fetches the contribution amount of a specific address.
    
    -getFunder(uint256): Retrieves a contributor's address by index.

    HelperConfig

    -Dynamically configures the Chainlink price feed addresses based on the target network (e.g., Sepolia, Mainnet, Anvil).