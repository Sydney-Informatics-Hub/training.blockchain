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

Let's all become SIHCoin trillionaires! Visit [https://remix.ethereum.org/](https://remix.ethereum.org/) and we will start writing our own smart-contracts and [ERC-20 tokens](https://ethereum.org/en/developers/docs/standards/tokens/erc-20/).

~~~
//declare version of compiler (ranges can be used)
//Note: this does not change the version of the compiler, it just checks the used compiler with this line
pragma solidity ^0.5.0;


//import functions
//import other contracts etc

/*
Setup the contract with variables defined.
A Solidity contract type is a collection of code, functions, etc, that lives at an address on the blockchain
*/
contract SIHCoin {    

    //Solidity is a statically typed language, 
    //which means that the type of each variable (state and local) needs to be specified
    string symbol_;
    uint256 totalsupply;
    
    //constructor is a function that is only run when the contract is deployed only
    //we set the variables and whether this is public/private/internal/external
    constructor (string memory _symbol, uint256 _totalsupply) public {
        
        //_leading underscores indicate variable is private
        //trailing_ underscores to avoid naming collisions
        
        symbol_ = _symbol;
        totalsupply = _totalsupply;
        balances[msg.sender] = totalsupply;
        
        //msg.sender address of the person clicking the button
    }
    
    
    //functions are accessible to run at any time (and can be called by other contracts)
    //Returns the currecny symbol
    //"memory" keyword can indicate whether it stored in storage, onchain, temporarily
    function symbol() public view returns (string memory) {
        return symbol_;
    }
    
    //Returns the circulating supply of the currency
    function totalSupply() public view returns (uint256){
        return totalsupply;   
    }
    
    //Mappings are similar to hash tables or dictionaries, 
    //which are virtually initialised such that every possible key exists and is mapped to a value
    //map all adresses to the balance of our currency
    mapping (address => uint256) balances;
    
    
    //Returns the balance of some wallet address
    function balanceOf(address _owner) public view returns (uint256 balance) {
        return balances[_owner];
    }
    
    
    //Events are convenience interfaces with the EVM logging facilities.
    /*
    Events are inheritable members of contracts. 
    When you call them, they cause the arguments to be stored in the transaction’s log 
    These logs are associated with the address of the contract, are incorporated into the blockchain, 
    and stay there as long as a block is accessible
    */
    event Transfer(address indexed _from, address indexed _to, uint256 _value);
    
    //A function that allows transactions between addreses and maintains totalsupply of currenct
    function transfer(address _to, uint256 _value) public returns (bool success){
        
        //error handling capabilities and control sturctures
        require(balances[msg.sender] >= _value, "Not enough balance!");
        
        //update balances
        balances[msg.sender] -= _value;
        balances[_to] += _value;
        
        //emitted events are stored in the blockchain transaction logs
        emit Transfer(msg.sender, _to, _value);
        
        return true;
    }
}
~~~
{:. bash}

The Ethereum Virtual Machine or EVM is the runtime environment for smart contracts in Ethereum. It is completely isolated, which means that code running inside the EVM has no access to network, filesystem or other processes.



