# ENCODE WEEK ONE ASSIGNEMENT - REPORT on HelloWorld contract
The etherscan contract adress : https://sepolia.etherscan.io/address/0x9548d41a9a13b53222cad9d31e88df3df9132406;

The contract was deployed to sepolia ethereum testnet network the functions in this contract are : 

## helloWorld(): 
This function doe snot need arguments and returns a string "Hello World".

## setText: 
This function sets a new value for the text variable that is private to the contract. You need to provide newText argument is declared as type string 
calldata. This means that the input argument will be stored in the calldata area of memory during the function execution it will be lost after execution. However the 
data will still be available in the transaction receipt, which is stored on the blockchain. Therefore, if the data is required to be stored permanently, it can be 
stored on the blockchain in the transaction receipt, or it must be written to storage within the contract.

0x31a197e967f29f24475a5d959183786f0f4e8651b2a1420bbaee21864dce87f5 nothing to declare here everything works, anyone can intercat with this function.

The function can read the value of newText without copying it to another location in memory.
string memory, you need to be careful about the amount of memory that you use. Large strings can consume a significant amount of memory, which can cause the contract 
to run out of gas and fail. After deploying the contract we can view on tetherscan the max gas limit that will cause the contract to fail. 

## transferOwnership: 
This function transfer contract ownership to a new given address as an argument. This function works in parallel with the modifier onlyOwner() which 
checks if the caller of the function is the current owner of the contract. 
If the caller adress does not match the owner adress, the transaction will fail and the contract will revert and will trow an error message. Revert will stop the 
execution of the function the caller will not spend the full gasprice for the contract.


0xe2e32fad18f8a260901c6a83102556fb944954d53674e0f6d09d5fc1ace76009 this transaction succeeded as the owner was transfering the ownership and the modifer could check if 
the caller was the owner. 

0x99f06b99f71df5f0075adc1f1f681e53d9712ad906105c2d70df90a527fa780d this transaction revert the previous owner  tried to get back ownership. the modifier sent "Caller 
is not the owner".

An important issue regarding the transferownership function if the _; is put above the require the contract ownership could be lost by allowing the ownership of the 
contract to be transferred to anyone. The require thus is useless. 


In conclusion the helloWorld contract is simple demonstration of how to deploy and interact with a smart contract, it can be used to be look further into contracts 
requiring ownership transfer functionality.
