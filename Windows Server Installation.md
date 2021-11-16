# Windows Server 2019 Installation
I am using Oracle VM Box as a virtualized space to install Windows Server 2019. </br>
https://www.virtualbox.org/

I have downloaded Windows Server 2019 ISO from Microsoft’s ‘Evaluation Center’, it’s a free product given for testing.
https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2019



## The first step is deploying the Windows Server on Oracle VM Box

<img src="Pictures/First.png" width="1000">

## Choosing the memory size for the OS

<img src="Pictures/Second.png" width="400">

## Creating a virtual hard drive

<img src="Pictures/Third.png" width="400">

## Choosing the hard disk type
VDI is the default disk format in Oracle VM Box, it supports Windows Server 2019 amongst other OSs. 

<img src="Pictures/Fourth.png" width="400">

## Choosing either a dynamic or a fixed size hard disk
Dynamic hard disk is preferred as it allows for a maximum sized disk without assigning non required space.

<img src="Pictures/Fifth.png" width="400">

## Placing the VDI file and choosing a maximum size for the disk

<img src="Pictures/Sixth.png" width="700">

# Updating the virtual machine's settings

Open the 'Storage' tab and click on the empty storage device (has a disk-shaped icon). Then, click on the disk-shaped icon on the right side and click 'Choose a disk file...' Insert the Windows Server ISO file.

<img src="Pictures/Settingsone.png" width="400">

The network settings could be configured as the following:

<img src="Pictures/Network1.png" width="400">

<img src="Pictures/Network2.png" width="400">

