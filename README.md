# MyToken Contract

This Solidity contract implements a basic ERC-20 like token with minting and burning functionalities.

## Contract Overview

The contract includes:
- Public variables for the token name, abbreviation, and total supply.
- A mapping to store the balances of each address.
- Functions to mint and burn tokens.

## Contract Code

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.7;

contract MyToken {

    // public variables here
    string public tokenName = "Vcoin";
    string public tokenAbbrv = "coin";
    uint public totalSupply = 0;

    // mapping variable here
    mapping(address => uint) public balances;

    // mint function
    function mint(address _address, uint _value) public {
        totalSupply += _value;
        balances[_address] += _value;
    }

    // burn function
    function burn(address _address, uint _value) public {
        if (balances[_address] >= _value) {
            totalSupply -= _value;
            balances[_address] -= _value;
        }
    }
}
```

## Usage

Deploy the contract to an Ethereum-compatible blockchain and interact with the functions as follows:

### Mint Tokens

```javascript
// Mint 100 tokens to a specific address
await MyTokenContract.mint('0xYourAddressHere', 100);
console.log(await MyTokenContract.balances('0xYourAddressHere')); // 100
```

### Burn Tokens

```javascript
// Burn 50 tokens from a specific address
await MyTokenContract.burn('0xYourAddressHere', 50);
console.log(await MyTokenContract.balances('0xYourAddressHere')); // 50
```

## License

This project is licensed under the MIT License.
