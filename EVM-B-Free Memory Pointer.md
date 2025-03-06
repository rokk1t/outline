# Free Memory Pointer
- Definition: Указатель на свободную память.
	- Bytecode: `6080604052`.
```
60 80 | PUSH1 80 | For MSTORE(offset, value = 80)
Stack: 80

60 40 | PUSH1 40 | For MSTORE(offset = 40, value = 80)
Stack: 40, 80

52 | MSTORE(offset = 40, value = 80)
Memory: 000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000080
```
***
## Little Dictionary:
- `0x80 == 128, 0x40=64`.
- `Stack: 0x0000000000000000000000000000000000000000000000000000000000000000`.
- Memory = 3 cells.
***
External Links:
- https://www.evm.codes/playground
***
Internal Links:
$\bigtriangleup$ [[EVM-B-0Bytecodes]]
$\bigcirc$ Sibling
$\bigtriangledown$ Child
***
\[Nested] Tags:
- #EVM/Bytecode/FreeMemoryPointer 
- #Public
***
Keywords:
- 
***
***