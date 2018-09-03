# Firewall\(固件\)

In[electronic systems](https://en.wikipedia.org/wiki/Electronic_system)and[computing](https://en.wikipedia.org/wiki/Computing),**firmware**[\[a\]](https://en.wikipedia.org/wiki/Firmware#cite_note-2)is a specific class of computer[software](https://en.wikipedia.org/wiki/Computer_software)that provides the low-level control for the device's specific[hardware](https://en.wikipedia.org/wiki/Computer_hardware). Firmware can either provide a standardized operating environment for the device's more complex[software](https://en.wikipedia.org/wiki/Software)\(allowing more[hardware-independence](https://en.wikipedia.org/wiki/Porting)\), or, for less complex devices, act as the device's complete[operating system](https://en.wikipedia.org/wiki/Operating_system), performing all control, monitoring and data manipulation functions. Typical examples of devices containing firmware are[embedded systems](https://en.wikipedia.org/wiki/Embedded_systems), consumer appliances, computers, computer peripherals, and others. Almost all electronic devices beyond the simplest contain some firmware.

Firmware is held in[non-volatile memory](https://en.wikipedia.org/wiki/Non-volatile_memory)devices such as[ROM](https://en.wikipedia.org/wiki/Read-only_memory),[EPROM](https://en.wikipedia.org/wiki/EPROM), or[flash memory](https://en.wikipedia.org/wiki/Flash_memory). Changing the firmware of a device may rarely or never be done during its lifetime; some firmware memory devices are permanently installed and cannot be changed after manufacture. Common reasons for updating firmware include fixing bugs or adding features to the device. This may require ROM[integrated circuits](https://en.wikipedia.org/wiki/Integrated_circuit)to be physically replaced, or flash memory to be reprogrammed through a special procedure.[\[2\]](https://en.wikipedia.org/wiki/Firmware#cite_note-3)Firmware such as the[ROM BIOS](https://en.wikipedia.org/wiki/ROM_BIOS)of a personal computer may contain only elementary basic functions of a device and may only provide services to higher-level software. Firmware such as the program of an embedded system may be the only program that will run on the system and provide all of its functions.

Before the inclusion of integrated circuits, other firmware devices included a[discrete](https://en.wikipedia.org/wiki/Semiconductor_diode)semiconductor[diode matrix](https://en.wikipedia.org/wiki/Diode_matrix). The[Apollo guidance computer](https://en.wikipedia.org/wiki/Apollo_guidance_computer)had firmware consisting of a specially manufactured[core memory](https://en.wikipedia.org/wiki/Magnetic-core_memory)plane, called "[core rope memory](https://en.wikipedia.org/wiki/Core_rope_memory)", where data was stored by physically threading wires through \(1\) or around \(0\) the core storing each data bit.

## History

Ascher Opler coined the term "firmware" in a 1967[Datamation](https://en.wikipedia.org/wiki/Datamation)article.[\[4\]](https://en.wikipedia.org/wiki/Firmware#cite_note-Opler-5)Originally, it meant the contents of a writable[control store](https://en.wikipedia.org/wiki/Control_store)\(a small specialized high speed memory\), containing[microcode](https://en.wikipedia.org/wiki/Microcode)that defined and implemented the computer's[instruction set](https://en.wikipedia.org/wiki/Instruction_set), and that could be reloaded to specialize or modify the instructions that the[central processing unit](https://en.wikipedia.org/wiki/Central_processing_unit)\(CPU\) could execute. As originally used, firmware contrasted with hardware \(the CPU itself\) and software \(normal instructions executing on a CPU\). It was not composed of CPU machine instructions, but of lower-level microcode involved in the implementation of machine instructions. It existed on the boundary between hardware and software; thus the name "firmware". Over time, popular usage extended the word "firmware" to denote any computer program that is tightly linked to hardware, including processor machine instructions for[BIOS](https://en.wikipedia.org/wiki/BIOS),[bootstrap loaders](https://en.wikipedia.org/wiki/Booting), or the control systems for simple[electronic devices](https://en.wikipedia.org/wiki/Consumer_electronics)such as a[microwave oven](https://en.wikipedia.org/wiki/Microwave_oven),[remote control](https://en.wikipedia.org/wiki/Remote_control), or[computer peripheral](https://en.wikipedia.org/wiki/Computer_peripheral).

## Applications\[[edit](https://en.wikipedia.org/w/index.php?title=Firmware&action=edit&section=2)\]

### Personal computers\[[edit](https://en.wikipedia.org/w/index.php?title=Firmware&action=edit&section=3)\]

[![](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/AMI_486DX_EISA_BIOS_20051109.jpg/220px-AMI_486DX_EISA_BIOS_20051109.jpg)](https://en.wikipedia.org/wiki/File:AMI_486DX_EISA_BIOS_20051109.jpg)



ROM [BIOS](https://en.wikipedia.org/wiki/BIOS) firmware on a [Baby AT](https://en.wikipedia.org/wiki/Baby_AT) [motherboard](https://en.wikipedia.org/wiki/Motherboard)

In some respects, the various firmware components are as important as the[operating system](https://en.wikipedia.org/wiki/Operating_system)in a working computer. However, unlike most modern operating systems, firmware rarely has a well-evolved automatic mechanism of updating itself to fix any functionality issues detected after shipping the unit.

The BIOS may be "manually" updated by a user, using a small utility program. In contrast, firmware in storage devices \(harddisks, DVD drives, flash storage\) rarely gets updated, even when flash \(rather than ROM\) storage is used for the firmware; there are no standardized mechanisms for detecting or updating firmware versions.

Most computer peripherals are themselves special-purpose computers. Devices such as printers, scanners, cameras and[USB flash drives](https://en.wikipedia.org/wiki/USB_flash_drive)have internally stored firmware; some devices may also permit field upgrading of their firmware.

Some low-cost peripherals no longer contain non-volatile memory for firmware, and instead rely on the host system to transfer the device control program from a disk file or CD.[\[5\]](https://en.wikipedia.org/wiki/Firmware#cite_note-6)

### Consumer products

As of 2010, most[portable music players](https://en.wikipedia.org/wiki/Portable_music_player)support firmware upgrades. Some companies use firmware updates to add new playable file formats \(codecs\);[iriver](https://en.wikipedia.org/wiki/Iriver)added[Vorbis](https://en.wikipedia.org/wiki/Vorbis)playback support this way, for instance. Other features that may change with firmware updates include the GUI or even the battery life. Most[mobile phones](https://en.wikipedia.org/wiki/Mobile_phone)have a[Firmware Over The Air](https://en.wikipedia.org/wiki/Firmware_Over_The_Air)firmware upgrade capability for much the same reasons; some may even be upgraded to enhance reception or sound quality, illustrating that firmware is used at more than one level in complex products \(in a CPU-like[microcontroller](https://en.wikipedia.org/wiki/Microcontroller)versus in a[digital signal processor](https://en.wikipedia.org/wiki/Digital_signal_processor), in this particular case\).

### Automobiles

Since 1996, most[automobiles](https://en.wikipedia.org/wiki/Automobile)have employed an on-board computer and various sensors to detect mechanical problems. As of 2010, modern vehicles also employ computer-controlled[anti-lock braking systems](https://en.wikipedia.org/wiki/Anti-lock_braking_system)\(ABS\) and computer-operated[transmission control units](https://en.wikipedia.org/wiki/Transmission_control_unit)\(TCUs\). The driver can also get in-dash information while driving in this manner, such as real-time fuel economy and tire pressure readings. Local dealers can update most vehicle firmware.

## Examples

Examples of firmware include:

* In consumer products:
  * Timing and control systems for [washing machines](https://en.wikipedia.org/wiki/Washing_machine)
  * Controlling sound and video attributes, as well as the channel list, in modern[TVs](https://en.wikipedia.org/wiki/TV)
  * [EPROM](https://en.wikipedia.org/wiki/EPROM) chips used in the Eventide H-3000 series of digital music processors
* In computers:
  * The [BIOS](https://en.wikipedia.org/wiki/BIOS) found in IBM-compatible personal computers
  * The [\(U\)EFI](https://en.wikipedia.org/wiki/Extensible_Firmware_Interface)-compliant firmware used on [Itanium](https://en.wikipedia.org/wiki/Itanium) systems, Intel-based computers from [Apple](https://en.wikipedia.org/wiki/Apple_Inc.), and many Intel desktop computer motherboards
  * [Open Firmware](https://en.wikipedia.org/wiki/Open_Firmware), used in [SPARC](https://en.wikipedia.org/wiki/SPARC)-based computers from [Sun Microsystems](https://en.wikipedia.org/wiki/Sun_Microsystems) and [Oracle Corporation](https://en.wikipedia.org/wiki/Oracle_Corporation),[PowerPC](https://en.wikipedia.org/wiki/PowerPC)-based computers from Apple, and computers from [Genesi](https://en.wikipedia.org/wiki/Genesi)
  * [ARCS](https://en.wikipedia.org/wiki/ARCS_%28computing%29), used in computers from [Silicon Graphics](https://en.wikipedia.org/wiki/Silicon_Graphics)
  * [Kickstart](https://en.wikipedia.org/wiki/Kickstart_%28Amiga%29), used in the [Amiga](https://en.wikipedia.org/wiki/Amiga) line of computers \([POST](https://en.wikipedia.org/wiki/Power-on_self-test), hardware init + [Plug and Play](https://en.wikipedia.org/wiki/Plug_and_Play) [auto-configuration](https://en.wikipedia.org/wiki/Autoconfig) of peripherals,[kernel](https://en.wikipedia.org/wiki/Kernel_%28computing%29), etc.\)
  * [RTAS](https://en.wikipedia.org/wiki/Run-Time_Abstraction_Services)\(Run-Time Abstraction Services\), used in computers from [IBM](https://en.wikipedia.org/wiki/IBM)
  * The[Common Firmware Environment](https://en.wikipedia.org/wiki/Common_Firmware_Environment)\(CFE\)
* In [routers](https://en.wikipedia.org/wiki/Residential_gateway) and [firewalls](https://en.wikipedia.org/wiki/Firewall_%28computing%29):
  * [LibreCMC](https://en.wikipedia.org/wiki/LibreCMC) – a 100% [free software](https://en.wikipedia.org/wiki/Free_software) router distribution based on the [Linux-libre](https://en.wikipedia.org/wiki/Linux-libre) kernel
  * [IPFire](https://en.wikipedia.org/w/index.php?title=IPFire&action=edit&redlink=1) – an [open-source](https://en.wikipedia.org/wiki/Open-source_software) firewall/router distribution based on the [Linux kernel](https://en.wikipedia.org/wiki/Linux_kernel)
  * [fli4l](https://en.wikipedia.org/wiki/Fli4l)– an open-source firewall/router distribution based on the Linux kernel
  * [OpenWrt](https://en.wikipedia.org/wiki/OpenWrt) – an open-source firewall/router distribution based on the Linux kernel
  * [m0n0wall](https://en.wikipedia.org/wiki/M0n0wall) – an embedded firewall distribution of [FreeBSD](https://en.wikipedia.org/wiki/FreeBSD)
* In [NAS](https://en.wikipedia.org/wiki/Network-attached_storage)systems:
  * [NAS4Free](https://en.wikipedia.org/wiki/NAS4Free) – an open-source NAS operating system based on FreeBSD 9.1
  * [Openfiler](https://en.wikipedia.org/wiki/Openfiler)– an open-source NAS operating system based on the Linux kernel


