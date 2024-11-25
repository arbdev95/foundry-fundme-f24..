FundMe
FundMe is a decentralized crowdfunding smart contract built using Solidity and Foundry. The project demonstrates how to accept ETH contributions, track funding from multiple users, and withdraw funds securely. It leverages Chainlink's price feed oracles to ensure users meet a minimum contribution amount in USD.

Features
ETH Contributions: Accepts ETH from multiple users.
Minimum Contribution: Ensures contributions meet a minimum USD threshold using Chainlink price feeds.
Secure Withdrawals: Allows only the owner of the contract to withdraw funds.
Efficient Operations: Implements a gas-optimized cheaperWithdraw function for scalability.
Prerequisites
Ensure you have the following installed:

Foundry for testing and deploying.
Node.js and npm for setting up dependencies.
An Ethereum-compatible wallet for deployment.
Access to an Ethereum test network or local blockchain.
Installation
Clone the repository:

bash
Copy code
git clone git@github.com:<your-username>/FundMe.git
cd FundMe
Install Foundry dependencies:

bash
Copy code
forge install
Set up Chainlink price feed library:

bash
Copy code
git submodule update --init --recursive
Usage
1. Build the Project
Compile the Solidity contracts:

bash
Copy code
forge build
2. Run Tests
Execute all unit tests to ensure functionality:

bash
Copy code
forge test
3. Deploy the Contract
You can deploy the contract locally or to a testnet. Update the deployment script in script/DeployFundMe.s.sol with the appropriate configurations:

bash
Copy code
forge script script/DeployFundMe.s.sol --rpc-url <YOUR_RPC_URL> --private-key <YOUR_PRIVATE_KEY> --broadcast
4. Interact with the Contract
Once deployed, interact with the contract using Foundry's console:

bash
Copy code
forge console --rpc-url <YOUR_RPC_URL>
Project Structure
src/: Contains the Solidity smart contracts.
FundMe.sol: Core crowdfunding logic.
PriceConverter.sol: Utility library for ETH-to-USD conversions using Chainlink.
script/: Deployment scripts.
DeployFundMe.s.sol: Script for deploying the FundMe contract.
test/: Contains unit and integration tests.
Key Components
FundMe Contract
Accepts ETH contributions and validates them against a minimum USD threshold.
Implements secure withdrawal mechanisms using access control.
HelperConfig
Dynamically configures Chainlink price feed addresses based on the target network.
Example Contribution
Call the fund() function to send ETH:

bash
Copy code
cast send <CONTRACT_ADDRESS> "fund()" --value <ETH_AMOUNT>
Verify funding amounts using the getter function:

bash
Copy code
cast call <CONTRACT_ADDRESS> "getAddressToAmountFunded(address)" <YOUR_ADDRESS>
To-Do
Add support for more price feed networks.
Implement events for improved transparency.
Optimize the fallback function.
License
This project is licensed under the MIT License.