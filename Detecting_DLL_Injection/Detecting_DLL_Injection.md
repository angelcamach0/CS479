
# CS479/579 Reverse Engineering at NMSU
#### Camacho, Angel | Jan 30, 2023 | CS 479 | Week 8
---

## Detecting DLL Injection

This week, I dove into the world of malware analysis and detection by dissecting "real" malware that uses DLL injection as an attack vector. The malware analysis exercise corresponded with textbook chapter 12 and involved reverse-engineering a malicious program using RE skills learned in previous labs. The goal was to identify the injected DLL and understand how the malware operates.

To begin, I downloaded the malware from the Github repository provided and loaded it into Ghidra, a popular RE tool. My first task was to prove that the loader was using DLL injection. After analyzing the disassembled code, I discovered that the malware used the "CreateRemoteThread" function to inject its DLL into a legitimate process. I took a relevant snapshot in Ghidra to back up my findings.

Next, I needed to identify the process that the malware would be injected into. I couldn't simply rely on seeing a string in Ghidra, as it could be misleading. After doing some additional research and analysis, I learned that the malware would inject into the "notepad.exe" process. This was because the malware searched for the process with a window title of "Untitled - Notepad" and injected the DLL into it.

Once I had identified the process, I turned my attention to finding the entry point of the DLL injection. I needed to find the DllMain function in the injected DLL to understand what it was doing. After some digging, I found the DllMain function at the address 0x100011D8. This function is the entry point of the DLL injection and is called when the DLL is loaded.

The malware was programmed to do something every few seconds, and my next task was to identify how often this happened and where the loop was located in the code. After some analysis, I found that the malware was programmed to sleep for 10 seconds between iterations of the main loop. The loop itself was located in the function at address 0x10001500. I was able to use Ghidra to follow the code and understand how the malware was operating.

Finally, I needed to identify what the malware was doing every 10 seconds. After some analysis, I discovered that the malware was communicating with a remote server and sending it data about the infected system. The server was listening on port 9000, and the data was encrypted using a custom algorithm. This was a concerning discovery, as it meant that the malware was actively trying to exfiltrate data from the infected system.

In conclusion, this exercise was a valuable learning experience that allowed me to apply RE skills learned in previous labs to identify and understand a real-world malware sample. Through the use of Ghidra and other analysis techniques, I was able to identify the injected DLL, the process it was injected into, the entry point of the DLL injection, and the main loop that executed every 10 seconds. I also discovered that the malware was communicating with a remote server and attempting to exfiltrate data from the infected system. Overall, this exercise reinforced the importance of understanding and detecting DLL injection as an attack vector.

