---
title: "3. An employment contract"
teaching: 5
exercises: 20
questions:
- "What can you include in a smart-contract?"
objectives:
- "Write a smart contract"
keypoints:
- "Every execution of the contract is a transaction on the blockchain"

---

# Write a smart contract

We can write definite rules and logic on our contract. 

~~~
pragma solidity ^0.5.0;

// ^0.5.0 means make it compatible for all .5. versions
//https://remix.ethereum.org/#optimize=false&runs=200&evmVersion=null&version=soljson-v0.5.17+commit.d19bba13.js

/* 

This is our first smart contract code
We are building our first app!

*/

//import "../2_Owner.sol"

contract Nathan {
  
    bool isOpen;    //camelCase
    bool isValidInOffice; //bool can be true or false
    
    uint8 smallNo; //this variable can have value of 2^8 = 0-255
    uint16 nextNo; //upto 2^16=0-65535
    uint256 largestNo; // 2^256 = a 78 digit number
    
    
    bytes1 data; 
    bytes32 largeData;
    
    string alphanumericEntry;
    
    //address type varible
    address payable user;   //only "payable" can send or recieve ether
    address manager;
    address payable admin;
    
    enum TrafficLight {
        Red,
        Yellow,
        ellow,
        Amber,
        Orange,
        Green
    }
    
    enum VoteCandidate {Trump, Biden}
    
    //Arrays
    
    uint8[] employeeNos;
    address[50] lotteryWinners;
    
    struct PersonalData {
        address employee;
        string fName;
        //string lName;
        //bool isEligible;
        //uint8 employeeNo;
    }
    
    
    //Maping : KEY map to a VALUE.
    
    //mapping (KEY => VALUE) allow;
    mapping (address => uint8) enumber;  //His address is mapped to his employ number
    mapping (address => uint8) salary;
    mapping (uint8 => PersonalData) pdata;
    //mapping (address => mapping (uint8 => PersonalData)) nestedmapping;
    mapping (address => mapping (address => uint256)) allowance;
    
    
    /*
    function NAME( inpu PARAMETER) VISIBILITY RETURNS(DATA VARIABLE){
    
        SOME CODE
    }
    */
    
    function addData(uint8 _number) public returns(uint8){
        
        smallNo = _number;  //Single = RHS value is assigned to LHS.
        smallNo = smallNo + 10;
        
        return smallNo;
        
    }
    
    
    function viewData() public view returns(uint8) {
        
        return smallNo;
    }
    
    //function addEmployee(address _addr, uint8 _no) public {
    function addEmployee(uint8 _no) public {
        
        //enumber[KEY] = VALUE;
        
        //enumber[_addr] = _no;
        
        //whoever runs this will be map their address to the number
        enumber[msg.sender] = _no;
        
        //require to check if _no is NOT part of the emplyeeNos array.
        employeeNos.push(_no);
        
    }
    
    function viewNos() public view returns(uint8[] memory) {
        return employeeNos;
    }
    
    //Check someone elses employee number (if you have their address)
    function viewEmp(address _addr1) public view returns (uint8) {
        
        return enumber[_addr1];
        
    }
    
    //whoever "calls" this function will be the addres that gets mapped
    function viewMyEmp() public view returns(uint8) {
        return enumber[msg.sender];
    }
    
    //0xd9145CCE52D386f254917e481eB44e9943F39138
    
    //if the address of the caller of function is to be identified - msg.sender

    //pure function neither reads or writes to the ledger
    function welcome() public pure returns(string memory) {
        return "Welcome to my smart contract.";
    }
    
    function welcome1() public pure returns(string memory, uint8) {
        return ("Welcome to my smart contract #", 1);
    }
    
    function addPDate(string memory _fName) public {
        pdata[enumber[msg.sender]] = PersonalData(msg.sender, _fName);
        
    }
    
    function viewPData (uint8 _no) public view returns(string memory) {
        return pdata[_no].fName;
    }
    
}
~~~
{: .bash}


