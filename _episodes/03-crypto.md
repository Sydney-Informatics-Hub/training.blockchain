---
title: "Write your own Crypto"
teaching: 10
exercises: 15
questions:
- "How do I write my own cryptocurrency?"
objectives:
- "Write a cryptocurrency in Solidity"
- "Deploy the contract to the network"
keypoints:
- "A cryptocurrency is a contract"
- "Contract transactions are verified on the network"
---
This episode shows you how to write your own cryptocurrency contract using the Solidity programming language. We can then launch this coin/contract to the Etherum (or test) network.


# Writing your own cryptocurrency

Let's all become SIHCoin trillionaires! Visit [https://remix.ethereum.org/](https://remix.ethereum.org/) and we will start writing our own smart-contracts.

~~~
//declare version of compiler (ranges can be used)
pragma solidity ^0.5.0;

/*
Setup the contract with variables defined.
A Solidity contract type is a collection of code, functions, etc, that lives at an address on the blockchain
*/
contract SIHCoin {    

    //variables types and names are declared 
    string name_;
    string symbol_;
    uint8 decimal_;
    uint256 totalsupply;
    
    //constructor is a function that is only run when the contract is deployed only
    //we set the variables and whether this is public/private
    constructor (string memory _name, string memory _symbol, uint8 _decimal, uint256 _totalsupply) public {
        name_ = _name;
        symbol_ = _symbol;
        decimal_ = _decimal;
        totalsupply = _totalsupply;
        balances[msg.sender] = totalsupply;
    }
    
    //functions are accessible to run at any time (and can be called by other contracts)
    function name() public view returns (string memory){
        return name_;
    }
    
    function symbol() public view returns (string memory) {
        return symbol_;
    }
    
    function decimals() public view returns (uint8) {
        return decimal_;
    }    
    
    function totalSupply() public view returns (uint256){
        return totalsupply;   
    }
    
    mapping (address => uint256) balances;
    
    function balanceOf(address _owner) public view returns (uint256 balance) {
        return balances[_owner];
    }
    
    event Transfer(address indexed _from, address indexed _to, uint256 _value);
    
    function transfer(address _to, uint256 _value) public returns (bool success){
        
        require(balances[msg.sender] >= _value, "Not enough balance!");
        
        //update balances
        balances[msg.sender] -= _value;
        balances[_to] += _value;
        emit Transfer(msg.sender, _to, _value);
        
        return true;
    }
}
~~~
{:. bash}

The Ethereum Virtual Machine or EVM is the runtime environment for smart contracts in Ethereum. It is completely isolated, which means that code running inside the EVM has no access to network, filesystem or other processes.



