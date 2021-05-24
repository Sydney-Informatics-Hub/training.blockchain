---
title: "2. Simple methods"
teaching: 10
exercises: 15
questions:
- "Which method for acceleration should I choose?"
objectives:
- "Learn simples methods to profile your code"
- "See how numpy and pandas use Vectorising to improve perfomance for some data"
- "Use MPI to communicate between workers"
keypoints:
- "Understand there are different ways to accelerate"
- "The best method depends on your algorithms, code and data"
---
This episode shows you a few of the basic tools that we can use in Python to make our code go faster. There is no perfect method for optimising code. Efficiency gains depend on what your end goal is, what libraries are available, what method or approach you want to take when writing algorithms, what your data is like, what hardware you have. Hopefully these notes will allow you to think about your problems from different perspectives to give you the best opportunity to make your development and execution as efficient as possible.


# Writing your own cryptocurrency

Let's all become SIHCoin trillionaires! Visit https://remix.ethereum.org/ and we will start writing our contracts.

~~~
pragma solidity ^0.5.0;

//Setup the contract with variables defined.
contract SIHCoin {    
    string name_;
    string symbol_;
    uint8 decimal_;
    uint256 totalsupply;
    
    constructor (string memory _name, string memory _symbol, uint8 _decimal, uint256 _totalsupply) public {
        name_ = _name;
        symbol_ = _symbol;
        decimal_ = _decimal;
        totalsupply = _totalsupply;
        balances[msg.sender] = totalsupply;
    }
    
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
{: .python}




# MPI: Message Passing Interface
MPI is a standardized and portable message-passing system designed to function on a wide variety of parallel computers.
The standard defines the syntax and semantics of a core of library routines useful to a wide range of users writing portable message-passing programs in C, C++, and Fortran. There are several well-tested and efficient implementations of MPI, many of which are open-source or in the public domain.

MPI for Python, found in [mpi4py](https://mpi4py.readthedocs.io/en/stable/index.html), provides bindings of the MPI standard for the Python programming language, allowing any Python program to exploit multiple processors. [This simple code](https://sydney-informatics-hub.github.io/training.artemis.python/files/mpi.py) demonstrates the collection of resources and how code is run on different processes:

~~~
#Run with:
#mpiexec -np 4 python mpi.py

from mpi4py import MPI

comm = MPI.COMM_WORLD
size = comm.Get_size()
rank = comm.Get_rank()

print("I am rank %d in group of %d processes." % (rank, size))
~~~
{: .python}

If you want to submit this python script on Artemis, the PBS script is below. Notice here we are requesting 4 seperate nodes in the PBS script. This amount aligns with the ```-np 4``` flag (number of processes), so each process is seperate and executed on different nodes on Artemis.
~~~
#!/bin/bash

#PBS -P Training
#PBS -N testmpi
#PBS -l select=4:ncpus=1:mem=1GB
#PBS -l walltime=00:10:00
#PBS -q defaultQ

cd $PBS_O_WORKDIR
module load python
module load openmpi-gcc

mpiexec -np 4 python mpi.py > mpi.out
~~~
{:. bash}

Let's now get stuck into some more specific use-cases and tools to use.

