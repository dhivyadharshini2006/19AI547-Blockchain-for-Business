# Experiment 6: Blockchain-Based Passwordless Authentication (Using Public-Private Key Cryptography)
## Name:Dhivya Dharshini B
## Reg no:212223240031
## Date:23/4/25


# Aim:
To implement a secure passwordless authentication system using public-private key cryptography on Ethereum. This prevents phishing and password leaks.

# Algorithm:
Step 1: 
User Registration
A user registers with their Ethereum public key (instead of a password).
Step 2: Login Process
When logging in, the user signs a random challenge message using their private key.
The smart contract verifies the signature using the user’s public key.
# Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract PasswordlessAuth {
    mapping(address => bool) public registeredUsers;

    event UserRegistered(address user);
    event UserAuthenticated(address user);

    function registerUser() public {
        require(!registeredUsers[msg.sender], "Already registered");
        registeredUsers[msg.sender] = true;
        emit UserRegistered(msg.sender);
    }

    function authenticate(bytes32 hash, uint8 v, bytes32 r, bytes32 s) public view returns (bool) {
        require(registeredUsers[msg.sender], "User not registered");
        address signer = ecrecover(hash, v, r, s);
        return signer == msg.sender;
    }
}
```

# Expected Output:
Users can register without a password.
![Screenshot 2025-04-28 144659](https://github.com/user-attachments/assets/9d77f1ec-88ab-4fae-881e-3adb3c032e47)



Users sign a challenge with their private key for authentication.
![image](https://github.com/user-attachments/assets/62c8063d-5df3-4047-ac17-3502684ceb15)



The smart contract verifies signatures to confirm identity.

![image](https://github.com/user-attachments/assets/040a7994-294e-42a4-99d5-3539df8cbfc2)



# High-Level Overview:
Eliminates password hacks & phishing attacks.
Uses Ethereum's built-in cryptographic functions.
Inspired by Web3 login solutions like MetaMask authentication.

# RESULT: 
Thus,Blockchain-Based Passwordless Authentication (Using Public-Private Key Cryptography) has been created and successfully executed.
