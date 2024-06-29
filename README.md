
ETH_AVAX_PROOF-Intermediate_EVM_Course
MODULE - 1 FINAL PROJECT
This project demonstrates error handling methods in Solidity through the implementation of an account creation system. The contract includes examples of using require, assert, and revert statements.

CODE EXPLANATION:
solidity
Copy code
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.25;

contract AccountCreation  {

    struct User  {
        uint age;
        string name;
        bool isAgeVerified;
    }

    mapping(address => User) private users;
    mapping(string => bool) private nameExists;

     // Function to check age using require statement
    function checkAge(uint _age) public  {
        require(_age > 18, "You must be older than 18 to create an account");
        users[msg.sender].age = _age;
        users[msg.sender].isAgeVerified = true;
    }

     // Function to create an account using revert statement
    function createAccount(string memory _name) public  {
        if (users[msg.sender].isAgeVerified == false) {
            revert("You are not legal to create an account");
        }
        require(nameExists[_name] == false, "Name is already taken");
        users[msg.sender].name = _name;
        nameExists[_name] = true;
    }

     // Function to verify that the user has checked their age using assert statement
    function verifyAgeCheck() public view returns (string memory) {
        if(users[msg.sender].isAgeVerified == true){
            return("Legal");
        } else{
            return("Not Legal");
        }
    }

     // Function to get user details
    function getUser() public view returns (uint, string memory, bool) {
        User memory user = users[msg.sender];
        return (user.age, user.name, user.isAgeVerified);
    } 
}
require(_age > 18, "You must be older than 18 to create an account");
This line is a condition that checks if the user's age is greater than 18. If it's not, the function will revert the transaction and display the error message "You must be older than 18 to create an account".

users[msg.sender].age = _age;: This line sets the user's age.
users[msg.sender].isAgeVerified = true;: This line marks the user's age as verified.
if (users[msg.sender].isAgeVerified == false) { revert("You are not legal to create an account"); }
This line checks if the user's age has been verified. If it hasn't, the function will revert the transaction and display the error message "You are not legal to create an account".

require(nameExists[_name] == false, "Name is already taken");: This line ensures the name is unique.
users[msg.sender].name = _name;: This line assigns the name to the user.
nameExists[_name] = true;: This line marks the name as taken.
assert(users[msg.sender].isAgeVerified == true);
This line is an assertion that checks if the user's age has been verified. If not, it will throw an exception.

return("Legal");: This line returns "Legal" if the age is verified.
return("Not Legal");: This line returns "Not Legal" if the age is not verified.
(uint age, string memory name, bool isAgeVerified) = contractInstance.getUser();
This function call retrieves the user's details: age, name, and age verification status.

LICENSE
This project is licensed under the MIT License.
