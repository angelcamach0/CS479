# CS479/579 Reverse Engineering at NMSU
#### Camacho, Angel | Feb 1, 2023 | CS 479 | Week 2
---

Summary: Within this lab we took a look at two other viruses, both being .exe files, both of these files were flagged as viruses by Virustotal.com the first with an over all 85 virus flag rate, and the second one with an 82 percent virus flag rate.

From the tools that we used including UPX and Strings, it seemed like it both files were obfuscated, or the method of unpacking simply was not working on these specific files.

From the first libraries that were called we can infer that there was an ettempet for memory manipulation (kernell32.dll) and something to do with retreving the highest ordinal value GetProcAddress. 
The second libraries that were called which were KERNEL32.dll & Advapi32.dll which provides access to advanced core Windows components such
as the Service Manager and Registry.


Lab 1-3
Analyze the file Lab01-03.exe.

1. Upload the Lab01-03.exe file to http://www.VirusTotal.com/. Does it match
any existing antivirus definitions?

Yes, by 59 anti viruses, 11 anti viruses did not detect it, and 4 were unable to process it.

2. Are there any indications that this file is packed or obfuscated? If so,
what are these indicators? If the file is packed, unpack it if possible.


As demonstrated below there hasnt been any indicators that upacking lab01-03.exe has had any effect on strings output.
This means that it was either inefective or it wasn't obfuscated.

| Before UPX       | After UPX        |
|------------------|------------------|
| !Windows Program | !Windows Program |
| \'.rdata          | `.rdata          |
| @.data           | @.data           |
| KERNEL32.dll     | KERNEL32.dll     |
| LoadLibraryA     | LoadLibraryA     |
| GetProcAddress   | GetProcAddress   |
| ":Ll             | ":Ll             |
| 3Bt>O            | 3Bt>O            |
| VQ(8             | VQ(8             |
| 2]<,M            | 2]<,M            |
| P@M^             | P@M^             |
| S>VW             | S>VW             |
| AQ=h             | AQ=h             |
| I*G9>            | I*G9>            |
| e%nN             | e%nN             |
| ole32.vd         | ole32.vd         |
| Init             | Init             |
| FoCr             | FoCr             |
| U!!C             | U!!C             |
| }OLEAUTLA        | }OLEAUTLA        |
| IMSVCRTT"b       | IMSVCRTT"b       |
| _getmas          | _getmas          |
| yrcs             | yrcs             |
| \|P2r3Us         | \|P2r3Us         |
| p\|vuy           | p\|vuy           |
| fmod             | fmod             |
| xF*l             | xF*l             |


3. Do any imports hint at this program’s functionality? If so, which imports
are they and what do they tell you?

At first glance I only recognize kernell32.dll, which may be used to access and manipulate memory, files, and hardware.

4. What host- or network-based indicators could be used to identify this malware on infected machines?

```
MD5 9c5c27494c28ed0b14853b346b113145
SHA-1 290ab6f431f46547db2628c494ce615d6061ceb8
SHA-256 7983a582939924c70e3da2da80fd3352ebc90de7b8c4c427d484ff4f050f0aec 
```


Lab 1-4
Analyze the file Lab01-04.exe
1. Upload the Lab01-04.exe file to http://www.VirusTotal.com/. Does it match any existing antivirus definitions?

Yes, 58 anti viruses detected it as some kind of malware. 13 anti viruses did not detect it, and 4 were unable to process it.

2. Are there any indications that this file is packed or obfuscated? If so,
what are these indicators? If the file is packed, unpack it if possible.

As demonstrated below there hasnt been any indicators that upacking lab01-04.exe has had any effect on strings output.
This means that it was either inefective or it wasn't obfuscated.

| Before UPX                                          | After UPX                                           |
|-----------------------------------------------------|-----------------------------------------------------|
| !This program cannot be run in DOS mode.            | !This program cannot be run in DOS mode.            |
| Rich                                                | Rich                                                |
| .text                                               | .text                                               |
| \`.rdata                                             | `.rdata                                             |
| @.data                                              | @.data                                              |
| .rsrc                                               | .rsrc                                               |
| h,0@                                                | h,0@                                                |
| h@0@                                                | h@0@                                                |
| hL0@                                                | hL0@                                                |
| Qhd0@                                               | Qhd0@                                               |
| hl0@                                                | hl0@                                                |
| hp0@                                                | hp0@                                                |
| hx0@                                                | hx0@                                                |
| =$1@                                                | =$1@                                                |
| =(1@                                                | =(1@                                                |
| =,1@                                                | =,1@                                                |
| SVW                                                 | SVW                                                 |
| 501@                                                | 501@                                                |
| %\ @                                                | %\ @                                                |
| %l @                                                | %l @                                                |
| CloseHandle                                         | CloseHandle                                         |
| OpenProcess                                         | OpenProcess                                         |
| GetCurrentProcess                                   | GetCurrentProcess                                   |
| CreateRemoteThread                                  | CreateRemoteThread                                  |
| GetProcAddress                                      | GetProcAddress                                      |
| LoadLibraryA                                        | LoadLibraryA                                        |
| WinExec                                             | WinExec                                             |
| WriteFile                                           | WriteFile                                           |
| CreateFileA                                         | CreateFileA                                         |
| SizeofResource                                      | SizeofResource                                      |
| LoadResource                                        | LoadResource                                        |
| FindResourceA                                       | FindResourceA                                       |
| GetModuleHandleA                                    | GetModuleHandleA                                    |
| GetWindowsDirectoryA                                | GetWindowsDirectoryA                                |
| MoveFileA                                           | MoveFileA                                           |
| GetTempPathA                                        | GetTempPathA                                        |
| KERNEL32.dll                                        | KERNEL32.dll                                        |
| AdjustTokenPrivileges                               | AdjustTokenPrivileges                               |
| LookupPrivilegeValueA                               | LookupPrivilegeValueA                               |
| OpenProcessToken                                    | OpenProcessToken                                    |
| ADVAPI32.dll                                        | ADVAPI32.dll                                        |
| _snprintf                                           | _snprintf                                           |
| MSVCRT.dll                                          | MSVCRT.dll                                          |
| _exit                                               | _exit                                               |
| _XcptFilter                                         | _XcptFilter                                         |
| exit                                                | exit                                                |
| __p___initenv                                       | __p___initenv                                       |
| __getmainargs                                       | __getmainargs                                       |
| _initterm                                           | _initterm                                           |
| __setusermatherr                                    | __setusermatherr                                    |
| _adjust_fdiv                                        | _adjust_fdiv                                        |
| __p__commode                                        | __p__commode                                        |
| __p__fmode                                          | __p__fmode                                          |
| __set_app_type                                      | __set_app_type                                      |
| _except_handler3                                    | _except_handler3                                    |
| _controlfp                                          | _controlfp                                          |
| _stricmp                                            | _stricmp                                            |
| winlogon.exe                                        | winlogon.exe                                        |
| SeDebugPrivilege                                    | SeDebugPrivilege                                    |
| sfc_os.dll                                          | sfc_os.dll                                          |
| \system32\wupdmgr.exe                               | \system32\wupdmgr.exe                               |
| %s%s                                                | %s%s                                                |
| #101                                                | #101                                                |
| EnumProcessModules                                  | EnumProcessModules                                  |
| psapi.dll                                           | psapi.dll                                           |
| GetModuleBaseNameA                                  | GetModuleBaseNameA                                  |
| psapi.dll                                           | psapi.dll                                           |
| EnumProcesses                                       | EnumProcesses                                       |
| psapi.dll                                           | psapi.dll                                           |
| \system32\wupdmgr.exe                               | \system32\wupdmgr.exe                               |
| %s%s                                                | %s%s                                                |
| \winup.exe                                          | \winup.exe                                          |
| %s%s                                                | %s%s                                                |
| !This program cannot be run in DOS mode.            | !This program cannot be run in DOS mode.            |
| Rich                                                | Rich                                                |
| .text                                               | .text                                               |
| \`.rdata                                             | `.rdata                                             |
| @.data                                              | @.data                                              |
| h$0@                                                | h$0@                                                |
| Rh<0@                                               | Rh<0@                                               |
| QhD0@                                               | QhD0@                                               |
| %L @                                                | %L @                                                |
| hX @                                                | hX @                                                |
| SVW                                                 | SVW                                                 |
| =x0@                                                | =x0@                                                |
| %, @                                                | %, @                                                |
| %D @                                                | %D @                                                |
| GetWindowsDirectoryA                                | GetWindowsDirectoryA                                |
| WinExec                                             | WinExec                                             |
| GetTempPathA                                        | GetTempPathA                                        |
| KERNEL32.dll                                        | KERNEL32.dll                                        |
| URLDownloadToFileA                                  | URLDownloadToFileA                                  |
| urlmon.dll                                          | urlmon.dll                                          |
| _snprintf                                           | _snprintf                                           |
| MSVCRT.dll                                          | MSVCRT.dll                                          |
| _exit                                               | _exit                                               |
| _XcptFilter                                         | _XcptFilter                                         |
| exit                                                | exit                                                |
| __p___initenv                                       | __p___initenv                                       |
| __getmainargs                                       | __getmainargs                                       |
| _initterm                                           | _initterm                                           |
| __setusermatherr                                    | __setusermatherr                                    |
| _adjust_fdiv                                        | _adjust_fdiv                                        |
| __p__commode                                        | __p__commode                                        |
| __p__fmode                                          | __p__fmode                                          |
| __set_app_type                                      | __set_app_type                                      |
| _except_handler3                                    | _except_handler3                                    |
| _controlfp                                          | _controlfp                                          |
| \winup.exe                                          | \winup.exe                                          |
| %s%s                                                | %s%s                                                |
| \system32\wupdmgrd.exe                              | \system32\wupdmgrd.exe                              |
| %s%s                                                | %s%s                                                |
| http://www.practicalmalwareanalysis.com/updater.exe | http://www.practicalmalwareanalysis.com/updater.exe |

3. When was this program compiled?

According to Virus Total:
Compilation Timestamp 2019-08-30 22:26:59 UTC

4. Do any imports hint at this program’s functionality? If so, which imports
are they and what do they tell you?

KERNEL32.dll - This is a very common DLL that contains core functionality, such as access
and manipulation of memory, files, and hardware.
Advapi32.dll - This DLL provides access to advanced core Windows components such
as the Service Manager and Registry.


5. What host- or network-based indicators could be used to identify this
malware on infected machines?

```
MD5 625ac05fd47adc3c63700c3b30de79ab
SHA-1 9369d80106dd245938996e245340a3c6f17587fe
SHA-256 0fa1498340fca6c562cfa389ad3e93395f44c72fd128d7ba08579a69aaf3b126 
```