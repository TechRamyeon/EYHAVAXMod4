
# DegenToken Smart Contract

## Overview
DegenToken is an ERC20 token implemented in Solidity using OpenZeppelin libraries. The contract introduces a unique feature: the ability for users to purchase heroes with tokens and track ownership. This README provides an overview of the contract's functionality and instructions for deployment and usage.

## Features
1. **ERC20 Token Standard**: Implements the standard ERC20 token interface for fungible tokens.
2. **Hero Marketplace**: Allows users to purchase heroes using the DegenToken (`DGN`).
3. **Hero Ownership Tracking**: Tracks ownership of heroes on a per-user basis.
4. **Minting and Burning**: Includes functions for the owner to mint tokens and for users to burn their tokens.
5. **Custom Transfer Logic**: Overrides the `transfer` function for token transfers.

## Contract Details

- **Token Name**: Degen
- **Token Symbol**: DGN
- **Token Decimals**: 18 (default for ERC20 tokens)

### Hero Prices
The following hero types are available for purchase:
- **Shouyue**: 2,500 `DGN`
- **Guiguzi**: 7,000 `DGN`
- **Liu Bang**: 12,000 `DGN`
- **Shangguan**: 1,200 `DGN`

## Deployment

### Prerequisites
1. **Node.js**: Install [Node.js](https://nodejs.org/) and [npm](https://www.npmjs.com/).
2. **Hardhat**: Install Hardhat for compiling and deploying the contract.
3. **Solidity Compiler**: Ensure Solidity version `^0.8.18` is compatible.

### Steps
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Compile the contract:
   ```bash
   npx hardhat compile
   ```
4. Deploy the contract:
   ```bash
   npx hardhat run scripts/deploy.js --network <network-name>
   ```

## Functions

### Token Operations
- **`mint(address to, uint256 amount)`**
  - Mints new tokens to the specified address.
  - Only callable by the contract owner.
- **`burn(uint256 amount)`**
  - Allows the sender to burn a specified amount of their tokens.
- **`transfer(address to, uint256 amount)`**
  - Transfers tokens from the sender to the specified address.

### Hero Operations
- **`buyHer0(string memory heroType)`**
  - Purchases a hero by spending the specified amount of tokens.
  - Increases the count of owned heroes for the buyer.
- **`getOwnedHero(address owner, string memory heroType) public view returns (uint256)`**
  - Returns the count of heroes owned by a specific user.

## Events
- **`HeroPurchased(address indexed buyer, string heroType)`**
  - Emitted when a user successfully purchases a hero.

## Security Notes
1. The contract uses OpenZeppelin's `Ownable` for ownership management.
2. Ensure proper access control for minting tokens.
3. Validate inputs in all user-facing functions to prevent misuse.

## License
This project is licensed under the [MIT License](https://opensource.org/licenses/MIT). 
