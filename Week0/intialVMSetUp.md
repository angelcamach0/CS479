# CS479/579 Reverse Engineering at NMSU
#### Camacho, Angel | Jan 26, 2023 | CS 479
---

In this repo (will) hold your reports on reverse engineering malware samples from "Practical Malware Analysis"

On week zero we set up a safe environment where we will be conducting our labs. I set up a dual boot system where I am running Windows 11 and PopOS on my host machine. In which we set a Virtual Machine (using Virtual Box) to work with malware.

The purpose of this set up is to create a safe environment where we greatly reduce the posibilites of our host machine getting infected.

Steps taken to set up envirnment.
> 1. Created a live USB using Rufus and popOS.iso
> 2. Enabled Virtualization at the BIOS settings of my computer.
> 3. Disabled Fast Boot and Seecure Boot.
> 4. Changed the primary boot drive to be from the source of a usb flash drive.
> 5. Ran PopOS live drive on my computer and initialized the installation.
> 6. Ran a system update on PopOS.
> 7. Installed Virtual Box
> 8. Created a new VM using a Windows 10 .iso
> 9. Disabled the network card so the VM machine is unable to communicate witht the network.
> 10. Took snapshot of the state of the VM for the future recovery.

Technical issues redacted for simplicity.