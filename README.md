
# **FundMe**

**FundMe** is a cutting-edge smart contract project built on Ethereum using the **[Foundry](https://github.com/foundry-rs/foundry)** framework. It provides a decentralized crowdfunding platform that utilizes **Chainlink Price Feeds** to ensure contributions meet a minimum USD threshold. This ensures fairness, security, and accurate valuation for all transactions.

---

## **FEATURES**

- **Decentralized Crowdfunding**: Securely accepts ETH contributions from users.
- **Real-Time Price Validation**: Integrates **Chainlink Oracles** to fetch live ETH/USD prices.
- **Owner-Only Withdrawals**: Only the contract owner can withdraw the funds, ensuring robust access control.
- **Gas Efficiency**: Implements a `cheaperWithdraw` function for optimized gas usage when managing contributors.
- **Seamless Fallback and Receive**: Automatically handles Ether transfers via fallback and receive functions.

---

## **PREREQUISITES**

Before working with this project, ensure the following are installed:

- **[Foundry](https://github.com/foundry-rs/foundry)** for development, testing, and deployment.
- **[Node.js](https://nodejs.org/)** and **[npm](https://www.npmjs.com/)** for managing additional dependencies.
- Access to an Ethereum network (local, testnet, or mainnet) or a local blockchain emulator like **[Anvil](https://book.getfoundry.sh/anvil/)**.
- A wallet and private key for deployment.

---

## **INSTALLATION**

Follow these steps to set up the project locally:

1. **Clone the Repository**:
   ```bash
   git clone git@github.com:<your-username>/FundMe.git
   cd FundMe
   ```

2. **Install Foundry Dependencies**:
   ```bash
   forge install
   ```

3. **Initialize Chainlink Submodule**:
   ```bash
   git submodule update --init --recursive
   ```

---

## **PROJECT STRUCTURE**

### **`src/`**
- **`FundMe.sol`**: The main smart contract for the crowdfunding platform.
- **`PriceConverter.sol`**: A utility library for converting ETH to USD using Chainlink price feeds.

### **`script/`**
- **`DeployFundMe.s.sol`**: A deployment script for deploying the `FundMe` contract.

### **`test/`**
- Contains unit and integration tests to ensure contract functionality.

---

## **USAGE**

### **1. Compile the Contracts**
Build the smart contracts using Foundry:
```bash
forge build
```

### **2. Run Tests**
Verify the functionality of the contracts by running tests:
```bash
forge test
```

### **3. Deploy the Contracts**
Deploy the contracts to a testnet or local blockchain:
```bash
forge script script/DeployFundMe.s.sol --rpc-url <RPC_URL> --private-key <PRIVATE_KEY> --broadcast
```

### **4. Interact with the Contract**
Interact with the deployed contract using Foundry's console:
```bash
forge console --rpc-url <RPC_URL>
```

---

## **CONTRACT DETAILS**

### **`FundMe`**
- **Purpose**: Manages ETH contributions, ensuring they meet a minimum USD value.
- **Key Functions**:
  - **`fund()`**: Accepts ETH contributions.
  - **`withdraw()`**: Allows the contract owner to withdraw all funds.
  - **`cheaperWithdraw()`**: An optimized withdrawal method for reduced gas usage.
  - **`getAddressToAmountFunded(address)`**: Retrieves the contribution amount of a specific address.
  - **`getFunder(uint256)`**: Returns the contributor’s address by index.

### **`HelperConfig`**
- Dynamically configures Chainlink price feed addresses based on the target network (e.g., Sepolia, Mainnet, or Anvil).

---

## **EXAMPLE USAGE**

1. **Fund the Contract**:
   Send ETH to the contract using the `fund()` function:
   ```bash
   cast send <CONTRACT_ADDRESS> "fund()" --value <ETH_AMOUNT>
   ```

2. **Check Contributions**:
   Retrieve a specific user's contribution:
   ```bash
   cast call <CONTRACT_ADDRESS> "getAddressToAmountFunded(address)" <USER_ADDRESS>
   ```

3. **Withdraw Funds**:
   Withdraw all funds as the contract owner:
   ```bash
   cast send <CONTRACT_ADDRESS> "withdraw()"
   ```

---

## **TESTING**

The project includes robust tests to validate contract functionality:

```bash
forge test
```

- **Gas Reports**:
  Use Foundry's built-in gas reporting tools to identify optimization opportunities.

---

## **SUPPORTED NETWORKS**

This project supports deployment on:

- **Sepolia Testnet**
- **Ethereum Mainnet**
- **Local Development Chains (e.g., Anvil)**

Ensure the deployment script includes the correct price feed address for your target network.

---

## **FUTURE IMPROVEMENTS**

- **Multi-Token Support**: Enable contributions in other tokens like DAI or USDC.
- **Event Logs**: Add events for key actions (e.g., funding and withdrawals).
- **User-Friendly Interface**: Build a web-based UI for easier interaction with the smart contract.
- **Automated Testing**: Incorporate CI/CD for testing and deployment pipelines.

---

## **LICENSE**

This project is open-sourced under the **[MIT License](LICENSE)**.

---

## **ACKNOWLEDGMENTS**

Special thanks to:
- **[Chainlink](https://chain.link/)** for providing reliable price feed oracles.
- **[Foundry](https://github.com/foundry-rs/foundry)** for an exceptional Solidity development framework.
- The Solidity developer community for guidance and inspiration.

---

## **CONTACT**

For questions or collaboration:
- **GitHub**: [Your Username](https://github.com/<your-username>)
- **Email**: your-email@example.com
