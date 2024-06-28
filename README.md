
# Solidity Token 
This Solidity Program is a ERC-20 token contract named: **SolidityToken**. In this Solidity Program we also demonstrates the use of **OpenZeppelin library** which provides us pre-defined smart contracts and helps us for creating a burnable ERC20 token with ownership capabilities.
## Description
The contract, "SolidityToken", inherits smart contracts from OpenZeppelin which are ERC20, ERC20Burnable, Ownable. It includes functions for minting new tokens, burning tokens, and transferring tokens. Also we have initiated three events TokensMinted, TokensBurned, TokensTransferred which are used for Event Logging means all the events whether the tokens are minted ,the tokens are burned and if the tokens are transferred from our owner address to another address will be logged(recorded).  
## Getting Started
### Executing program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, follow these steps:

1. **Create a New File**:
   
   a. Click on the "+" icon in the left-hand sidebar.
   
   b. Save the file with a `.sol` extension (e.g., `SolidityToken.sol`).
   
2. **Copy and Paste the Code**:
   
   a. Copy and paste the code given below:
   ```solidity
   // SPDX-License-Identifier: MIT
   pragma solidity ^0.8.25;

   import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
   import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
   import "@openzeppelin/contracts/access/Ownable.sol";

   contract SolidityToken is ERC20, ERC20Burnable, Ownable {
    event TokensMinted(address to, uint amount);
    event TokensBurned(address  from, uint amount);
    event TokensTransferred(address  from, address to, uint amount);

    constructor(uint initialSupply) ERC20("Solidity", "SOL")
    Ownable(msg.sender)
     {
        _mint(msg.sender, initialSupply);
    }

    function mint(address to, uint amount) public onlyOwner {
        _mint(to, amount);
        emit TokensMinted(to, amount);
    }

    function burnToken(uint256 amount) public {
        _burn(msg.sender, amount);
        emit TokensBurned(msg.sender, amount);
    }

    function transferToken(address to, uint256 amount) public returns (bool) {
        _transfer(msg.sender, to, amount);
        emit TokensTransferred(msg.sender, to, amount);
        return true;
    }
   }
   ```
3. **Compile the Code**: Click on the "Solidity Compiler" tab in the left-hand sidebar. Ensure the "Compiler" option is set to "0.8.25" (or another compatible version). Click on the "Compile SolidityToken.sol" button.
4.  **Deploy the Contract**: Click on the "Deploy & Run Transactions" tab in the left-hand sidebar. Enter the initial supply in the deployment input box. Click on the "Deploy" button.
5.  **Interact with the Contract**: After deployment, we can interact with the contract using the provided functions that are mint, burnToken, transferToken.

## Authors
Metacrafter UDAY CHOPRA ---->
[UDAY CHOPRA](https://www.linkedin.com/in/uday-chopra-86701b2b0/)

## License

This project is licensed under the MIT License.
