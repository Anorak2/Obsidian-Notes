
2025-04-22

Tags: [[Reverse Engineering]] [[tool]]
# Ghidra Scripting Cheatsheet

We have access to the whole ```FlatprogramAPI``` which allows us to do a lot of things, documentation is listed at:
https://ghidra.re/ghidra_docs/api/ghidra/program/flatapi/FlatProgramAPI.html

All scripts extend ```ghidra.app.script.GhidraScript```, which Inherits from ```FlatProgramAPI``` and has access to all methods from ```FlatProgramAPI```.

All scripts are handed the current state encompassed by these variables:
- ```Program``` ```currentProgram```
- ```Address``` ```currentAddress```
- ```ProgramLocation``` ```currentLocation```
- ```ProgramSelection``` ```currentSelection```
- ```TaskMonitor``` ```monitor```

The full Ghidra API can be found at:
https://ghidra.re/ghidra_docs/api/index.html

#### Program Class
```Program``` is the root of the Program API hierarchy and outermost layer of the data model of the binary file
- ```Listing getListing()```
- ```FunctionManager getFunctionManager()```
- ```SymbolTable getSymbolTable()```
- ```Memory getMemory()```
- ```ReferenceManager getReferenceManager()```
- ```LanguageID getLanguageID()```

#### Function and Instruction Interfaces

Function interface:
https://ghidra.re/ghidra_docs/api/ghidra/program/model/listing/Function.html
- ```AddressSetView getbody()```
- ```StackFrame getStackFrame()```
- ```Function getFirstFunction()```: Returns the first function in the program
- ```Function getFunctionAfter(Address or Function)```: Can either take in an address or a function, and it returns the next function 
- ```Function getFunctionAt(Address entryPoint)```: Returns the function at a given address 
- ```Function getFunctionContaining(Address addr)```: Returns the function that has the given address inside of it 

Instruction interface:
https://ghidra.re/ghidra_docs/api/ghidra/program/model/listing/Instruction.html#getNext()
- ```String getMnemonicString()```: Returns the string for the function type, such as ```"MOV"```
- ```int getNumOperands()```
- ```int getOperandType(int optIndex)```
- ```Instruction getFirstInstruction(None or Function)```: returns the first instruction in either the program or the first instruction in a given function
- ```Instruction operation.getNext()```: returns the next operation if there is one or none if not found

#### User Interface Functions
- ```void println(String msg)```
- ```void printf(String msg, Object… args)```
- ```void popup(String msg)```
- ```String askString(String title, String msg)```
- ```boolean askYesNo(String title, String msg)```
- ```Address askAddress(String title, String msg)```
- ```int askInt(String title, String msg)```
- ```File askFile(String title, String buttonText)```
- ```boolean goTo(Address addr)```


# References

