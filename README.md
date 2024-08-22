MyToken Contract
This Solidity program is a straightforward example of a token contract. It showcases the creation of a simple token with basic features for minting and burning tokens. The goal of this contract is to provide a foundational example for those interested in learning about ERC20-like token creation and smart contract development on the Ethereum blockchain.

Description
The program defines a contract named MyToken, written in Solidity, a language designed for creating smart contracts on the Ethereum blockchain. The contract includes functionalities to mint new tokens, burn existing tokens, and maintain records of the total supply and individual balances. Additionally, it incorporates basic security features like access control and event logging. This contract serves as an introductory example for creating and managing tokens and can be expanded to support more advanced use cases.

Getting Started
Running the Program
To execute this program, you can use Remix, an online IDE for Solidity. Below is a step-by-step guide to get you started:

Access Remix:
Navigate to the Remix website at Remix IDE.
Create a New File:
Click the "+" icon in the left-hand sidebar to create a new file.
Save the file with a .sol extension (e.g., MyToken.sol).
Paste the Code:
Copy and paste the following code into the file:

solidity
Copy code
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

import "@openzeppelin/contracts/access/Ownable.sol";

contract MyToken is Ownable {
    // Public variables to store token details
    string public tokenName;
    string public tokenAbbrev;
    uint public totalSupply;

    // Mapping to store balances of addresses
    mapping(address => uint) public balances;

    // Events to log minting and burning actions
    event Mint(address indexed to, uint value);
    event Burn(address indexed from, uint value);

    // Constructor to initialize the token details
    constructor() {
        tokenName = "META";
        tokenAbbrev = "MTA";
        totalSupply = 0;
    }

    // Function to mint new tokens
    function mint(address _address, uint _value) public onlyOwner {
        require(_address != address(0), "Cannot mint to the zero address");
        totalSupply += _value;
        balances[_address] += _value;
        emit Mint(_address, _value);
    }

    // Function to burn tokens
    function burn(address _address, uint _value) public onlyOwner {
        require(_address != address(0), "Cannot burn from the zero address");
        require(balances[_address] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_address] -= _value;
        emit Burn(_address, _value);
    }

    // Optional: Receive function to accept ETH
    receive() external payable {}

    // Optional: Fallback function to handle any fallback calls
    fallback() external payable {}
}
Compile the Code:
Click on the "Solidity Compiler" tab in the left-hand sidebar.
Ensure the "Compiler" option is set to version 0.8.18 (or another compatible version).
Click the "Compile MyToken.sol" button to compile the code.
Deploy the Contract:
Go to the "Deploy & Run Transactions" tab in the left-hand sidebar.
Select the MyToken contract from the dropdown menu.
Click the "Deploy" button to deploy the contract.
Interact with the Contract:
Once deployed, you can interact with the contract through the Remix interface.
Use the mint function to create new tokens, specifying an address and the amount to mint.
Use the burn function to destroy tokens, specifying an address and the amount to burn.
Authors
Akash - akash50127@gmail.com

License
This project is licensed under the MIT License - see the LICENSE.md file for details.







