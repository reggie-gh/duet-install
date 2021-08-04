NOTE: THIS REPO IS NO LONGER ACTIVELY MAINTAINED. PLEASE USE http://sourceforge.net/projects/cloverefiboot/ INSTEAD.

This repo contains compiled build of tianocore.sourceforge.net UDK/EDK2 DuetPkg firmware and tianocore.sourceforge.net EDK DUET firmware (EDK_UEFI64 version that of SVN repository as on 15th September 2010 - revision 236 - seems like EDK development has stopped).


The Bootsector "bin" files have been taken from Migle's BootDuet https://github.com/migle/BootDuet and the "com" files have been taken from UDK/EDK2 DuetPkg. The Windows_Binaries files have also been taken from UDK/EDK2 Basetools. The CreateUSB.cmd script has been taken from EDK2 DuetPkg CreateBootDisk.bat file and modified by me.


The UDK_X64 firmware supports AHCI but EDK_UEFI64 firmware supports only Legacy IDE (or IDE Compatibility) SATA mode. 


Both the firmwares do not include support for reading HFS or HFS+ filesystem partitions or for reading Apple Partition Map partitioned disks.
These firmwares also do not include support for reading NTFS filesystem partitions from within the firmware itself. They include support only for FAT12, FAT16 and FAT32 filesystems, and support only Master Boot Record and GUID Partition Table partitioned disks. 


They are completely unmodified in source code level (although some modules have been removed/added from the Makefiles) UDK_X64 and EDK_UEFI64 firmware. 

Please do not request addition of new features to DUET as I am not a programmer (I only know Linux Shell scripting). If the feature you request is already available in source-code form and if it can be compiled into the firmware, then I would try to do so. 


I use UDK_X64 firmware to boot Windows 7 Professional x86_64 SP1 in UEFI-GPT mode in my Dell Studio 1537 Laptop.


This git repo contains 2 builds of DUET firmware :-

UDK_X64 - UDK/EDK2 based UEFI 2.31 x86_64 64-bit firmware (usually matches the latest UEFI Spec version at http://www.uefi.org/specs/)

EDK_UEFI64 - EDK based UEFI 2.1 x86_64 64-bit firmware (this may be removed in future)

The Efildr20 files support booting only from a FAT32 partition, not FAT12/FAT16 (if "com" bootsector file are used"

In UDK_X64 , I replaced DuetPkg/FSVariable/FSVariable.inf with MdeModulePkg/Universal/Variable/EmuRuntimeDxe/EmuVariableRuntimeDxe.inf , otherwise it leads to Windows 7 x64 Blue Screen and Archlinux x86_64 Kernel Panic if FSVariable is used.


The Shell binary included is the Shell of UDK/EDK2's ShellBinPkg (Beta Shell), not EdkShellBinPkg.


To setup the DUET USB flash drive in Windows, you will also need to download "HP USB Disk Storage Format Utility" from this link http://www.4shared.com/file/143511399/975c2e6/HP_USB_Disk_Storage_Format_Utility.html . This utility partitions the USB flash device as MBR, as required by DUET. Formatting the USB flash drive directly using Windows will lead to a non-partitioned USB "superfloppy" which will not boot DUET.


To launch UEFI Shell, go to (after booting DUET USB) :-

Boot Maintenance Manager -> Boot from file -> UEFI_DUET -> efi -> Shell -> Shell.efi


Check whether DUET (especially UDK_X64) works in your system. It is known to work properly only in Intel Processor+Chipset combination systems. I would like to get feedback from users of AMD processor and/or NVIDIA chipset systems.

For any queries reply in this forum link - http://www.insanelymac.com/forum/index.php?showtopic=186440 or send a mail to the.ridikulus.rat aattee gemmmaiel ddoooottii coome.
