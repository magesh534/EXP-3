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
![Screenshot 2025-04-26 094820](https://github.com/user-attachments/assets/bcddeb3a-93e5-40fa-9b93-48867ea18dae)

Transaction
![Screenshot 2025-04-26 094844](https://github.com/user-attachments/assets/4e198bae-6435-4881-a7b7-b714531edf87)

Verification
![Screenshot 2025-04-26 094855](https://github.com/user-attachments/assets/f4f263fe-c7b6-4dd5-a52e-bb53d77a2b7b)



# RESULT : 
A smart contract that tracks the supply chain of luxury goods and ensuring authenticity is successfully executed.


