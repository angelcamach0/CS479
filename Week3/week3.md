# CS479/579 Reverse Engineering at NMSU
#### Camacho, Angel | Feb 14, 2023 | CS 479 | Week 3
---

66 of 71 - anti-viruses detected and flaged lab03-01.exe as malware.
File type: exe
Packer: PENinja

kernel32.dll
winVMX32-
vmx32to64.exe
advapi32
ntdll
user32

### Week 3

Week 3, this week we set up a new environment for malware analysis, a windows xp virtual machine and a linux virtual machine. Two virtual machines were required, because we will be simulating a network interface a without actually connecting to the world wide web (www). The Windows XP machine will be running the malware and the linux machine will be pretending to be a network.

The purpose of inetsim (simulated internet) in this case is to prevent the malware from accesing the internet while sill providing the malware space to make requests to the www, this in turn allows us to analyze the malware packets that are being requested. By doing this we also prevent the malware from downloading other external resources it may need to complete the malwares purpose.

### Lab03-01.exe
## Executive Summary


After analyzing the malware I learned a few things one of them being the fact that it seems like its trying to reach for the domain www.preacticalmalwareanalysis.com. I am unsure what it exactly is trying to do with it but, I do know it is trying to connect to it. 

Further more I ran the Lab03-01.exe through Virustotal.com I learned that the executable file was being packed by "PENinja", the website had 66 different virusscanners flagg it as malware.

With Strings I learned that the the following libraries were being reached, kernel32.dll, winVMX32-, vmx32to64.exe, advapi32.

## Indicators of Compromise

How do i know that the maware is doing something bad?
Honestly after analyzing this malware despite the fact that it is being flagged as malware I cannot say for sure that it is actually doing something malicious in the computer. I know the program is trying to use some libraries that can be used for malicious intent but it does not mean that it is neseesary doing anything malicious.

Perhaps because we are in a safe environment but with the tools I have used I cannot concretly deduct that the malware is doing something malicious.


## Mitigations

By utilizing Windows 10, or Windows 11 will automatically place the security and vulnerabily of you device miles ahead compared to using an expired operating system.
Also having a a firewall enabeled might help, and if by some chance the malware some how still infected your machine, then perhaps having a dumby internet connect would help prevent malware from accesing the internet while stilll allowing the maware to "think" it is connected to the internet.


## Evidence

Before running the malware I opened wireshark to observe the packets that were being sent and recieved. No packets were being sent or recieved prior to executing the malware. After the malware was executed, I found that there was a change in activity. 
I copied and paseted the request.
From WIRESHARK: "38","161.603196000","10.0.0.23","10.0.0.20","DNS","92","Standard query 0xbb77  A www.practicalmalwareanalysis.com"
Regshot did not help 


### Lab03-02.dll
## Executive Summary

What i learned about the mallware

## Indicators of Compromise

How do i know that the maware is doing something bad?

## Mitigations

how to stop the malware. prevent it from happening.

## Evidence

### Lab03-03.exe
## Executive Summary

What i learned about the mallware

## Indicators of Compromise

How do i know that the maware is doing something bad?

## Mitigations

how to stop the malware. prevent it from happening.

## Evidence



Strings v2.42
Copyright (C) 1999-2011 Mark Russinovich
Sysinternals - www.sysinternals.com

!This program cannot be run in DOS mode.
Rich
.text
`.rdata
@.data
.reloc
QQSUVW3
Hu4S
PSUV
j@SU
D$ 3
|$%Y
D$$SPh
t%HHt
D$ P
D$$h
D$ P
PhDa
SSSSh
tNSh
Qh4a
SSSSP
_WSP
QSSSSSS
F;5p
SVW3
PhDa
SSSj
Ph~f
SVWjJ3
SPSS
tFSh
VSh0
SSSPS
u(hta
uZh`a
PSSj
SPSS
_^[t
SVWj
PhDa
SSSSh
Ph4a
SSSSW
QVPW
j@VV
UUUUh
QQjPh(`
OQQQQP
Pj@h
_^][
PShxd
SSSSSh
SPSj
SPS3
ShTb
PhHb
@Y@PWj
VHtHHt3Ht
Hu_3
NWVS
u7WPS
u&WVS
_^[]
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
??3@YAXPAX@Z
fwrite
fopen
strrchr
??2@YAPAXI@Z
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
??1type_info@@UAE@XZ
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
Y29ubmVjdA==
practicalmalwareanalysis.com
serve.html
dW5zdXBwb3J0
c2xlZXA=
Y21k
cXVpdA==
 Windows XP 6.11
CreateProcessA
kernel32.dll
.exe
HTTP/1.1
%s %s
1234567890123456
quit
exit
getfile
cmd.exe /c 
ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/
--!>
<!--
.PAX
.PAD
DependOnService
RpcSs
ServiceDll
GetModuleFileName() get dll path
Parameters
Type
Start
ObjectName
LocalSystem
ErrorControl
DisplayName
Description
Depends INA+, Collects and stores network configuration and location information, and notifies applications when this information changes.
ImagePath
%SystemRoot%\System32\svchost.exe -k 
SYSTEM\CurrentControlSet\Services\
CreateService(%s) error %d
Intranet Network Awareness (INA+)
%SystemRoot%\System32\svchost.exe -k netsvcs
OpenSCManager()
You specify service name not in Svchost//netsvcs, must be one of following:
RegQueryValueEx(Svchost\netsvcs)
netsvcs
RegOpenKeyEx(%s) KEY_QUERY_VALUE success.
RegOpenKeyEx(%s) KEY_QUERY_VALUE error .
SOFTWARE\Microsoft\Windows NT\CurrentVersion\Svchost
IPRIP
uninstall success
OpenService(%s) error 2
OpenService(%s) error 1
uninstall is starting
.?AVtype_info@@
080@0^0m0r0
1,131D1S1e1n1
2+2:2A2R2r2{2
3;3B3T3[3
4$4W4b4|4
676D6P6]6r6|6
7"7,797D7]7p7w7
8)868B8O8d8n8
9+969O9b9i9v9
:$:2:K:U:\:l:
;";7;A;Q;^;e;x;
<)<9<C<S<e<x<
=*=7=A=Q=c=q=
>(>/>B>Q>_>t>~>
?-???M?b?l?~?
0-0;0P0Z0l0z0
1)1>1H1U1`1y1
2)202?2J2]2j2w2
4!4:4A4Q4_4t4{4
5 505:5E5o5x5
60676G6U6j6q6~6
7&707;7]7f7v7
8&848N8X8h8r8
9*959O9Y9i9s9
:+:6:P:Z:j:t:
;,;7;Q;[;k;u;
< <'<2<O<\<l<v<
=!=.=9=S=]=j=t=
>">/>:>T>^>n>x>
?#?0?;?U?_?o?y?
0*010<0S0`0m0w0
1!1+1Q1i1s1
2$2G2[2b2j2v2
3 3(3.33383>3D3K3\3c3}3
3`4i4|4
5J5W5v5
5%636:6Q6\6s6
7<7G7p7
888N8d8t8
8!9O9^9p9w9
;&;7;f;
<(<.<9<B<H<e<l<x<
=$=/=K=o=
=(>J>O>j>w>
4"414F4T4s4
5 5'585V5]5m5s5
6H6\6p6u6
797N7W7c7i7q7y7
8)818C8T8\8k8{8
9/9@9Q9d9u9
:0:>:G:X:^:j:r:
;#;J;P;b;w;
<F<m<z<
>.>:>@>b>t>
h1l1p1t1|1
2 242@2H2x2
