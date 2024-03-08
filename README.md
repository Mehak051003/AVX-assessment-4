# Degen Token (ERC-20): Unlocking the Future of Gaming

This Contract Creates ERC-20 Fungible tokens that can be transfered,minted and used to redeem rewards.

## Description

This Contract is deployed on the FUJI testnet and is used to create fungible tokens that can be used to redeem rewards. The contract makes use of the ERC-20 standard and is deployed on the Fuji network. Provides the following functionality:

Minting of tokens
Transfer of tokens
Redeeming of tokens
Burning of tokens
Checking of balances

## Getting Started

### Executing program

Executing program To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (eg., HelloWorld.sol). Copy and paste the following code into the file:

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18; 

contract Degen {

    uint256 public totalSupply;
    address public owner;
    string public name = "DEGEN";
    string public symbol = "DGN";
    uint8 public decimals = 18;

    constructor() {
        owner = msg.sender;
    }

    mapping(address => uint256) public balances;

    // Mint function
    function mint(address to, uint256 amount) public {
        require(msg.sender == owner, "Only the contract owner can mint tokens.");
        require(amount > 0, "Amount must be greater than 0.");

        balances[to] += amount;
        totalSupply += amount;
    }

    // Burn function
    function burn(address from, uint256 amount) public {
        require(amount <= balances[from], "Amount exceeds balance.");

        balances[from] -= amount;
        totalSupply -= amount;
    }

    // Transfer function
    function transfer(address to, uint256 amount) public {
        require(amount <= balances[msg.sender], "Amount exceeds balance.");
        require(to != address(0), "Cannot transfer to the zero address.");

        balances[msg.sender] -= amount;
        balances[to] += amount;
    }

    // Redeem function
    function redeem(address to, uint256 amount, uint256 gameItem) public { 
        require(amount <= balances[to], "Amount exceeds balance");

        if (gameItem == 1) {
            require(amount >= 50, "Insufficient tokens for Game Item 1");
            burn(to, amount);
        } else if (gameItem == 2) {
            require(amount >= 100, "Insufficient tokens for Game Item 2");
            burn(to, amount);
        } else if (gameItem == 3) {
            require(amount>=200, "Insufficient tokens for Game Item 3");
            burn(to, amount);
        } else {
            revert("Invalid game item");
        }
    } 
}
```
To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.9" (or another compatible version), and then click on the "Compile HelloWorld.sol" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "DegenToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the sayHello function. Click on the "DegenToken" contract in the left-hand sidebar, and then click on multiple functions available. Finally, click on the "transact" button to execute the function and retrieve the appropriate messages.

# Proof of work as the Fuji Contract detail

Contract Address is provided as Application id as well
![alt text](image.png)


## Authors

Mehak Thakur [mehakthakur051003@gmail.com]


## License

This project is licensed under the MIT License - see the LICENSE.md file for details
