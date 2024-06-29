AccountCreation Smart Contract
Overview
The AccountCreation smart contract allows users to create accounts with age verification and unique names. It includes functionality for checking age, creating accounts, and retrieving user details. This contract is implemented in Solidity and is intended to run on the Ethereum blockchain.

Prerequisites
Solidity compiler version 0.8.25 or later.
An Ethereum wallet/address to interact with the contract.
Contract Structure
User Struct
The contract defines a User struct with the following properties:

age: A uint representing the user's age.
name: A string representing the user's name.
isAgeVerified: A bool indicating if the user's age has been verified.
Mappings
The contract uses two mappings:

users: Maps an address to a User struct, storing user details.
nameExists: Maps a string (name) to a bool, indicating if a name is already taken.
Functions
checkAge
solidity
Copy code
function checkAge(uint _age) public
Description: Verifies if the user's age is greater than 18.
Parameters: _age - The age to be verified.
Requirements: The user must be older than 18 to pass the check.
Effects: Sets the user's age and marks the age as verified.
createAccount
solidity
Copy code
function createAccount(string memory _name) public
Description: Creates an account with a unique name for the user.
Parameters: _name - The name to be assigned to the user's account.
Requirements:
The user's age must be verified.
The name must not be already taken.
Effects: Assigns the name to the user and marks the name as taken.
verifyAgeCheck
solidity
Copy code
function verifyAgeCheck() public view returns (string memory)
Description: Checks if the user's age has been verified.
Returns: "Legal" if the age is verified, otherwise "Not Legal".
getUser
solidity
Copy code
function getUser() public view returns (uint, string memory, bool)
Description: Retrieves the details of the user.
Returns: The user's age, name, and age verification status.
Example Usage
Check Age:

solidity
Copy code
contractInstance.checkAge(21);
Create Account:

solidity
Copy code
contractInstance.createAccount("Alice");
Verify Age Check:

solidity
Copy code
string memory status = contractInstance.verifyAgeCheck();
Get User Details:

solidity
Copy code
(uint age, string memory name, bool isAgeVerified) = contractInstance.getUser();
Error Handling
The checkAge function uses a require statement to ensure the user is older than 18.
The createAccount function uses a revert statement to prevent account creation if the user's age is not verified and a require statement to ensure the name is unique.
License
This project is licensed under the MIT License.
