
# CS479/579 Reverse Engineering at NMSU
#### Camacho, Angel | Apr 17, 2023 | CS 479 | Week 8
---

## Detecting DLL Injection

As part of our reverse engineering course, we were tasked with dissecting real malware and preparing malware analysis reports. This week's focus was on detecting DLL injection, a common technique used by malware loaders to inject evil threads into legitimate programs.

To accomplish this task, we used the malware from Lab 12-1 and honed our RE skills by doing crackmes. In order to demonstrate our understanding of the malware, we had to answer the following questions and provide relevant Ghidra screenshots to back up our answers:

1. Prove that the loader is using DLL injection.

To prove that the loader is using DLL injection, we analyzed the malware code in Ghidra and found evidence of it loading a DLL file using the LoadLibrary function. Specifically, we found a call to LoadLibraryA, which is used to load a DLL into the address space of the calling process. We also observed the malicious DLL being loaded into a legitimate process using Process Explorer, confirming that DLL injection was indeed taking place.

![Alt text](Screenshot%20from%202023-05-13%2019-03-36.png)

2. Identify the process that will be injected into.

Identifying the process that will be injected into requires analyzing the code further. We found that the malware enumerates through a list of running processes on the system and checks each one to see if it meets certain criteria for injection. Specifically, it looks for a process with a window title that contains the substring "Program Manager". If such a process is found, the malware will inject itself into that process.

![Alt text](Screenshot%20from%202023-05-13%2023-31-15.png)

3. Identify the entry point of the DLL injection. Where is DllMain?

To identify the entry point of the DLL injection, we searched for the DllMain function in the malicious DLL. We found it in the export table of the DLL, which is a list of functions that can be called from outside the DLL. DllMain is the entry point for a DLL and is called by the system when the DLL is loaded and unloaded. In this case, DllMain is responsible for setting up the malicious code to be executed within the legitimate process.

![Alt text](Screenshot%20from%202023-05-13%2023-39-19.png)

4. This malware does something every ____ seconds. How often, and where is the loop where that waiting happens?

The malware performs its malicious activity every 60 seconds. We identified this by analyzing the code and finding a loop that sleeps for 60,000 milliseconds (60 seconds) before executing the next iteration. The loop is located in the malicious DLL and is responsible for the malware's persistence and communication with its command and control (C&C) server.

![Alt text](Screenshot%20from%202023-05-13%2023-45-12.png)

5. What does the malware do every _____ seconds?

The malware connects to its C&C server every 60 seconds and waits for commands. When a command is received, the malware executes it within the context of the legitimate process it has injected into. The exact nature of the commands and their effects on the compromised system depend on the specific malware variant, which may include data exfiltration, remote access, or other malicious activities.

![Alt text](Screenshot%20from%202023-05-13%2023-43-10.png)