# gas optimizations

collect the gas  optimizations from links, from audit reports.

## 1. unchecked can save gas 
when it is not possible for them to overflow, as is the case when used in for- and while- loops

## 2. ++i > i ++

## 3. State variables should be cached in stack variables rather than re-reading them from storage.

## 4. setting the constructor to payable

## 5. Marking the function as payable will lower the gas cost for legitimate callers because the compiler will not include checks for whether a payment was provided. 
if function is limit with onlyOwner, use payable can save gas

## 6. internal function only called once can be inlined to save gas

## 7. using fixed bytes is cheaper than using string
Fixed size variables are cheaper than variable size.

## 8. optimize names to save gas
https://medium.com/joyso/solidity-how-does-function-name-affect-gas-consumption-in-smart-contract-47d270d8ac92
https://gist.github.com/IllIllI000/a5d8b486a8259f9f77891a919febd1a9

## 9. public function to external can save gas (Public vs External (External is cheaper))
The public visiblilty modifier is equivalent to external plus internal. In other words, both public and external can be called from outside your contract (like MetaMask), but of these two, only public can be called from other functions inside your contract.

Because public grants more access than external (and is costlier than the latter), the general best practice is to prefer external. Then you can consider switching to public if you fully understand the security and design implications.


## 10. in condition two statements with && , use two requries can save gas 

## 11. require/revert strings longer then 32 bytes cost extra gas 

## 12. x += y costs more gas than x = x + y for state variables

## 13. if use keccak256 with a const param, we can store in the storage to save gas 

## 14. ues newest version compiler can save gas 
* Use a Solidity version of at least 0.8.2 to get simple compiler automatic inlining.
* Use a Solidity version of at least 0.8.3 to get better struct packing and cheaper multiple storage reads.
* Use a Solidity version of at least 0.8.4 to get custom errors, which are cheaper at deployment than revert()/require() strings.
* Use a Solidity version of at least 0.8.10 to have external calls skip contract existence checks if the external call has a return value.

## 15. use int/uint < 32 byte, can cost more gas

## 16. for constans, use private can save gas than public
If needed, the values can be read from the verified contract source code, or if there are multiple values there can be a single getter function that returns a tuple of the values of all currently-public constants. Saves 3406-3606 gas in deployment gas due to the compiler not having to create non-payable getter functions for deployment calldata, not having to store the bytes of the value outside of where it’s used, and not adding another entry to the method ID table.

## 17. if div 2, use shifting op can save gas (Use of Bit shift operators)
Check if arithmethic operations can be achieved using bitwise operators, if yes, implement same operations using bitwise operators and compare the gas consumed. Usually bitwise logic will be cheaper (ofc we cannot use bitwise everywhere, there some limitations)

Note: Bit shift << and >> operators are not among the arithmetic ones, and thus don’t revert on overflow.

## 18. using calldata instead of memory for read-only arguments in external functions saves gas

## 19. <array>.length should not be looked up in every loop of a for-loop

## 20. Using bools for storage incurs overhead。

## 21. Use custom errors rather than revert()/require() strings to save gas

## 22. Fixed size variables are cheaper than variable size. （this like 8）
Whenever it is possible to set an upper bound on the size of an array, use a fixed size array instead of a dynamic one.

## 23. Mappings are cheaper than arrays
Solidity provides only two data types to represents list of data: arrays and maps. Mappings are cheaper, while arrays are packable and iterable.

In order to save gas, it is recommended to use mappings to manage lists of data, unless there is a need to iterate or it is possible to pack data types. This is useful both for Storage and Memory. You can manage an ordered list with a mapping using an integer index as a key.

## 24. There is no need to initialize variables with default values

## 25. Avoid redundant checks

## 26. Use nested if and, avoid multiple check combinations
Using nested is cheaper than using && multiple check combinations. There are more advantages, such as easier to read code and better coverage reports.

## 27. Use libraries to save some bytecode
When you call a public function of the library, the bytecode of the function will not become part of your contract, so you can put complex logic in the library while keeping the contract scale small.

The call to the library is made through a delegate call, which means that the library can access the same data and the same permissions as the contract. This means that it is not worth doing for simple tasks.

## 28. Packing Structs
A common gas optimization is “packing structs” or “packing storage slots”. This is the action of using smaller types like uint128 and uint96 next to each other in contract storage. When values are read or written in contract storage a full 256 bits are read or written. So if you can pack multiple variables within one 256 bit storage slot then you are cutting the cost to read or write those storage variables in half or more.


## 29. Solidity Gas Optimizer
Make sure Solidity’s optimizer is enabled. It reduces gas costs. If you want to gas optimize for contract deployment (costs less to deploy a contract) then set the Solidity optimizer at a low number. If you want to optimize for run-time gas costs (when functions are called on a contract) then set the optimizer to a high number.

## 30. Short circuiting















# Credits
https://hackmd.io/@DlM5Hmp7QSqUc7nKqKbkkw/H1QG4wbVq#Gas-Optimizations-in-Solidity
