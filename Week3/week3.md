# CS479/579 Reverse Engineering at NMSU
#### Camacho, Angel | Feb 14, 2023 | CS 479 | Week 3
---

### Week 3

Week 3, this week we set up a new environment for malware analysis, a windows xp virtual machine and a linux virtual machine. Two virtual machines were required, because we will be simulating a network interface a without actually connecting to the world wide web (www). The Windows XP machine will be running the malware and the linux machine will be pretending to be a network.

The purpose of inetsim (simulated internet) in this case is to prevent the malware from accesing the internet while sill providing the malware space to make requests to the www, this in turn allows us to analyze the malware packets that are being requested. By doing this we also prevent the malware from downloading other external resources it may need to complete the malwares purpose.

### Lab03-01.exe
## Executive Summary


After analyzing the malware I learned a few things one of them being the fact that it seems like its trying to reach for the domain www.preacticalmalwareanalysis.com. I am unsure what it exactly is trying to do with it but, I do know it is trying to connect to it. 

Further more I ran the Lab03-01.exe through Virustotal.com I learned that the executable file was being packed by "PENinja", the website had 66 different virusscanners flagg it as malware.

With Strings I learned that the the following libraries were being reached, kernel32.dll, winVMX32-, vmx32to64.exe, advapi32.

## Indicators of Compromise

Honestly after analyzing this malware despite the fact that it is being flagged as malware I cannot say for sure that it is actually doing something malicious in the computer. I know the program is trying to use some libraries that can be used for malicious intent but it does not mean that it is neseesary doing anything malicious.

Perhaps because we are in a safe environment but with the tools I have used I cannot concretly deduct that the malware is doing something malicious, or that it has been compromised.

Hashes provided by Virus Total.
MD5 d537acb8f56a1ce206bc35cf8ff959c0
SHA-1 0bb491f62b77df737801b9ab0fd14fa12d43d254
SHA-256 eb84360ca4e33b8bb60df47ab5ce962501ef3420bc7aab90655fd507d2ffcedd 
Compilation Timestamp 2008-01-06 14:51:31 UTC 

## Mitigations

By utilizing Windows 10, or Windows 11 will automatically place the security and vulnerabily of you device miles ahead compared to using an expired operating system.
Also having a a firewall enabeled might help, and if by some chance the malware some how still infected your machine, then perhaps having a dumby internet connect would help prevent malware from accesing the internet while stilll allowing the maware to "think" it is connected to the internet.


## Evidence

Before running the malware I opened wireshark to observe the packets that were being sent and recieved. No packets were being sent or recieved prior to executing the malware. After the malware was executed, I found that there was a change in activity. 
I copied and paseted the request.
From WIRESHARK: "38","161.603196000","10.0.0.23","10.0.0.20","DNS","92","Standard query 0xbb77  A www.practicalmalwareanalysis.com"
Reg shot showed that there were changes done however no new information was gathered.


### Lab03-02.dll
## Executive Summary

From what I observed this malware was ettemting to reach the domain practicalmawareanalysis.com. 57 of 69 security vendors flagged this file as malicious.

## Indicators of Compromise

Hashes provided by Virus Total.
MD5 84882c9d43e23d63b82004fae74ebb61
SHA-1 c6fb3b50d946bec6f391aefa4e54478cf8607211
SHA-256 5eced7367ed63354b4ed5c556e2363514293f614c2c2eb187273381b2ef5f0f9 
Compilation Timestamp 2010-09-28 01:00:25 UTC


## Mitigations

By utilizing Windows 10, or Windows 11 will automatically place the security and vulnerabily of you device miles ahead compared to using an expired operating system.
Also having a a firewall enabeled might help, and if by some chance the malware some how still infected your machine, then perhaps having a dumby internet connect would help prevent malware from accesing the internet while stilll allowing the maware to "think" it is connected to the internet. Deleting the respective file of malware should also prevent it from runnning. Turning off and on the computer should halt the virus from running, untill ranned again.

## Evidence

I was unable to run the malware, it seemed to be closed immidiatly as it was opened, I am unsure if this was done my windows xp it self or the malware purposefully closed its own operation, I suspect the later however the fact that I analysed the malware with strings, procmon wire shark and more suggest me that the malware is unsuccessful when running because it does not "achive" anything.

Strings is the only thing that provides me with information that lets me deduct what it is supposed to do, which in such case I can de duct that the malware ettempts to change registries in the system, while also creating a new service which the deletes the service. As shown bellow InstallA and uninstalA.

Relevant libraries in sequece that were reached.

GetModuleFileNameA
Sleep
TerminateThread
WaitForSingleObject
GetSystemTime
CreateThread
GetProcAddress
LoadLibraryA
GetLongPathNameA
GetTempPathA
ReadFile
CloseHandle
CreateProcessA
GetStartupInfoA
CreatePipe
GetCurrentDirectoryA
GetLastError
lstrlenA
SetLastError
OutputDebugStringA
KERNEL32.dll
RegisterServiceCtrlHandlerA
RegSetValueExA
RegCreateKeyA
CloseServiceHandle
CreateServiceA
OpenSCManagerA
RegCloseKey
RegQueryValueExA
RegOpenKeyExA
DeleteService
OpenServiceA
SetServiceStatus
ADVAPI32.dll
WSASocketA
WS2_32.dll
InternetReadFile
HttpQueryInfoA
HttpSendRequestA
HttpOpenRequestA
InternetConnectA
InternetOpenA
InternetCloseHandle
WININET.dll
memset
wcstombs
strncpy
strcat
strcpy
atoi
fclose
fflush
fwrite
fopen
strrchr
atol
sscanf
strlen
strncat
strstr
_itoa
strchr
__CxxFrameHandler
_EH_prolog
_CxxThrowException
_except_handler3
MSVCRT.dll
free
_initterm
malloc
_adjust_fdiv
_strnicmp
_chdir
_stricmp
Lab03-02.dll
Install
ServiceMain
UninstallService
installA
uninstallA
practicalmalwareanalysis.com
serve.html
Windows XP 6.11
CreateProcessA
kernel32.dll
.exe
GET
HTTP/1.1
quit
exit
getfile
cmd.exe /c 

### Lab03-03.exe
## Executive Summary

The malware seems to be a logger of some sort, but it does not seem to be sending the information anywhere remotely, but rather accessins some resousrces reading and modifing memory.

## Indicators of Compromise

After running the malware like the previous one it worked momentarly then stopped working. Perhaps it is trying to hide it self or perhaps it is not working properly.

Hashes provided by Virus Total.
MD5 e2bf42217a67e46433da8b6f4507219e
SHA-1 daf263702f11dc0430d30f9bf443e7885cf91fcb
SHA-256 ae8a1c7eb64c42ea2a04f97523ebf0844c27029eb040d910048b680f884b9dce 
Compilation Timestamp 2011-04-08 17:54:23 UTC 


## Mitigations

Delete the malware with the given hashes. Enable fire wall, use uptodate operating system.

Note: During this lab I could not get a lot of the programs to properly work like regshot, wireshark, procmon, dependecy walker. I tried to the best of my ability to use these programs but could not get them to properly work.