# CS479/579 Reverse Engineering at NMSU
#### Camacho, Angel | Feb 20, 2023 | CS 479 | Week 4
---


<li>What is the difference between machine code and assembly?</li>
The difference between machine code and assembly is that machine code is first and foremost specific to the microcode firmware (known to be 1s and 0s). As opposed to assembly which is arguably human readable.
<li>If the ESP register is pointing to memory address 0x001270A4 and I execute a `push eax` instruction, what address will ESP now be pointing to?</li>
It should be at 0x001270A0.
<li>What is a stack frame?</li>
The last in first out structure is supported by x86 which has a top-down format, it is used for short-term storage only. It's used for the management of data exchange between function calls.
<li>What would you find in a data section?</li>
Static values and global values.
<li>What is the heap used for?</li>
The heap is used for dynamic memory during program execution to create or eliminate values that the program no longer needs.
<li>What is in the code section of a program's virtual memory space?</li>
Includes instructions fetched by the CPU to execute the program's tasks.
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
The tap flag is used for debugging, the x86 processor will execute only one instruction at a time if the flag is set.
<li>Why would an attacker want to control the EIP register inside a program they want to take control of?</li>
EIP is the instruction pointer, you can control what is executed by the CPU.
<li>What is the AL register and how does it relate to EAX?</li>
AL is one of three ways of referencing to EAX which is one byte.
<li>What is the result of the instruction `<em>xor eax, eax`</em> and where is it stored?</li>
The result of `<em>xor eax, eax`</em> is the register eax being set to zero. In other words, it clears the EAX register.
Also solve this crackme

<hr>

### Ghidra first time use

In this week we were also introduced to a new tool, a tool desinged by the one an only NSA. We used Ghidra decompiler. The objective was very simple, figure out the "password" that the program required us to input inorder for the result to give us the pass. 

First we installed it our linux vm's, I had to install a GUI on my virtual machine because I was running Ubuntu Live Server. Not that Ghidra is malware but we also took safety precations while installing the program, such as trasferring files via the shared folder of the vm, and not directly logging in to our vms to the internet, infact we isolated our virtual machines form the network in previous weeks. 

Second we installed a Open JDK, The transfering of the files from the shared folder to another location in the vm was needed, however in Linux for some reason the user isnt allowed to see the files in the shared folder, this is because they dont have the privilages to do so. So one cant simply drag and drop the files fromt he shared folder to the vm and start running immediatly. So we had to use the terminal give our selves root access and trasnfer the files "manually" via the terminal. Then we gave the user access to the files by changing the fiels permissions with chmod.

Third we ran and installed ghidra, and we proceded to create an new project and imported the "crack.me" file which is the file that we had to crack.

In conclusion cracking the file was straight foward but I did have to search up a few things because I was unfamiliar with the software. The main key points that I would make that allowed me to crack the file was to first start essentially reading the main function and seeing what the file is essentially doing, after I observed that it was calling a specific function I followed that fuction to see what was the requirement for that fuction to return true, and I saw that it was takign an input and takign the modus of 1223 and if the remainder was zero then the fuction would return 1. Which in the main it was inside of an if statement if true (1) then it printed you successfully cracked the file.

The password was 1223.
