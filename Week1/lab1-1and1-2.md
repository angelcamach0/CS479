# CS479/579 Reverse Engineering at NMSU
#### Camacho, Angel | Jan 30, 2023 | CS 479 | Week 1
---
### Analyze the file Lab01-01.dll

1. Upload the files to http://www.VirusTotal.com/ and view the reports. Does either file match any existing antivirus signatures?

Yes the virus is recognized by several anti viruses.

2. When were these files compiled?

Compilation Timestamp 2010-12-19 16:16:38 UTC

3. Are there any indications that either of these files is packed or obfuscated? If so, what are these indicators?

No.

4. Do any imports hint at what this malware does? If so, which imports are they?

kernell32.dll & Ws2_32.dll are being called, these two libraries deals with memory manipulation & network connection instructions. In relation to network connection instructions, I noticed that there is an IP 27.26.152.13 maybe it is trying to communicate with it.


5. Are there any other files or host-based indicators that you could look for on infected systems?

From what I read in the chapter and my understanding the main indicators would be the hashes produced by these programs.
- MD5 ae4ca70697df5506bc610172cfc288e7
- SHA-1 31e8a82e497058ff14049cf283b337ec51504819
- SHA-256 8bcbe24949951d8aae6018b87b5ca799efe47aeb623e6e5d3665814c6d59aeae 

6. What network-based indicators could be used to find this malware on infected machines?

7. What would you guess is the purpose of these files

#### Analyze the file Lab01-02.exe

1. Upload the Lab01-02.exe file to http://www.VirusTotal.com/. Does it match any existing antivirus definitions?

2. Are there any indications that this file is packed or obfuscated? If so,
what are these indicators? If the file is packed, unpack it if possible.

Compared to running ```strings -n 4 Lab01-02.exe``` before unpacking with ```UPX -d Lab01-02.exe``` and running strings after unpacking I noticed a definetly notcied a difference, which in my opinion indicates that it was obfuscated. 

3. Do any imports hint at this program’s functionality? If so, which imports are they and what do they tell you?

Yes, imports such as kernell32.dll indicate to me that there is an ettemt for memory manipulation. advapi32.dll which accesd to core windows commponents such as the registry which operates the systems configuration options. Last but not least wininet.dll which are commonly used for highlevel networking functions that implement protocols such as FTP, HTTP, and NTP.


4. What host- or network-based indicators could be used to identify this malware on infected machines?

Its specific hash produced.
- MD5 290934c61de9176ad682ffdd65f0a669
- SHA-1 a4b35de71ca20fe776dc72d12fb2886736f43c22
- SHA-256 f50e42c8dfaab649bde0398867e930b86c2a599e8db83b8260393082268f2dba