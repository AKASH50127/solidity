// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract MyToken {
    // Public variables to store token details
    string public tokenName = "Akash kumar";
    string public tokenAbbrev = "AK";
    uint public totalSupply = 0;

    // Mapping to store balances of addresses
    mapping(address => uint) public balances;

    // Function to mint new tokens
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // Function to burn tokens
    function burn(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_address] -= _value;
    }
}
