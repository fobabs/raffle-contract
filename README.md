# Raffle Smart Contract  

A decentralized raffle smart contract implemented in Solidity, using Chainlink VRF v2.5 for provable randomness. Built with [Foundry](https://book.getfoundry.sh/) to ensure a modern development experience with seamless testing and deployment.

---

## Features  

- **Randomized Winner Selection:** Integrates Chainlink VRF v2.5 to ensure cryptographically secure randomness.  
- **Automated State Transitions:** Employs an interval-based upkeep mechanism for automated raffle management.  
- **Gas-Optimized Design:** Implements Solidity best practices for efficient execution.  
- **Extensible Architecture:** Modular code organization allows for easy maintenance and enhancements.  
- **Comprehensive Test Suite:** Includes unit and integration tests for robust validation.  

## Prerequisites  

- **Foundry:** Install Foundry by following the [installation guide](https://book.getfoundry.sh/getting-started/installation.html).
- **A Chainlink Subscription:** Necessary for accessing the Chainlink VRF service.  

## Installation  

**NOTE:** A Makefile is used to streamline and standardize development workflows by defining a set of commands to build, test, deploy, and manage the project. To execute a command using `make`, you need to ensure you have `make` installed.

1. **Clone the Repository:**  
   ```bash
   git clone https://github.com/fobabs/raffle-contract.git
   cd raffle-contract
   ```

2. **Install Dependencies:**  
   ```bash
   make install
   ```

3. **Configure Environment Variables:**  
   Create a `.env` file in the root directory and include the following values:  
   ```env
   SEPOLIA_RPC_URL=<SEPOLIA_RPC_URL>
   ETHERSCAN_API_KEY=<ETHERSCAN_API_KEY>
   ```

4. **Compile the Contract:**  
   ```bash
   make build
   ```

## Contract Structure

### Function Highlights  

- **`enterRaffle()`**  
  Allows participants to join the raffle by paying the required `entranceFee`.  

- **`checkUpkeep(bytes memory)`**  
  Determines if the contract is ready for winner selection based on time interval, contract state, and balance.  

- **`performUpkeep(bytes calldata)`**  
  Triggers the process to request a random number from Chainlink VRF.  

- **`fulfillRandomWords(uint256, uint256[] calldata)`**  
  Handles the randomness callback from Chainlink VRF to determine the winner.  

- **Getter Functions:** Provide insights into contract state (`getRaffleState`, `getEntranceFee`, `getRecentWinner`, etc.).  

## Testing  

Run the comprehensive suite of unit and integration tests with Foundry:  
```bash
make test
```

- **Unit Tests:** Validate individual functions in isolation.  
- **Integration Tests:** Ensure end-to-end behavior, including Chainlink VRF integration (mocked in testing).  

## Deployment  

Deploy the contract to sepolia. A script has been written for you, just execute the following:  
```bash
make deploy-sepolia
```
NOTE: Pay attention to this `--account default` in the `make deploy-sepolia` script and replace `default` with whatever keyword you used to save your private key.
