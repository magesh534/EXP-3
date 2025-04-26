# Ex No: 3 - Supply Chain Transparency for Luxury Goods
# Name : Magesh V
# Reg No: 212222040092
# Date : 26-04-2025
# Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
# Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
# Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.


Ownership is transferred at every checkpoint.


Buyers can check the authenticity before purchasing.


# High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.
# output:
Register
![Screenshot 2025-04-26 094820](https://github.com/user-attachments/assets/f7f0f42e-2a21-4ecb-9015-eec65ebdebd2)
Transaction
![Screenshot 2025-04-26 094844](https://github.com/user-attachments/assets/1a1e4651-615e-478d-a52b-b10c30614221)
Verification
![Screenshot 2025-04-26 094855](https://github.com/user-attachments/assets/273c55a0-6adb-4605-8e9b-48f02b0ce137)


# RESULT : 

A smart contract that tracks the supply chain of luxury goods and ensuring authenticity is successfully executed.

