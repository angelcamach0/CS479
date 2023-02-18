# CS479/579 Reverse Engineering at NMSU
#### Camacho, Angel | Feb 14, 2023 | CS 479 | Week 4
---


<li>What is the difference between machine code and assembly?</li>
The difference between machine code and assembly, is that machine code is first and formost specific to the microcode firmware (known to be 1's and 0's). As opposed to assembly which is arguably human readable. 
<li>If the ESP register is pointing to memory address 0x001270A4 and I execute a `push eax` instruction, what address will ESP now be pointing to?</li>
It should be at 0x001270A0.
<li>What is a stack frame?</li>
The last in first out structure supported by x86 which has a top down format, it is used for short tem storage only. its used for the management of data exchaneg between function calls.
<li>What would you find in a data section?</li>
Static values and global values.
<li>What is the heap used for?</li>
The heap is used for dynamic memory during program execution to create or eliminate values that the program no longer needs.
<li>What is in the code section of a program's virtual memory space?</li>
Includes instructions feteched by the cpu to execute the programs tasks. 
<li>What does the `inc` instruction do, and how many operands does it take?</li>
inc, Increments, It takes one register and increments it by one.
<li>If I perform a `div` instruction, where would I find the remainder of the binary division (modulo)?</li>
The remainder is stored in EDX. 
<li>How does `jz` decide whether to jump or not?</li>
It jumps if the ZF is equal to 1;
<li>How does `jne` decide whether to jump or not?</li>
jne will jump if the destination is not equal to the source.
<li>What does a `mov` instruction do?</li>
It moves from one location to another.
<li>What does the `TF` flag do and why is it useful for debugging?</li>
The tap flag is used for debugging, the x86 processor gwill execute only one instruction at a time if the flag is set.
<li>Why would an attacker want to control the EIP register inside a program they want to take control of?</li>
EIP is the instruction pointer, you can controll what is executed by the cpu.
<li>What is the AL register and how does it relate to EAX?</li>
AL is one of three ways of refrencing to EAX which is one byte.
<li>What is the result of the instruction `<em>xor eax, eax`</em> and where is it stored?</li>
The result of `<em>xor eax, eax`</em> is the register eax being set to zero. In other word its clears the EAX register.