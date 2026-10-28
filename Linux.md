# Linux

## CONTENTS

- What to find
    - Linux & hardware
        - Debian
            - Install: failure in login (command line or GUI)
                - duainstall with UEFI
                - packages: environment-modules,
                - error
            - Linux common structure
                - Partition Network OS & Kernel NVIDIA Hangul GNOME (dconf-editor, gsettings)  Printer VM (Virtual Box, VMware) Error
                - Basic Package (pip, cmake) network
                - Common Package ( anaconda, docker ) QChem ( VASP Science Package Autotools Makefile Library html teamviewer\_uninstall
                - Linux common command sudo
            - OpenSUSE
                - SGE
            - Machine

Cluster(PBS) Nurion – EEWS server

- SuperUser Management and shell programming

Shell bash tcsh, Shell\_command special shell command (sed, awk, gawk, xargs) Linux Programming - Shell programming,  RE Environment Environment Modules Cluster installation Cluster control PBS Slurm Process control Linux Programming Some techniques SQL vim

GitHub & GIT

```text
git two remote repo
```

- GnuPlot
    - TCL/Tk
        - Ubuntu
            - CentOS 7
            - Installation mount utilities
            - Install Package
                - printer, teamviewer, virtual box, visual package, graphic packages, Science Package

<br>

## Search

anaconda: conda, jupyter notebook, jupyterlab

system: sound (speaker and mic),

hardware install: hdd, &#9;&#9;

linux skill, change owner/group of directory

video capture,

vmware, virtualbox,

zoom,

<br>

## System Spec

## Distribution

### find distribution

- /etc/os-release
    - ` grep . /etc/*-release `
    - cat /etc/\*-release \| uniq
- /etc/issue\*
    - ` grep . /etc/issue* `
- Redhat
    - rpm –qa \*-release
- Linux kernel
    - uname –a
        - 3.16.0-4-amd64
    - cat /etc/issue
    - lsb\_release –da
    - hostnamectl

### Debian:

- Debian project
    - the strongest point of Debian comes from the core of Debian, namely, its package management
    - sid: development version
    - 10: buster
    - 11: bullseye
- properties
    - ubuntu is trial version
    - install by CD 1:  Now try using CD, Debian 10.0
- version check
    - cat /etc/os-release

### Ubuntu

- Download server version
    - Long time secured LTS version
        - 16.04
    - https://www.ubuntu.com/download/server
- rufus
    - Ubuntu install usb maker
    - https://kjvvv.kr/2635

### Redhat

- related distribution
    - Fedora
    - CentOS: Community enterprise Operating System
    - Opensuse
- Redhat software
    - [http://rpm.pbone.net/index.php3](<http://rpm.pbone.net/index.php3>)

### making bootable usb/DVD

- windows
    - download .iso file in distribution website
    - rutus
- in linux
    - Bracero in debian
        - making bootable DVD
            - xorriso
                - doable as user
                - xorriso –as cdrecord –v dev=/dev/sr0 –eject \*.iso
            - growisofs
                - for DVD and BD
                - growisofs –dvd-compat –Z /dev/sr0=\*.iso
        - making bootable CD
            - wodim
                - wodim –v dev=/dev/sr0 –eject –sao \*.iso
        - making bootable usb

## Run Linux OS

### Root

- Root operating
    - Etc
        - /etc/ini.d
        - /etc/init.d
        - /etc/inittab

### multi boot

- grub
    - choose the installed OS
    - appears
        - the newest linux at the top
        - advanced option for linux
            - there are several version of kernel
        - Windows also
    - when kernel changed, grub changes
        - cf. kernel update and update-grub
- in case fail to usb booting from CMOS (del)
    - use F10 for direct boot disk selection
- grub broken error
    - windows disappears in grub
        - sudo os-prober
            - shows windows OS is alive
        - if windows are alive
            - possibility
                - Grub entry only disappeard
                - EFI boot order changed
        - modify
            - ` sudo vi /etc/default/grub `
            - ` GRUB_DISABLE_OS_PROBER=false	! remove comment out `
        - sudo update-grub
            - shows windows
                - Found Windows Boot Manager on /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi
                - Found Windows Boot Manager on [/dev/sdc1@/efi/Microsoft/Boot/bootmgfw.efi](<mailto:/dev/sdc1@/efi/Microsoft/Boot/bootmgfw.efi>)
        - is this related with kakao talk error  can’t not login

### boot

- booting
    - boot with /etc/passwd
        - there is shell and home directory
    - shell reads /etc/profile
        - set env variables
            - PATH, PS1
        - this run /etc/profile.d/\*sh
            - bash\_completion.sh
                - /usr/share/bash-completion/bash\_completion
            - vte
                - terminal,
        - this calls /etc/\{system shell\}
    - /etc/\{system shell\}
        - Such as
            - /etc/csh
            - /etc/bash
            - /etc/tcshrc
    - ~/.profile is called
        - In bash, run one of three files
            - ~/.bash\_profile
            - ~/.bash\_login
            - ~/.profile
        - in one of the three files
            - . ~/.bashrc
    - .bashrc
        - add user initial setup in .
    - /etc/motd
        - Motd: message of the day
        - It runs after successful login
- run level
    - level in booting  term is changed to target after systemctl introduced
    - run level
        - 0&#9;poweroff.target
        - 1&#9;rescue.target
        - 3 multi-user.target
        - 5&#9;graphical.target
        - 6&#9;reboot.target
- management target
    - basic
        - confirm basic target: get-default
        - GUI: graphical.target
        - server: multi-user.target&#9;
    - list-units --type target
        - system target list
    - change target
        - set-default: reflected at booting
        - isolate: prompt reflection in the present session&#9;cf. NVIDIA

## Hardware

### system check

- inxi -Fxz
    - system
    - Machine
    - CPU
    - Graphics
    - Audio
    - Network
    - Drives
    - Parition
    - Sensors
    - Info
- inspect system logs
    - journal --no-pager -b -0 \| grep -9 \> journal.gz

### howtocheck

- Motherboard
    - sudo dmidecode \| grep ‘Product Name’
- CPU
    - lscpu
    - /proc/cpuinfo
- Memory
    - dmidecode -t 17 \| grep “Locator\\\|Size” \| grep -v Bank
- Graphic Card
    - lspci \| grep -E “AMD\|NVIDIA”
- hard disk
    - check hard disk connection
        - lsblk -o "NAME,MAJ:MIN,RM,SIZE,RO,FSTYPE,MOUNTPOINT,UUID"
        - lsblk -o NAME,SIZE,FSTYPE,MOUNTPOINT
            - sda&#9;465 G&#9;vfat&#9;ntfs
            - sdb&#9;1.8 T&#9;ext4&#9;/Storage
            - sdc&#9;238 G&#9;vfat&#9;ntsf
            - sdd&#9;238 G&#9;vfat boot/efi, ext4 /, ext4 /home
    - install smartctl
        - ` sudo apt-get install smartmontools `
    - sudo smartctl -i /dev/harddisk (such as sda,
        - -a: many info
- Peripheral device
    - power supply
        - dmidecode --type 39
            - does not show manufacturer

### motherboard

- sudo dmidecode \| grep ‘Product Name’
    - X9DAi
        - [https://www.supermicro.com/products/motherboard/Xeon/C600/X9DAi.cfm](<https://www.supermicro.com/products/motherboard/Xeon/C600/X9DAi.cfm>)
    - download mother board manual

Figure 1 Mother board

### cpu

- definition
    - system composition and operating principle
    - relation between components
- manufacturer
    - Intel Core i7 ~ i9 vs AMD Ryzen 9, 7
    - Intel
    - AMD
- CLI
    - centos
        - cpuinfo
        - lscpu
    - debian
        - lscpu
    - cat
        - /proc/cpuinfo
- processor
    - core and thread
    - core
        - physical unit that can execute instruction independently
        - cpu can have multiple cores  run multiple tasks simultaneously
        - more independent tasks can be run concurrently
    - thread
        - logical software unit that can run on a single core  independently of other threas
        - threads share the same memory space and resources as the process that created them
        - optimized for parallel execution
- architecture of CPU
    - /proc/cpuinfo
        - present: Intel Xeon
    - lscpu&#9;&#9;cf lscpu in command

|  | 32 bit | 64 bit |
| --- | --- | --- |
| architecture | i686 | x86\_64 |
| cpu op-mode | 32-bit | 32-bit, 64-bit |
| Model name |  | Intel Xeon (chi)<br>Intel Core i7 (eta) |

- cat /proc/cpuinfo
    - chi: Intel Xeon E5-2620
        - eta: Intel Core i7
    - cpu info
        - [https://ark.intel.com/content/www/us/en/ark/products/75789/intel-xeon-processor-e5-2620-v2-15m-cache-2-10-ghz.html](<https://ark.intel.com/content/www/us/en/ark/products/75789/intel-xeon-processor-e5-2620-v2-15m-cache-2-10-ghz.html>)
        - performance
            - # of cores: 6
            - # of Threads: 12
    - Ncores
        - Number of socket (physical cpu)
        - Number of core / socket
        - Number of thread / core
    - many channels increase the speed by parallelized work
        - so 8G × 8 (4 per cpu) would be best
    - cpu temperature
        - install lm-sensors
            - ` sudo yum install lm_sensors `
        - configuration
            - sudo sensors-detect
                - almost YES
                - configuration files in /etc/conf.d/lm\_sensors
                    - used by lm\_sensors.service for loading kernel modules on boot
        - $sensors
            - each core shows temperature: current T (high T, critical T)
                - if current T reaches high T or critical T
                    - should check hardwares
        - watch sensors
            - real time monitor
- zeon
    - have x86\_64
    - use AMD64
- X86 or 80x86
    - IA-32: Intel Architecture of 32 bit
    - IA-64 is 64 bit just for Intel Itanium 64 bit processor
- Samsung
    - 1 socket, 8 cores, 2 threads per core

### memory

- spec
    - [http://plan.danawa.com/info/?nPlanSeq=4465](<http://plan.danawa.com/info/?nPlanSeq=4465>)
    - basic spec
        - DDRN  DDR4
            - DDR: Double Data Rate
        - clock  2226, etc
        - capacity  8, 16 GB
    - depending on system
        - PC: 2 memory controllers
        - server: 4 ~ 6 memory controllers
    - hardware shape
        - different slot for different version
- memory specification
    - memory type: DDR3
    - max # of memory channel: 4
        - new system has 6 channels
            - cpu have 6 memories for maximum speed
- debian
    - lshw -short
        - 8 GiB DDR4 2667 MHz
- centos
    - memory is the first instability source
    - per cpu
        - should equip two same memories
            - cpu writes both halves to both memories
    - kinds
        - U: un-buffered for PC
        - E: ECC un-buffered for server mother board, also useful for PC
        - R: ECC register for server only
        - 2R/1R
            - DDR2 2R is better
            - DDR3 1R is better
    - sudo dmidecode -t 17
        - shows all the memory slots
        - Locator: slot name
        - if Size, it is installed, if not, empty
        - Type: DDR3
        - dmidecode -t 17 \| grep “Locator\\\|Size” \| grep -v Bank
    - memory installation in X8Dai
        - 2 CPU
            - 4 RAM: A1, B1; E1, F1
                - use A1, B1 (16G); E1, F1 (8G)
            - optimization with 8 RAM (4 channels per cpu)
                - A1, B1, C1, D1, E1, F1, G1, H1
            - 6 RAM: A1, B1, C1, D1; E1, F1
    - present
        - A1, C1 (16G); E1, G1 (8G)

### graphic card

- classify by company
    - company & brand
        - NVIDIA: Geforce
        - ATI: Radeon
    - chip set company
        - intel, nvidia, ati(amd)
    - graphic card company
        - IMTech, Asus, Gigabite
- check graphic card spec
    - lspci \| grep -E “AMD\|NVIDIA”
    - dpkg -l \| grep xorg

### storage

- kinds
    - NVMe drives (modern SSD, Solid State Drive)
        - Non Volatile Memory Express
        - /dev/nvme0n1p1: partition 1 of NVMe drive 0, namespace 1
    - SATA/USB/HDD drives
        - hdd: hard disk driver,
        - /dev/sda, /dev/sdb, /dev/sdc, etc.
- hard disk
    - performance
        - speed
        - stability
    - storage kind
        - NAS: Network-Attached Storage
        - DAS: Direct-Attached Storage
    - maker
        - Backblaze: estimation of error rate of HDD
        - HGST \>\> Tochiba \> WD \>\>\> Seagate by choi
        - up to 2017
            - Seagate: over 25%
            - HGST (Hitache Global Storage Technologies): \<= 1%
            - Western Digital - best at the moment
            - Toshiba
- installation
    - /dev/sdd&#9;&#9;# physical harddisk driver is detecting
        - /dev/sdd1, sdd2&#9;# partition is detected
            - how to use hard disk
                - ` make partition using gdisk `
                - format using mkfs
                - register in fstab using uuid and mount point
    - install smartctl through smartmontools packages
    - sudo smartctl -a /dev/sda
        - Samsung SSD
        - 256GB
    - overall health check
        - #smartctl /dev/sda -H
            - …. PASSED
    - self test
        - subcommand: offline, short, long, conveyance, force, vendor, N, select, M-N, pending,
        - smartctl -t short /dev/sda
            - it will show the finish time
            - then,
                - smartctl -l selftest /dev/sda
    - comprehensive health status
        - smartctl --xall /dev/sda

### Network

- infiniband
    - lspci \| grep -i infiniband
        - or lspci \| grep -i Mellanox
    - ibstat
        - shows
            - CA ‘ibp24s0’ …
    - ip link
        - infiniband: ib0, ib1
        - Ethernet: eth0, eno1, ens3f0, …
- Switches
    - infiniband
        - NVIDIA/Mellanox
            - model: Quantum, Quantum-2…
        - Cable
            - QSFP56, … thicker, short, often labeled ‘200G/400G IB”

### eta & hardware command

- lshw
    - ` sudo apt-get install lshw `
    - usage
        - sudo lshw -short
        - sudo lshw -html \> hardwareinfo.html
- lsblk -o NAME,SIZE,TYPE,MOUNTPOINT,MODEL
- hw
    - NVMe 256 GB linux
    - SATA SSD 500 GB sda
    - SATA SSD 250 GB sdc
    - HDD       2 TB sdb

## Linux Core

### OS version

- /etc/os-release -\> /usr/lib/os-release
    - ` grep . /etc/*-release `
- /etc/issue
    - ` grep . /etc/issue* `
- /etc/debian\_version

### kernel

- kernel check
    - uname
        - uname -a: for all
        - uname -r
    - location
        - /boot
        - /usr/src
    - available kernel check
        - ` apt search linux-headers `
- kernel errors
    - case 1
        - some odd package installation, some apps collide and are broken
        - remove the recent kernel and reinstall the new kernel again
    - wrong kernel version in /boot
        - /boot
            - config-5.15.12
        - /sur/src
            - linux-headers-5.10.0-19-amd64
- kernel update
    - boot in the old stable kernel in grub
        - cf grub
    - check kernels
        - dpkg -l \| grep linux-
    - remove excess kernel
        - when the newest version is 5.10
            - leave two versions of old kernel such as 4.19.0-1, 4.19.0-20
        - remove
            - dpkg -r linux-image-4.19.0-14-amd64
            - ` apt remove --purge linux-image-4.19.0-17-amd64 `
                - N.B. the directory is not removed
            - ` apt-get remove --purge linux-image-5.10.120-1-amd64 linux-headers-5.10.120-1-amd64 `
                - ` apt-get remove --purge linux-image-5.10* `
    - update & clean
        - check sources.list
            - ` make empty /etc/apt/sources.list.d `
                - copy sources.list.d/\* sources.list.old/
                - (cf.) remove the problematic packages
                    - (deb) dpkg -l \| grep \[docker, etc \]
                        - dpkg -r docker\*
                - remove VB
        - ` apt-get update `
        - ` apt-get full-upgrade `
        - ` apt autoremove `
            - if update is done
            - check
                - dpkg -l \| grep linux
    - reinstall the new kernel
        - reinstall
            - ` apt-get reinstall linux-image-5.10.0-21-amd64 linux-headers-amd64 `
        - check
            - dpkg -l \| grep linux-
                - new kernel version
            - ls /boot
                - new kernel appears
            - lib/modules
                - remove wrong version
                    - rmmod /lib/modules/linux-version
                        - linux-version is directory
                        - rmmod might not remove
                    - rm -rf /lib/modules/linux-version
        - cf.
            - if not working, kernel build
                - [https://techviewleo.com/how-to-install-linux-kernel-on-debian/](<https://techviewleo.com/how-to-install-linux-kernel-on-debian/>)
                - escape kernel build for the stability is not guaranteed
    - grub update
        - update-grub
            - only available kernels appear
    - reboot
        - the newest version should be the installed version
        - (normal)
            - ` apt-get full-upgrade  if Done `
        - recover /etc/sources.list.d

### desktop

- ls /usr/bin/\*session
    - gnome
    - mate
    - lxde
    - jwm -\> icewm
- env \| grep DESKTOP\_SESSION
    - ` DESKTOP_SESSION=gnome-xorg `
- GUI in login
    - Kinds
        - GNOME, GNOME Classic, GNOME on Xorg
    - GNOME
        - is based on the Wayland backend
        - Wayland
            - newer interface with security and bugfixes than xorg
            - not Xorg
        - cf. teamviewer
            - do not use wayland for teamviewer
    - GNOME on Xorg
        - uses Xorg in GNOME
        - Client/server model
    - How to check the present X
        - $echo $XDG\_SESSION\_TYPE

### hostname & ip

- /etc/hostname
- /sbin/ifconfig

### groups

- $groups
    - to find groups where I belong
- /etc/group
    - entire group list in
    - check group members in a group
    - cut –d: -f1 /etc/group

### Samsung in EE

- cpu
    - 1 socket, 8 cores, 2 threads
    - intel i7-10700
- memory
- graphic card

## Software

### bios

- how to update bios

### bus

- kinds
    - I/O bus
    - memory bus
- speed
    - PCI \>\>\> SATA \>\> IDE

### PCI

- Peripheral Component Interconnect
    - kinds
        - 32 bit PCI
        - PCI eXtended

### SATA

- SATA I: 1.5Gb/s (width: 150MB/s)
- SATA II: 3Gb/s (width: 300 MB/s)
- SATA III: 6Gb/s (width: 600 MB/s)
    - SATA III and SATA 3 are different

### AHCI

- Advanced
- compose SATA SSD

### NVMe

- Non-Volatile Memory Express
    - PCIe based SSD
- used in
    - PCIe card slot
    - M.2
    - U.2
        - only use NVMe

## Files and Terminology

### AHCI

- Advanced Host Controller Interface
    - used

### back\|front end

- back end: for data
- front end: for visual

### CLI (cf. GUI)

- command line interface
    - all-text display mode provided in console or terminal window by a shell
- other name
    - text-based user interface
    - command-line user interface
    - console user interface
    - character user interface
- app
    - users type commands in the command line interface to run task on a computer

### console

- all-text display mode that occupies the entire display monitor screen
- cf. terminal
    - text-only window that emulates a console
    - can be opened on a GUI screen

### dmi

- desktop management interface
    - dmidecode for mother board specification

### MBR

- master boot Record
- booting order
    - switch \> rom bios \> MBR in the first sector \> partition of OS sector \> load OS
- MBR is on cylinder 0, head 0, sector 1

### pci

- Peripheral component interconnect
    - Local computer bus for attaching hardware devices
    - cf. lspci

### (command) prompt

- prompt or command prompt
- short text message at the start of the command line on CLI

### port

- ` mv to network port `

### hardware port

- physical peripheral connecting point to a machine

### NVMe vs AHCI

### socket

- combination of software port and IP address

### storage

- memory
- primary storage
- secondary storage
    - known as external memory or auxiliary storage
    - not directly accessible by CPU
    - types
        - HDD and SSD
        - optical storage: CD, DVD
        - USB,
- tertiary storage
    - cloud storage

### protocol number

- different from port number

### schema

- similar to scheme

### ssd

- usage
    - SATA, PCIe slot, M.2
        - AHCI
    - cf. U.2 only for NVMe

### volatile

- non-volatile
    - retaining data when its power is shut off

### wheel

- group with superuser authority

## Errors

### lack of free space

- Debian
    - filesystem root is full
        - df -h: 99 % usage of root
    - remove
        - check
            - sudo du -hxd1 / \| sort -hr \| head -n 20
        - basic
            - ` sudo apt clean `
            - ` sudo apt autoclean `
            - ` sudo apt autoremove `
        - remove logfile
            - sudo du -sh /var/log/\*
            - sudo rm -f /var/log/\*.gz /var/log/\*.1
                - this lowered root usage from 99 % to 55 %
            - sudo journalctl --vacuum-time=3d   # Keep logs only 3 days
        - check /tmp/
            - sudo du -sh /tmp /var/tmp
            - sudo rm -rf /tmp/\*
            - sudo rm -rf /var/tmp/\*
- remove logfiles
    - logfiles
        - \*.1: rotated log files
        - \*.gz: compressed older logs
            - thes files can grow to several GB if system logs a lot
    - sudo journalctl --vacuum-time=3d   # Keep logs only 3 days
- limit size on /var/log/journal
    - sudo nano /etc/systemd/journald.conf
        - \[Journal\]
        - SystemMaxUse=500M
        - SystemKeepFree=1G
        - SystemMaxFileSize=100M
        - MaxRetentionSec=7day
    - sudo systemctl restart systemd-journald
- remove using crontab scheduler
    - sudo nano /usr/local/bin/log\_cleanup.sh
        - ` #!/bin/bash `
        - # Delete rotated/compressed logs
        - rm -f /var/log/\*.gz /var/log/\*.1
        - # Vacuum systemd journal older than 3 days
        - journalctl --vacuum-time=3d
    - ` sudo chmod +x /usr/local/bin/log_cleanup.sh `
    - sudo crontab -e
        - @weekly /usr/local/bin/log\_cleanup.sh
- alternative system Timer
    - create service
        - ` sudo vi /etc/system/system/log-cleanup.service `
            - \[Unit\]
            - Description=Clean up system logs
            - \[Service\]
            - Type=oneshot
            - ExecStart=/usr/local/bin/log\_cleanup.sh
    - create timer
        - ` sudo vi /etc/system/system/log-cleanup.timer `
            - \[Unit\]
            - Description=Run log cleanup weekly
            - \[Timer\]
            - OnCalendar=weekly
            - Persistent=true
            - \[Install\]
            - WantedBy=timers.target
    - enable timer
        - sudo systemctl daemon-reexec
        - sudo systemctl daemon-reload
        - sudo systemctl enable --now log-cleanup.timer
    - check it
        - systemctl list-timers \| grep log-cleanup

<br>

## Debian

## Basic Characteristic

### Debian

- new version in 2 years
- 6 years for maintenance

### Versions Characteristic

- v10: buster
    - no collision between anaconda virtual env and GUI
        - Centos has collision so turn off anaconda when logout
    - other characteristics
        - Hangul recommendation is nabi
            - Type hangul is not working
            - ` sudo apt-get install nabi `
        - ibus is OK
            - ` sudo apt-get install ibus ibus-hangul `
                - nabi is still alive
                - select Korean (Hangul)
                    - type is working
                - bad behavior in skype in linux
            - ibus makes problem in google-chrome
                - in hangul mode, back space and return keys are not working
        - printer is auto detected
            - when it is not detected in app
                - power button/setting/printers
                    - unlock to install
                    - if finding printer  add
                        - then it appears in app
                    - else
- sid: for the upgrade version
    - will be v11 later
    - do not install sid

### version update

- ` sudo apt-get dis-upgrade `

## Debian 10-11 install

### upgrade to 11

- not now
    - after VB for Debian 11 is released
- install
    - [https://doc.akito.ooo/books/essentials/page/manually-upgrade-debian-from-buster-to-bullseye](<https://doc.akito.ooo/books/essentials/page/manually-upgrade-debian-from-buster-to-bullseye>)
    - 1. su
    - 2. apt edit-sources
    - (change "buster" to "bullseye")
    - 3. apt-get udpate
    - 4. apt-get full-upgrade

### Make image file

- Download
    - CD or DVD image for usb installer
        - [https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/](<https://cdimage.debian.org/debian-cd/current/amd64/iso-dvd/>)
    - vmd64 for 64bit machine
    - Debian-9,5.0-amd64-DVD-1.iso
        - DVD-2, 3 are not necessary
    - use rufus for only one OS
        - yumi
            - old version is not working for Windows 10
            - reads only live version of Debian
- rufus for usb installer
    - [https://rufus.akeo.ie/](<https://rufus.akeo.ie/>)
        - MBR …
    - burn

### Tips for installation in advance

- setting in installation
    - time - korea
    - locale for language
        - American English
    - Network
        - watch out where it sets network
        - if you fail to set up network during installation
            - it would be troublesome to set up graphic card after installation
    - Mirror
        - If network is set correctly, mirror will works
            - [ftp.riken.jp](<ftp://ftp.riken.jp>)
        - if network is not set correctly,
            - try install using CD only  go to install without network
    - extra software
        - choose one of x-window
            - Gnome
                - Exclude xfc, kde, etc for similar x
                - this can be installed after OS installation but it would be tricky

### Install – before partition

- English – English
- locality – Asia – Korea
    - for time
- superuser ID, user ID
- hostname and domain name
    - name server is set in /etc/resolv.conf
        - nameserver 143.248.1.177

### Network (during installation)

- when is it set?
    - set ip during installation: it looks not possible
        - update is possible
    - without internet connection
        - update is not possible
        - after installation with minimum in CD, to read graphic card would fail
- network installation during installation
    - try to find network installation icon one the left-bottom during installation
        - otherwise, it will install DHCP as default
- Debian default
    - automatically check it with eth0 in v. 8.5 and enp6s0f1 in v. 9.5
    - DHCP
    - default setting
        - /etc/network/interfaces
            - ` source ../interfaces.d/* `
            - # loopback
                - auto lo
                - iface lo inet loopback
            - #primary network
                - allow-hotplug enp2s0
                - iface enp2s0 inet static
                - address 143.248.142.23
                - netmask 255.255.255.0
                - gateway 143.248.142.1
        - if modify, restart
            - service networking restart
    - go to set up after installation if GUI installation succeeds.

### partition

- 3 partition method
    - /
        - 30 GB, ext4, bootable
    - swap
        - [https://access.redhat.com/ko/solutions/744483](<https://access.redhat.com/ko/solutions/744483>)
        - 10 GB, swap
            - used as “file system: ext4, swap”
                - swap has different file system
                - do not use automatic
                    - it takes double of the memory such as 50 GB
        - thumb rule w.r.t. memory
            - ~ 64 GB memory – 10 GB
    - /home
        - remaining (210 GB), ext4, not-bootable
- other partitions

### install – postpartition

- desktop – Debian desktop environment
    - it is also GNOME
- grub is installed in the first booting disk
    - GRand Unified Bootloader
- in case of net-version, it does not make GUI

## Deb dual install w. UEFI Windows; minimum network install (quick menu)

### minimum installation with network

- try to set ip ?
    - in case no network
        - mirror fails
        - proxy set?
        - will be minimum install
- partition with EFI
    - select one partition automatic
        - /esp is made
        - then can modify separately
    - (fail and danger) trying manual or using /home
        - how to make it recognize EFI?  no EFI
        - if windows has UEFI, boot is destroyed
    - cf
        - fdisk -l
            - shows EFI System in /dev/nvme0n1p1 at /boot/efi (df shows 500 MB)
- will login at terminal

### after install

- set network
    - when failed setting in installation
    - ` vi /etc/networking/interfaces `
        - iface eth0 inet static
        - address 192.168.1.5
        - netmask 255.255.255.0
        - gateway 192.168.1.254
    - /etc/init.d/networking restart
    - check network
        - ip a
- modify /etc/apt/sources.list
    - vi
        - deb http://deb.debian.org/debian bookworm main non-free-firmware
        - deb-src http://deb.debian.org/debian bookworm main non-free-firmware
        - deb http://deb.debian.org/debian-security/ bookworm-security main non-free-firmware
        - deb-src http://deb.debian.org/debian-security/ bookworm-security main non-free-firmware
        - deb http://deb.debian.org/debian bookworm-updates main non-free-firmware
        - deb-src http://deb.debian.org/debian bookworm-updates main non-free-firmware
    - ` apt-get update ; apt-get upgrade `

### install basics

- man
- task-gnome-desktop
    - gnome tweaks
- chrome-stable
- set sudo

### gui

- check target
    - systemctl status target
- systemctl gdm start
- initial setup on left top corner

### hangul

- install ibus
- ibus-setup
- setting

### copy home

- ` rsync -avz /Storage/…home_debian . `

### other settings

- block screen saver
    - setting/power/Power Saving Options/
        - screen saver  Never
- tweaks
    - install gnome-shell-extension
    - install chrome-shell
    - open chrome and login
        - menu/installed extension
            - change all the button to on

### Try virtualbox

- check windows disk
    - fdisk -l
        - windows has 4 partitions: EFI, MS, Data, Recovery
- go on the main loop

### softwares

- gnome-screenshot
    - screenshot
- image
- movie
    - smplayer
    - vokoscreen
- pdf
    - default: document viewer
- zoom
- jscode
    - Download
        - Sudo apt install ./…deb file
    - Do not use snapd
        - install snapd
            - ` sudo apt install snapd `
            - sudo systemctl enable snapd && sudo systemctl start snapd
        - sudo snap install code –classic
    - ` $ code `
- install error
    - dpkg
        - dependency problem – leaving unconfigured
            - … not installed
        - ` apt --fix-broken install `
    - ` apt-get install `
        - ` apt --fix-broken install `
    - ` apt autoremove `
        - remove installed but not necessary library

## Deb Installation Further

### (expert) in case installation without network

- GUI would fail
    - fails to read graphic card, then screen is stopped
    - alt^F2 for terminal
    - root login
- Summary
    - Set network using #nmtui
        - Check network using ping ([www.google.com](<http://www.google.com>))
    - Check sources.list
        - Update & upgrade
    - set-default graphical.target
    - check gdm3
    - install firmware
        - ` apt install firmware-linux firmware-linux-nonfree libdrm-amdgpu1 xserver-xorg-video-amdgpu `
        - ` apt-get update `
        - systemctl start gdm
    - reboot
    - if login in command line or GUI
        - succeed. !!!
- set network in installation
    - #nmtui
        - set Ethernet connection to manual ip
            - (wired connection won’t work)
            - use back/OK after install
        - activate Ethernet connection 1
            - whenever reboot, lan is disconnected
                - just activate Ethernet connection; exit with OK
    - check ip
        - ip address
        - ip should appear at …..
    - ping [www.google.com](<http://www.google.com>)
        - should work
- edit sources.list and update
- setting graphical.target
    - systemctl stop gdm
    - systemctl status gdm
    - systemctl start gdm
    - systemctl set-default multi-user.target
    - systemctl set-default graphical.target
    - systemctl get-default
- install gdm3
    - update
    - dpkg -l \| grep gdm
        - displays
            - gdm3
            - amd64&#9;GNOME Display Manager
        - if there is not gdm3, install gdm3
    - dpkg -l \| grep xorg
        - displays
            - Nouveau
            - Intel
            - AMD/ATI display driver wrapper
                - AMD/ATI is graphic card
    - dpkg -l \| grep gnome-shell
    - update & upgrade
    - ` apt-get --reinstall install gdm3 `
    - dpkg-reconfigure gdm
    - dpkg-reconfigure gdm3
    - systemctl status gdm
        - loaded /lib/system/system/gdm.service; static
        - Active: active (running)
- check graphic card
    - lspci \| grep -E ‘AMD\|NVIDIA’
    - ` apt install firmware-linux firmware-linux-nonfree libdrm-amdgpu1 xserver-xorg-video-amdgpu `
    - ` apt-get update `
    - systemctl start gdm

### network setting&#9;&#9;&#9;&#9;cf. ip

- GUI is possible if installed by CD/DVD image
    - not possible if installed by net-version and w.o. network
- GUI-network
    - power icon or network icon
    - modify “wired connection”
    - then network is working
- nothing is changed in /etc/network
- network check
    - ping [www.google.com](<http://www.google.com>)
    - web-browser
    - ip address
        - ip a
        - ifconfig
        - hostname -I
- find port and name
    - lsof
    - netstat

### GUI

- Use GNOME xorg
    - for teamviewer
    - wayland is not supported by teamviewer

### terminal

- Software icon/search icon/ type “terminal”
    - to find terminal
        - terminal customization
        - put in favorite
- terminal kind
    - find terminal type
        - $echo $TERM
            - xterm-256color&#9;# normal setting
    - terminal types
        - linux for Linux console
        - screen for tmux
        - so many
        - check
            - infocmp screen
- mouse
    - mouse scroll button&#9;&#9;&#9;&#9;&#9;
        - terminal pane scrolls
        - in case history is scrolled
            - $tput rmcup

### kernel sources.list - mirror

- need to set up mirror
    - if Debian was installed without internet, sources.list needs to be modified to get mirror
        - basically it has only security
- [https://wiki.debian.org/SourcesList](<https://wiki.debian.org/SourcesList>)
    - /etc/apt/sources.list
        - deb, deb-src
        - deb.debian.org
            - stretch main
            - stretch-updates main
        - security.debian.org/Debian-security/ stretch/updates main
    - deb 10
        - comment # all the contents
        - deb http://ftp.debian.org/debian/  buster main contrib non-free
        - deb-src http://ftp.debian.org/debian/ buster main contrib non-free
        - deb http://security.debian.org/debian-security buster/updates main contrib
        - deb-src http://security.debian.org/debian-security buster/updates main contrib
        - deb https://download.virtualbox.org/virtualbox/debian buster contrib
- ` apt-get update `
- ` apt-get upgrade `
- install sudo
    - ` apt-get install sudo `
        - register joonho in sudo
            - “adduser joonho sudo “&#9;! this doesn’t work
            - visudo&#9;&#9;! as root
                - add “joonho ALL=(ALL) ALL”

### Sudo commands for installation

- su(bstitute)
    - default: become superuser
    - su username
        - change the user
- sudo command
    - running command with root authority
        - if not installed, install
    - set user as sudoer
        - insert sudo authority in user id cf.
    - usage
        - sudo –u username command
        - sudo command
            - input passwd
- Add user
    - adduser vs useradd
        - adduser
            - set passwd
            - makes home directory
            - options
                - -uid: define UID
                    - otherwise UID will be assigned from 1000, and goes on
        - useradd
    - del user
        - w or w/o home directory
            - cf adduser

### graphic card

- whatitis
    - lspci \| grep -E “AMD\|NVIDIA”
        - shows AMD or NVIDIA
- nvidia driver install
    - cf. cat /etc/network/interfaces

### mount file system

- summary
    - for unknown hard disk
        - hard disk will be recognized by cmos
            - then will appears in /dev
            - then /dev/disk/by-uuid is set
        - add uuid to /etc/fstab
            - follow the /home
            - determine mount point and mkdir
        - sudo mount -a
            - df will show the mount point
    - let Debian recognize Window sdd
        - try to install Debian with windows sdd put in.
- harddisk usage at the moment
    - / 30 GB assigned and 20G remained
    - /home 198G assigned and 187G remained
- df shows only sda
    - set uuid in /etc/fstab
- static file system table in /etc/fstab
    - only sda (sda1, sda5) and CD exists
    - principal partitions need to be allocated
- get uuid for disc
    - sudo blkid&#9;&#9;! or
    - ls –al /dev/disk/by-uuid
- modify fstab manually
    - similar to /home
        - file-system  mount-point  type  options   dump  pass
        - ` UUID=…..	/Data   default  0  2 `
    - Copy uuid into fstab
        - previous format
            - ` UUID=___________id__________________ /dir ext4 defaults 0 1 `
            - ` UUID=___________id_________________ /home ext4	   rw, defaults 0 2 `
    - do not include ntfs in constant mount
        - temporary mount /dev/sdc1 for backup
- ` make mount point and mount `
    - ` sudo mkdir /Data /shared /scratch	! etc for all the mount points `
    - sudo mount –a \[--all\]
- backup home and rsync backuped home
    - ` sudo mkdir ../joonho_i	! made by root `
    - ` rsync –avz ./ ../joonho_i `
    - ` rsync –avz –-delete /Data/backhome/joonho/ . `
- harddisk usage of home
    - /&#9;! 5/30 GB = 19%
    - /home&#9;! 97/198 = 52%

### tweak

- cf. GNOME
- gnome-tweak-tool is default
    - ` apt-get install –-reinstall task-gnome-desktop `
    - gnome-tweak is installed
- properties
    - install not too much
    - font is OK for 4K monitor
        - change font size in 4 K monitor&#9;cf. change size of mouse cursor

### Desktop

- upper left
    - favorate
- upper middle
    - date, time
- upper right: tray for many icons
    - power
        - screenshot
        - setting
        - Lock icon for Lock screen: Locked
            - Keeps current session
            - turn off display and shows login screen
            - Require password to unlock
            - Session remains active in memory (RAM): nothing is stopped or closed
        - power icon
            - Suspend
                - Saves session to RAM and power down most hardware to a low-power “sleep” state
                - Fans, screen, and most devices turn off
                - RAM stays powered to keep session
                - Resume by pressing a key or opening lid, it wakes up and asks passwd
                - This can be more trouble than simple Lock
                - if this makes a problem, use lock
                    - Do not suspend permanently
            - Log out
                - Ends session entirely.
                - return to the login screen (GDM)
                - use no extra memory or power
            - Power off
            - Restart

### further installation

- check list for portal
    - firefox: \*\*\*mola\*\*\*\*
    - gmail: \*\*\*gmil\*\*\*\*
- go to Debian package
    - including environment setting

### boot failure/boot error

- root directory is full  Failure in gdm.start in boot
    - @F2: move to a new terminal
        - login
    - check directory usage using ncdu
        - ` sudo apt install ncdu `
        - ncdu /
            - check a usage of root (/) directory
    - ` sudo apt autoclean & sudo apt autopurge  remove 8 G `

## Home rsync from different OS

### Copy home excluding hidden files

- copy home of other machine to somewhere
- just copy the necessary files
    - do not copy . hidden files
    - in case setting is required, copy it
        - .vimrc

### Save home

- ` rsync home to backup directory `
    - use crontab

### management of hidden directory

- may copy hidden directory
    - .vimrc
    - (etc) license directory
        - .vmware
- not copy
    - .bashrc
        - it is better to make a user which has clean initial files and clean GUI

## package management

### debian package manager

- apt
    - APT – Advanced Package Tool
        - similar to yum in redhat
        - deal with remote repo
        - use dpkg for install/remove
    - forwhat
        - install, upgrade, configure, removing,
        - maintain source repo
        - user several apps
            - use curl to download .deb and all its dependencies
            - then use dpkg to install it
- apt-get
    - apt
- dpkg
    - install/remove in the system
        - use to install local .deb
    - cannot
        - retrieve/download from remote repo, can’t figure out dependencies

### apt(-get), apt-cache & aptitude

- sources
    - ` source list `
        - /etc/apt/sources.list
    - additional source list
        - /etc/apt/sources.list.d/
            - teamviewer.list
            - etc
            - something not listed in sources.list
- installation location
    - /var/cache/apt/archive
- usage
    - update
        - package cache renew
            - list update based on sources.list
        - ` apt-get update `
        - ` aptitude update `
    - upgrade
        - ` apt-get upgrade `
            - Service restarts being deferred
                - systemctl restart NetworkManager.service
        - ` apt-get dist-upgrade `
            - upgrade with dependency
        - ` aptitude safe-upgrade `
        - ` aptitude dist-upgrade `
            - upgrade based on updated list, upgrade the installed package
    - install individual-package
        - ` apt-get install package `
            - python package locates /usr/lib/python2.7/dist-packages
            - ` pip locates python package at /usr/local/lib/python2.7/dist-packages `
        - ` aptitude install package `
    - reinstall
        - ` apt –reinstall install package `
    - remove just package
        - remove package with leaving configuration file
        - ` apt remove package		# tap key is working `
            - ` apt-get remove –auto-remove package `
                - remove it together with other dependent package
        - ` aptitude remove package (do not use!!) `
    - purge package – remove including env variable, configuration
        - remove package including configuration file
        - ` apt purge package `
            - ` apt-get purge –auto-remove package `
                - remove together with its dependency
        - ` aptitude purge package (do not use!!) `
    - ` source code download `
        - ` apt source package `
    - build the received source code with dependency
        - ` apt build-dep package `
    - check packages
        - check the installed package
            - ` apt list --installed		cf. pip list, conda list `
            - ` apt list --installed “fltk*” `
        - search package
            - apt-cache search package
                - faster
            - ` apt search package `
            - ` aptitude search package `
                - search for package containing keyword
                - ` aptitude search nvidia `
        - show the installed package
            - apt-cache show package
                - apt-cache show rsync
            - ` aptitude show package `
    - dependence show
        - ` apt-get –s dist-upgrade `
    - in the case of odds, reinstall
        - ` apt-get –reinstall install package `
    - force to install
        - ` apt-get –f install `
            - in case the previous dpkg –i failed due to dependency
            - if it can find dependency, it download and install it.
            - if it cannot find dependency, it removes the incomplete install package
    - CD\_ROM
        - apt-cdrom add
    - delete
        - ` apt-get remove package `
        - dpkg –P package&#9;# the same
        - remove install files all
            - ` apt-get –purge remove package `
    - ` apt-get dselect-upgrade `
    - scroll installed package
        - dpkg -l

### deb & source

- .deb: a collection of files managed by the Debian packages
    - opposed to source package
    - install a downloaded Debian package manually
        - dpkg –i \*.deb
    - use package manager of aptitude or synaptic to download and install
- ` source package `
    - necessary files to compile or build the software
    - tarball with .tar.gz ending
    - you can install them only if you know the package name
    - search

### [http://www.debian.org/distrib/packages](<http://www.debian.org/distrib/packages>)remove package

- e.g. packagename = ibus
    - ` sudo apt-get remove ibus `
        - remove just ibus package
    - ` sudo apt-get remove –auto-remove ibus `
        - remove ibus and any other dependent package which are no longer needed
    - ` sudo apt-get purge ibus `
        - delete configuration and/or data files
    - ` sudo apt-get purge –auto-remove ibus `
        - including its dependency

### aptitude

- ncurses based frontend to apt
- advance search including pattern
    - ` aptitude search nvidia `
        - show all the package including ‘nvidia’
    - ` aptitude search ‘?narrow’ `
- output of search
    - p&#9;: no trace of the package, removed or never installed
    - c&#9;: deleted but its configuration files remain
    - i&#9;: installed
    - d&#9;: deleted
    - A&#9;: automatically installed
- other usage
    - ` aptitude update `
    - ` aptitude safe-upgrade `
    - ` aptitude install package `
    - ` aptitude remove package `
    - ` aptitude purge package `

### sources.list

- location
    - /etc/apt/sources.list
- basic
    - deb [http://ftp.us.debian.org/debian/](<http://ftp.us.debian.org/debian/>) jessie main contrib non-free
    - deb-src [http://ftp.us.debian.org/debian/](<http://ftp.us.debian.org/debian/>) jessie main
    - deb [http://httpredir.debian.org/debian](<http://httpredir.debian.org/debian>) jessie-updates main
    - deb [http://secuirty.debian.org/](<http://secuirty.debian.org/>) jessie/updates main
    - deb-src [http://secuirty.debian.org/](<http://secuirty.debian.org/>) jessie/updates main
    - deb [http://ftp.debian.org/debian](<http://ftp.debian.org/debian>) jessie-backports main contrib non-free
    - deb [http://ftp.de.debian.org/debian](<http://ftp.de.debian.org/debian>) jessie-backports main
- format
    - deb [http://site.example.org/debian distribution compnent1](<http://site.example.org/debian%20distribution%20compnent1>) ...
    - deb-src http://ftp.kr.debian.org/debian
    - deb mirror\_sites distribution components
- deb indicates that the archive contains binary package
- deb-src indicates source packages
- world wide mirror sites
    - primary mirror site: ftp.\<contry\>.debian.org
    - secondary mirror site
- to edit sources.list using gnome tool: menu-system-administration-software sources
    - gksu –desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

### packages

- available package
    - cat /var/lib/dpkg/available
- status
    - cat /var/lib/dpkg/status
    - dpkg-query -l

### install error

- dependency error
    - message
        - dpkg: error processing package zoom (--install):
        - dependency problems - leaving unconfigured
        - Processing triggers for gnome-menus (3.31.4-3) ...
    - fix up
        - ` sudo apt --fix-broken install `
        - ` sudo apt install -f `

### dpkg

- debian package management system
    - .deb package install, remove, info
- output
    - first character: desired state
        - i: install
        - u: unknown
        - r: remove
        - p: purge
        - h: hold
    - second character: current state
        - n: not-installed
        - i: successfully installed
        - c: cfg-file present
        - u: unpacked
        - f: failed-cfg
        - h: half, partially installed
        - w: wait
        - t: trig-pend
- options
    - install
        - -i
            - dpkg -i deb\_filename
        - -x
            - install at home
    - show list: -l
        - dpkg -l: show all the installed lib, module
        - dpkg -l package\_name
            - wild card is used
            - dpkg -l \*ibus\*
    - check a package: -s
        - dpkg -s package\_name
    - similar
        - --info
            - dpkg (dpkg-deb) --info package\_name
        - --contents
            - dpkg --contents
        - cf. dpkg-query
    - remove: -r
        - dpkg –r package
            - cf. apt-get purge, if this does not work
- dpkg-query
    - ask for packages
    - usage
        - dpkg-query -l
        - using wild cards
            - dpkg-query -l ‘lib\*’

### virtual env

- e.g.
    - package structure
        - A – B, C
            - dev env is different for A—B and A—C
- use anaconda
- deprecated
    - install without virtualenv
        - whenever required a package
            - ` apt-get install python-xxx `
            - ` pip install xxx `
        - induces many problems
        - when there are many different version of package, …
        - resort to virtualenv
            - different env as for different App or different version
    - to use virtualenv
        - use PIP (pypi.python.org)
        - virtualenv myApp
            - makes myApp folder
                - all the env is made in /myApp
        - ` source myApp/bin/activator `
            - to use virtual env
            - change prompt to (myApp) $
        - e.g.
            - python package installation
                - (myApp)$ pip install psutil
                    - installed in myApp/lib/python2.7/site-packages
                - (myApp)$ pip list
                    - shows all the installed package under virtualenv
            - saving
                - (myApp) $ pip freeze \> myApp.req
            - making env
                - (anotherApp) $ pip install –r myApp.req
        - e.g.
            - if not virtual env
                - ` $ pip install psutil `
                    - installed in system folder of /usr/local/lib/python2.7/dist-packages (or site-package)
                    - suppress the installation in system folder if it is not common in all python versions

## Debian basic packages

### Prerequisite

- in the order of priority
    - hangul
        - for googling
    - virtualbox
        - for guest windows
    - dropbox
        - for file delivery
    - teamviewer
        - work at home
    - printer
        - last stage
    - etc
- Include the contribution web
    - Format in /etc/apt/sources.list
        - Archive\_type url\_repository distribution component
    - E.g.
        - deb [http://site.example.com/debian distribution compo1 compo2](<http://site.example.com/debian%20distribution%20compo1%20compo2>) ...
        - deb-src [http://site.example.com/debian distribution comp1 compo2](<http://site.example.com/debian%20distribution%20comp1%20compo2>) ...
    - Archive type
        - deb for binary package
        - deb-src for source package
    - Distribution or release class
        - distribution
            - Jessi for 8.0
            - Wheezy
        - Release class
            - Oldstable, stable, testing, unstable
    - Component
        - Main
        - Contrib
        - Non-free
- download package
    - ` wget url `

### install package

- search and install
    - ` aptitude search `
    - ` apt-get install packgename `
- download package from github
    - ` git clone https://github.com/3dem/relion.git `
        - made dir
    - ` cd dir `
        - ` mkdir build `
        - ` cd build `
        - ` cmake .. `
        - ` make –j <N> `
            - N is number of process, == 1
        - ` sudo make install `
- normal package installation
    - README
        - See INSTALL file for installation instruction
    - INSTALL
        - requirements
        - basic installation
            - configure, compile and install
        - advanced
            - if libraries are not automatically detected
    - Basic Installation
        - Create a ‘build’ directory in the source directory
            - ` mkdir build `
            - ` cd build `
        - Configure the build system
            - ` cmake ../ `
        - Compile
            - ` make –j2 `
        - Install
            - ` sudo make install `
    - Advanced

### Hangul

- ibus is OK in debian
    - ` sudo apt-get install ibus ibus-hangul `
    - makes problem in skype
- Korean fonts
    - ` apt-get install fonts-unfonts-core fonts-unfonts-extra `
    - apt-cache search Korean font

### Environment Modules

- installation
    - install is so simple in Debian 10
        - ` sudo apt-get install environment-modules `
        - reboot
            - before reboot, module is not working
        - not found tclsh  install
            - $sudo apt-get install tclsh
    - some check points
        - ` module install directory `
            - ls /usr/share/modules/modulefiles
        - ` module script in default running directory `
            - /etc/profile.d/modules.sh
- setup using add.modules
    - add.modules
        - yes
            - changes initial files
            - add scripts in the fore-part of .bashrc
    - ` source .bashrc `
    - ` module is working `
        - ` module av `
            - use.own
        - path was doubly included
- load module in .bashrc
    - ` module load use.own `

### Teamviewer

- download teamviewer
- install
    - sudo dpkg -I ./teamviewer-host-version.deb
    - dependency error
        - dpkg: dependency problems prevent configuration of teamviewer:
        - teamviewer depends on libqt5qml5 (\>= 5.5) \| qt56-teamviewer; however
    - ` sudo apt-get -f install `

### mendeley

- version
    - new version: streaming from cloud
        - takes long time loading a big file
    - old version: save in local
        - quickly loaded
- collision problem
    - remove preexisting version
        - new version installed by
            - AppImage
- installation
    - ` tar file  desktop `
        - removing new version
        - ` tar -xvf mendeleydesktop-1.19.8-linux-x86_64.tar.bz2 `
            - ./mendeleydesktop-1.19.8-linux-x86\_64/bin/mendeleydesktop
        - ` sudo mv mendeleydesktop-1.19.8-linux-x86_64 /opt/mendeleydesktop `
        - ` sudo chmod +x /opt/mendeleydesktop/bin/mendeleydesktop `
        - ` sudo vi /usr/share/applications/mendeley.desktop `
            - mendeley.desktop file&#9;&#9;&#9;cf. desktop file directory
                - \[Desktop Entry\]
                - Name=Mendeley Desktop
                - GenericName=Research Software
                - Comment=Mendeley Desktop is a free reference manager and academic social network.
                - Exec=/opt/mendeleydesktop/bin/mendeleydesktop %f
                - Icon=/opt/mendeleydesktop/share/icons/hicolor/128x128/apps/mendeleydesktop.png
                - Terminal=false
                - Type=Application
                - Categories=Education;Literature;Office;Science;
                - MimeType=application/pdf;
        - ` make soft-link file at /usr/loca/bin `
            - ` sudo ln -sf /opt/mendeleydesktop/bin/mendeleydesktop /usr/local/bin/mendeleydesktop `
                - then, $which mendeleydesktop is working
    - AppImage
        - install
            - file explorer: double click
            - cli: make it executable
        - uninstall
            - sudo rm -rf /opt/Mendeley
            - sudo rm -rf /usr/share/applications/mendeley.desktop
            - in case new version which use .local
                - rm -rf "/home/joonho/.local/share/data/Mendeley Ltd."
                - rm -rf "/home/joonho/.config/Mendeley Ltd."
- deb
    - Now it is executable
        - (old) [https://www.mendeley.com/guides/download-mendeley-desktop/ubuntu/instructions](<https://www.mendeley.com/guides/download-mendeley-desktop/ubuntu/instructions>)
        - Install
            - sudo dpkg -i mendeleydesktop\_1.19.8-stable\_amd64.deb
            - ` sudo apt-get install -f `
                - when the previous install has failed due to the dependency
                - python 2 modules will be installed more
            - command
                - mendeleydesktop
        - Uninstall
            - ` apt-get remove mendeleydesktop `
        - update
            - automatic
            - manual
                - ` apt-get update `
                - ` apt-get install mendeleydesktop `
    - character map error
        - install git
            - ` sudo apt install git `
        - sudo make
            - installs characters in

### VM

- whatitis&#9;&#9;&#9;&#9;&#9;
    - using virtual machine as guest in host
        - host: linux, guest: Windows 10
    - two ways
        - vmdk
            - use bootable disk as VM
        - vdi
            - ` make VM as app `
    - Vmware (Workstation and Player) vs VirtualBox
        - virtual box and VM player are freeware
        - Vmware Workstation is commercial for $300 or 30 days trial version

### printer – cups

- Debian 10
    - Automatically detected
        - Power icon/setting/Printers
    - need to disable the automatic network printer detection
        - sudo systemctl stop cups-browsed
        - sudo systemctl disable cups-browsed
        - if you wish to turn on
            - sudo systemctl start cups-browsed
- when printer is not detected
    - cups-browsed might be already installed
        - ` sudo apt install cups-browsed `
    - turn on cups-browsed
        - sudo systemctl start cups-browsed
    - printer-driver-all might be already installed
        - ` sudo apt install printer-driver-all `
    - cups might be installed
        - ` sudo apt install cups `
    - cups page
        - localhost:631
- Epson
    - USB but if not detected in setting (Power/setting/Printers)
    - Download driver
        - [http://support.epson.net/linux/en/epsonscan2.php](<http://support.epson.net/linux/en/epsonscan2.php>)
    - install
        - ` tar xf ep…..tar.gz `
        - ` ./install.sh `
    - printer is detected in setting
    - print is not working
        - jobs are in queue
        - reboot (and it prints)
- (not used)
    - install hp color laserjet M452dw
        - ` apt-get install hplip `
            - remove dependency and reinstall
                - ` apt-get purge lib_name `
                - ` apt-get install lib_name `
    - cups install
        - Common Unix Printing System
            - computer w. cups: server
                - client request print to server
            - composed of
                - unix print spooler, scheduler filter system, backend system
                - fiter: transform data to recognizable format for printer
                - backend: send new data to printer
            - cups-config for commander
        - install
            - [https://wiki.debian.org/SystemPrinting](<https://wiki.debian.org/SystemPrinting>)
                - ` apt-get install task-print-server `
                - ` aptitude install cups `
            - start the software
                - service cups start
        - version check
            - cups-config --version
    - web [http://localhost:631](<http://localhost:631>)
        - one way: you can add printer in
            - for permission to use “add printer”
                - add joonho in /etc/cups/cups-files.conf, the line of SystemGroup
                - sudo systemctl restart cups
                - renew the web page
            - web interface is working
            - change driver using print setting
                - Menu::/Applications/Sundry/Printer Setting
                - Make and Model/ you can change (M651 not M452dw)
                    - try to connect but “the printer is not responding”
    - bellows are unconvinced
        - hplip provided by HP
            - [http://hplipopensource.com/hplip-web/models/color\_laserjet/](<http://hplipopensource.com/hplip-web/models/color_laserjet/>) hp\_color\_laserjet\_m452dw.html
            - download: HP Linux Imaging and Printing – HPLIP
            - dpkg –l hplip
                - check current version
            - get newest version
                - download hplip-3.16.11.tar
                - untar into hplip-3.16.11.run
                - sh hplip-3.16.11.run
                    - request su passwd
                    - error due to not-supporting Debian 8.7 yet
            - after install hplip
                - go on
        - another way: find driver
            - google: install hp printer in Debian
                - hp site does not support Debian
                - Debian Printing (Common UNIX Printing System)
            - Install printer
                - package system-config-printer supplied by CUB
                    - wheez (oldstable) (python)
                        - python-minimal\_2.7.3-4+deb7u1\_all.deb
                        - python\_2.7.3-4+deb7u1\_all.deb

### pdf reader

- evince might be default

### make icon and put into favorate

- gather icons
    - ~/.icons
- Make a new icon for a command
    - Application/Accessory/Main Menu
        - E.g. go to Accessories
    - New Item
        - Command: e.g. rdesktop –g 1910x1100 143.248.247.238
        - Icon: click and change icon
    - New icon appears on the right column
    - Find icon in Application/Activities Overview/left column-bottom click
        - Find the icon move it to favorite, the left column
- Put an icon into favorate
    - execute the app, then, icon appears on the bar (favorate + running app)
    - Activities
        - favorate+running app appears on the bottom
        - click the icon on the bottom bar and move to favorate region
            - the icon splits and make the new icon locates on the favorate

### Mozilla flash plugin

- find
    - Debian Mozilla flash plugin
- Install w. su
    - ` apt-get install flashplugin-nonfree `
- uninstall
    - update-flashplugin-nonfree –uninstall
    - ` apt-get remove flashplugin-nonfree `

### image viewers and file format

- file format
    - adobe format
        - ps: PostScript
        - AI:
        - eps: Encapsulated PostScript
        - viewer: gv, evince
- vokoscreen
    - install
        - error in
            - ` apt-get install vokoscreen `
                - comes from ffmpeg is not installed.
        - After fix the error of dependency
            - Apt-get install vokoscreen (not tested)
            - Download .deb of vokoscreen
            - Dpkg –I voko\*\*\*.deb
    - Install ffmpeg
        - Error
            - Already ffmpeg is shown but it is not recognized when install vokoscreen
            - Not correctly installed
        - Solve
            - ` apt-get –f ffmpeg `
                - Installed without error message
    - Usage

### Movies

- Movie player
    - Video (default installed)
- Movie capture
    - simplescreenrecorder
- Smplayer in softwares
    - ` apt-get install smplayer `
    - it just movie player

### zoom

- download
    - [https://zoom.us/download?os=linux](<https://zoom.us/download?os=linux>)
- install
    - sudo dpkg -i …..deb

### anaconda & jupyter

### python

- structure
    - root or user&#9;&#9;cf. anaconda
- install
    - at root
        - ` sudo apt update `
        - ` sudo apt upgrade `
        - apt-cache search numpy
            - shows possible python package
        - ` sudo apt install python3-numpy		# python3-xxx (xxx package) `
        - ` pip3 install numpy  error `
    - at home
        - using apt-get
            - v. = 2.7
            - default: not-tuned car
            - install
                - $apt-get install python-matplotlib python-numpy python-scipy
            - location
                - /usr/lib/python2.7/dist-package
        - using pip
- ASE
    - as user
        - install
            - ` pip install –-upgrade –-user ase `
                - installed in ~/.local/bin
            - ` pip install --upgrade –user numpy scipy matplotlib `
            - PYTHONPATH to ~/.local/lib/python2.7/site-packages
            - PATH to ~/.local/bin
        - uninstall
            - ` pip uninstall ase `

### icons

- how to use icon for an installed app
    - general
        - create .desktop file with path to icon images placed at icon directory
    - order
        - create the icon image
        - place the icon file
            - /usr/share/icons/hicolor
            - create subfolders based on the icon size you need
        - create .desktop file
- icon image
    - download
        - [https://www.mendeley.com/download-reference-manager/linux](<https://www.mendeley.com/download-reference-manager/linux>)
        - Mendeley reference manager for desktop
            - download for generic linux: 64 bit
    - put it at icon directory
- e.g. Mendeley
    - [https://askubuntu.com/questions/1270479/install-mendeley-desktop](<https://askubuntu.com/questions/1270479/install-mendeley-desktop>)
        - download AppImage: e.g. mendeley-reference-manager-2…..AppImage
            - ` make it excutable `
        - ` make app folder `
            - ./mendeley-reference-manager-2…..AppImage --appimage-extract
                - makes folder: squashfs-root
            - ` mv to /opt/mendeley		# contents are moved `
        - create AppImage Launcher (.desktop file at /usr/share/applications)
            - \[Desktop Entry\]
            - Name=Mendeley
            - Type=Application
            - Categories=Office;
            - MimeType=image/svg+xml;
            - Exec=/opt/mendeley/AppRun %F
            - Icon=/opt/mendeley/mendeley-reference-manager.png
            - Terminal=false
            - StartupNotify=true
            - X-Desktop-File-Install-Version=0.26
        - install desktop file
            - sudo desktop-file-install /usr/share/applications/Mendeley.desktop
    - Ubuntu
        - ` sudo apt install flatpack `
        - sudo flatpack remote-add --if-not-exists [https://flathub.org/repo/flathub.flatpakrepo](<https://flathub.org/repo/flathub.flatpakrepo>)
        - sudo flatpack install flathub com.elsevier.MendeleyDesktop

### gnuplot

- ` sudo apt install gnuplot-qt `

## Debian package etc

### Avodadro

- install
    - ` apt-get install Avogadro `
    - download from website
        - [https://avogadro.cc/](<https://avogadro.cc/>)
        - avogadro-1.2.0
        - normal installation procedure
- saving directory for copy
    - /usr/share/avogadro/
        - how to find
            - locate 3-trigonal-planar
                - then several places
        - check matching between Build/Insert/Fragments and directory
    - copy
        - save /usr/share/Avogadro/water.cml
        - Build/Insert/Fragments

### vmd

- download vmd-1.9.1
- unpack using unzip
- README
    - ` vi configure `
        - bin
        - lib
    - ` ./configure `
    - ` cd src `
    - su –
        - ` make install `
            - write as root, /usr/local/bin
        - path check

### Jmol

- install
    - gunzip Jmol-14.4.1\_2015.12.15-binary.tar.gz
    - ` tar xvf Jmol-14.4.1_2015.12.15-binary.tar `
    - ` cd jmol-14.4.1_2015.12.15 `
    - ./jmol.sh
- link in /home/$USER/bin
    - ` ln –s $home_dir/jmol $USER/bin/jmol `
    - ` ln –s $home_dir/Jmol.jar	$USER/bin/Jmol.jar `
- [how to use](<file:///C:\Users\root\AppData\Roaming\Microsoft\Word\visual_program.docx>)

### molden

- web
    - https://mklammler.wordpress.com/2013/01/30/update-installing-molden-on-64bit-debian-based-gnulinux-systems/
- install dependencies
    - ` sudo apt-get install build-essential gfortran libX11-6 libX11-dev libgl1-mesa-dev libgl1-mesa-glx libglu1-mesa-dev libxmu-dev xutils-dev mesa-common-dev `
- install molden
    - ` wget ftp://ftp.cmbi.ru.nl/pub/molgraph/molden/molden5.0.tar.gz `
    - ` cd dir `
    - makefile
        - ` LIBS = -L/usr/X11R6/lib64 -lX11 –lm `
            - there is no directory of /usr/X11R6, but it runs with many warnings
    - make
        - show many warnings
        - makes molden, gmolden
    - install commander,
        - sudo install -t /usr/local/bin -m 755 molden gmolden
- [how to use](<file:///C:\Users\root\AppData\Roaming\Microsoft\Word\visual_program.docx>)

### IQmol

- download .run file
    - [http://iqmol.org/downloads.html](<http://iqmol.org/downloads.html>)
- ` chmod 755 IQmolxxx.run `
- ./IQmolxxx.run
    - ` make install directory `
    - exe file
        - $IQHOME/cde-root/opt/IQmol/iqmol.sh, IQmol
- [how to use](<file:///C:\Users\root\AppData\Roaming\Microsoft\Word\visual_program.docx>)

### grace (xmgrace)

- ` aptitude install grace `
    - xmgrace is automatically installed
- xmgrace – gui

### bazaar

- a distributed version control system
- install
    - ` aptitude search bzr `
    - ` apt-get install bzr `
- user id
    - register id
        - bzr whoami “Joonho Park \<email\>”
    - id check
        - bzr whoami
- starting a new project
- Adding files
- Making changes to your files
- Viewing the revision log
- Publishing your branch on Lanchpad
- Creating your own copy of another branch
    - to work with someone else’s code, copy of their branch
    - e.g. Bazaar’s GTK interface
        - bzr init-repo ~/bzr-gtk
        - bzr branch lp:~bzr/bzr-gtk/trunk ~/bzr-gtk/john
    - e.g. thinkcspy
        - bzr init-repo bzr
        - ` cd bzr `
        - bzr branch lp:thinkcspy
- Updating your branch from the main branch

### VASP ([gnu](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\vasp.docx>), [intel](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\vasp_qe.docx>))

- web for gnu:
    - [http://www.ivofilot.nl/posts/view/28/How+to+build+VASP+5.3.5+using+the+ GNU +compiler+on+Linux+Ubuntu+14.04+LTS#step1](<http://www.ivofilot.nl/posts/view/28/How+to+build+VASP+5.3.5+using+the+%20GNU%20+compiler+on+Linux+Ubuntu+14.04+LTS>)
    - install vasp 5.3.5 using gnu complier on linux Ubuntu 14.04 lts
        - for Ubuntu 14, Debian 8
    - for intel go to [vasp.doc](<file:///C:\WinData\Res_EEWS\Docs\vasp.docx>)
- 4 steps cf. [vasp.doc](<file:///C:\Users\root\AppData\Roaming\Microsoft\Word\vasp.docx>)
    - installing the necessary packages
    - install OpenMPI
        - building OpenBLAS
        - building ScaLAPACK
        - building VASP
            - [modify makefile](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\vasp_qe.docx>)
- run
    - console
        - ` mpirun np -4 /home/joonho/bins/vasp & `
- can run without license but can’t publish without license

### quantum espresso

- install
    - ` aptitude install quantum-espresso `
    - download & install

### cp2k

- ` aptitude search cp2k `
- ` aptitude install cp2k `

### p4vasp

- install from repository
    - cf p4vasp in Common
- install through repo
    - ` sudo apt-get update `
    - ` sudo apt-get install p4vasp `
        - in case failure, -f
            - ` apt-get -f install (without package name) `
- binary
    - $HOME/p4vasp/bin/p4v

### vesta

- JP-Minerals site
    - Mineralogy and Crystallography
    - http://jp-minerals.org
- download x86\_64
    - http://jp-minerals.org/vesta/en/download.html
        - cf. i686 is for 32 bit
- “bzip2 –d” followed by tar xvf
- it is run w.o. installation

### openbabel

- download jessi
    - [http://openbabel.org/wiki/Category:Installation](<http://openbabel.org/wiki/Category:Installation>)
- install
    - dpkg –I file
- run
    - ` which obabel `

### Matlab

- requirement
    - login [https://kr.mathworks.com](<https://kr.mathworks.com>)
        - [로그인 정보 삭제]
        - [로그인 정보 삭제]
    - click association
    - input activation key
        - to get license file and key
    - download linux version
- installation
    - online installation
        - ` ./install `
        - install window
            - install with login id in mathworks: internet connection is required
                - download and install takes time
        - activation
            - input mathworks id and passwd
    - download license file and personal activation key
        - ` ./install with license file `
            - install done
        - activation before using
            - activation key is required
    - execution file = matlab
        - /usr/local/bin/matlab

### relion

- surface image caring program
- install
    - ` git clone https://github.com/3dem/relion.git `
        - made dir of relion
    - ` cd relion `
    - ` git pull `
        - update in command line
    - ` mkdir build `
    - ` cd build `
    - ` cmake .. `
    - ` make –j <N> `
        - N is number of process, == 1
    - ` sudo make install `
- usage
    - go to upper directory of mrc files
    - $relion

### skype

- install
    - su –
    - ` apt-get update; apt-get upgrade `
    - downloading
        - ` wget -c http://download.skype.com/linux/skype-debian_4.3.0.37-1_i386.deb `
    - dpkg –i skype-debian\_4.3.0.37-1\_i386.deb
        - install fails
            - errors were encountered
        - need to install any required 32-bit packages
    - dpkg –add-architecture i386
    - ` apt-get update `
    - install again
        - dpkg –i skype-debian\_4.3.0.37-1\_i386.deb
            - error again
    - let the installer fix the dependencies by automatically installing any missing packages
        - ` apt-get –f install `

### vi, hwp viewer, jaxodraw

- vi
- jaxodraw
    - for drawing like chemdraw
    - only linux versions are available

### backup/ crontab rsync ssh

- back up home directory using crontab
    - ` which crontab `
    - crontab –e
        - 0 12 \* \* \* rsync –avz –delete /home/joonho/  &#9;/Data/Backhome/joonho
    - for remote server, make key
        - ssh-copy-id –I ~/.ssh/id\_rsa.pub chi.kaist.ac.kr
            - answer passwd
        - then you can login without passwd
        - ` rsync –avz –e ssh /qcfs/joonho/bin	joonho@chi.kaist.ac.kr:/Data/BUkaist `
- back up windows 7 data

### etc. dropbox

- dropbox
    - web
        - https://www.dropbox.com/install-linux
    - install in usermode
        - ` wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf - `
            - , which makes
                - ~/Dropbox
                - ~/.dropbox-dist
    - run daemon whenever you login
        - ~/.dropbox-dist/dropboxd
    - running the daemon from your own account
        - run /bin/lib/dropbox.py
        - now (?)
            - /etc/init.d/dropbox
                - /home/joonho/bin/lib/dropbox.py

### remote desktop

- kinds
    - xrdp, rdesktop, remmina, realvnc
- common
    - remote login
        - properties
            - to use KVM vs rlogin
        - remmina is for debian
- xrdp
    - X remote desktop protocal
    - install
        - update and upgrade
        - ` apt install xrdp `
    - check
        - systemctl status xrdp
    - configure
- remmina
    - property
        - best one
        - only for debian
    - install
        - ` apt-get remmina `
            - icon is automatically generated in Internet
    - direct connect
        - RDP
        - Put in IP and Connect
        - Open preferences dialog
            - RDP
                - Quality option: Best (slowest)
    - Save connection
        - New
        - Profile
            - Name: office window
            - Protocol: Remote Desktop Protocol
        - Basic
            - Server: ip
            - Username: id
            - Password: skip
            - Domain: kaist.ac.kr
            - Resolution
                - Fit to monitor
                - larger value shows larger Host window
            - Color: true color 24 or 32
        - Advanced
            - Quality: Best(slowest)
                - Shows Host wallpaper and mouse cursor properly
    - For host, adjust [windows 10](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\Window_Machine.docx>) performance
    - there are issues for cerius through mobaXterm
- Realvnc
    - install
        - guest
            - Download realvnc for debian of x64
            - ` tar x `
            - dpkg –I VNC-Viewer…deb
        - install and run realvnc server in host
    - not tested yet
- rdesktop
    - install
        - ` apt-get install rdesktop `
    - run
        - rdesktop –g size ip
            - e.g.: rdesktop –g 1910x1100 143.248.247.238
            - defect: wallpaper doesnot com
        - rdesktop –x I –g 1910x1100 143.248.247.238
            - wallpaper appears
            - defect: mouse cursor is not shown

## Debian Env setup

### Debian setting

- icon
    - power/find gear icon
- wi-fi
- network
- Bluetooth
- appearance
- notification
- search
- multitasking
- application
- privacy
- online accounts
- sharing
- soud
- power
- display
- mouth & touchpad
- keyboard
- printers
- removable media
- color
- region & language
- accessibility
    - Seeing
        - large text
        - enable animation
        - cursor size: size of mouse cursor, combined with zoom

### time & region

- do not use date to fix time
- System/Date & Time&#9;&#9;# power (pull down menue) / repair icon
    - Automatic Date & Time&#9;→ on
    - Time Zone → Seoul
- if it is not configured correctly
    - gmail time is affected
    - VM window regional time is different

### Korean

- System/Region & Language
    - input sources
        - others → select Korean (hangle)
- Korean fonts
    - Apt-get install fonts-unfonts-core fonts-unfonts-extra
    - Apt-cache search korean font

### gnome

- (win-icon):
    - show program
    - add program icon to favorite

### gnome shell extension

- install favorite
    - ` make favorite appear upper bar `
- the selected application appears the rightest side
    - properties

### where is preference

- open app
    - app icon is activated on the rightest of favorite row
- click pull down menu on activated icon on favorite bar
    - control preference

### nautilus (Files)

- default Gnome file manager, file navigator
- menu
    - View
        - toggle Full screen: F11
- Connect and open remote server
    - Connect to Server
        - Enter address
- bookmark
    - whatitis
        - shortcut which appears on the left side
    - in case that there is no “bookmark this location”
        - go into the directory and ^d
        - edit ~/.config/gtk-3.0/bookmarks for “bookmark”
- sort directory
    - whatitis
        - error of woven files and directories
            - not good in displaying files and directories in pane
            - want to select “first directory then files”
    - nautilus (file explorer)
        - add menu
        - location of preference
            - activate nautilus
            - Menu in top-bar/Preferences//Sort √ Sort folders before files
                - this is not default, check box
        - old version
            - /org/gnome/nautilus/preferences
                - this was moved to Menu in v. 3.28
    - file chooser
        - when try to choose a file in any application
        - /org/gtk/settings/file-chooser
            - sort-directories-first → true

### Main menu

- Location
    - Applications/system menu/Main menu

### Icon

- supported icons
    - ` make ~/.icon `
        - all the supported icons be located here
- icon change
    - Find application/Properties
        - Click icon window and insert icon file

### tweak

- menu:/system tools/tweak tool
    - add: Extensions/below -\> Install shell Extension -\> Get more extentions

### xterm

- preference/color
    - toggle on system theme: black or white background
    - if change “Text color” gray, Gray on black appears on Built-in schemes
    - XTerm: Palette “Built-in schemes”
        - makes dark blue into bright blue
- preference for open tab or Terminal/Edit/preference
    - pull-down menu of activated icon
- profile for color
    - Terminal/Edit/profile

### initial files & alias, PS

- .bashrc
    - general
        - if you have complete path, remove path
            - unset PATH
                - without unset, whenever source .bashrc $PATH increases
            - ` export PATH=”/home/joonho/bin:… “ `
        - set up alias, PS1, env variable for utility
    - unset LD\_LIBRARY\_PATH
    - ulimit –s unlimited
        - #ulimit –l unlimited
    - alias
- alias
    - alias ls=’ls –color=auto’
    - alias vi=’vim’
- env variables
    - ` export PS1=”’id –nu’@\h: \w$ “ `
    - color on PS1 make bug the line of xterm
        - ` PS1='\e[0;33m\u@\h:\e[0;31m\w\e[m\$ `

### change default program

- main program: setting
- application program: file -\> mouse right click/properties/Open with/default setup

## Debian Errors

### Boot error after OS update

- update and reboot
    - boot is not ended
        - failed job
            - avahi-daemon
        - A start job is running for Update the operating system whilst offline (time…
    - ^@del  reboot
        - it goes normal
            - avahi-daemon is running  sudo systemctl status avahi-daemon

### damage from installation of python-pqqt4:i386

- ` aptitude install python-pyqt4:i386 `
    - remove many system files
    - X is gone
    - driver, firmware are removed
- ` aptitude vs. apt-get `
    - ` aptitude install works more violently including system files `
        - do not use

### Cure

- repository (/etc/apt)
    - deactivate repository after the installed packages are working well
        - to escape dependency
- /etc/apt/source.list
    - leave basic only and remove the others
        - sorce.list.d is disabled original
- ` apt-get install –reinstall packagename `
    - install: just install not-existing files
    - install –reinstall: reinstall all the files

### kernel change

- save data
- install required package
    - prepare
        - build-essential
        - linux-source&#9;&#9;! kernel source
        - kernel-package&#9;&#9;! provide make-kpkg
        - libcurses5-dev
    - install
        - ` apt-get install build-essential linux-source kernel-package libncurses5-dev `

### network broken

- symptoms
    - case 1
        - in menu bar, network icon disappeared
        - setting/network
            - the system network services are not compatible with this version
    - case 2
        - OS was installed without network
        - manual network setting after OS installation
- related command
    - …
- key checks
    - as root
        - ifconfig –a
            - to check IP address
        - netstat –rn
            - whether the routes are right?
        - iptables –L
            - firewall rule which does not let you out
        - if they are all OK, maybe your IP address doesn’t belong to the router network
- manual IP setting&#9;&#9;cf. network
    - How to setup a static IP address in Debian Linux
        - [https://linuxconfig.org/how-to-setup-a-static-ip-address-on-debian-linux](<https://linuxconfig.org/how-to-setup-a-static-ip-address-on-debian-linux>)
    - using
        - GUI of network-manager
        - for manual work, disable any other interfering daemon such as
            - systemctl stop NetworkManager.service
            - systemctl disable NetworkManager.service
    - /etc/network&#9;&#9;! main position
    - interfaces&#9;&#9;! modify
        - ` source /etc/network/interfaces.d/*	! additional position `
        - # primary network interface
            - allow-hotplug eth0
            - iface eth0 inet (dhcp -\> static)
                - (to) iface eth0 inet static
    - two branches here
        - direct inclusion in interfaces
            - address&#9;&#9;&#9;! with tab
            - netmask
            - gateway
        - recommended way to add network interfaces in interfaces.d/
            - interfaces.d/eth0
            - iface eth0 inet static
                - address
                - netmask
                - gateway
            - then remove the last line in “interfaces”
                - iface eth0 inet static
    - set static DNS server
        - /etc/resolv.conf
            - nameserver 143.248.1.177
    - apply changes
        - #service networking restart
- remedies
    - instant connection
        - change IP address&#9;
            - ifconfig eth0 ip\_address netmask mask\_address
            - if you cannot see eth0 in ifconfig
                - use manual setting
        - change gateway (router)
            - route add default gw 143.248.247.1
    - manual setting
        - /etc/network/interfaces
    - graphic setting
        - Applications/System tools/Network tools
        - if you cannot see eth0 – check manual setting

### cdrom is not recognized

- problem
    - the system was installed by DVD
    - music CD is running
    - data is not read
        - cdrom0 does appear in file pane but can not access
        - error message
            - Unable to access “cdrom0”
            - mount: /dev/sr0 is already mounted or /media/cdrom0 busy

### system sluggish

- cpu usage when the system slows down
    - When system slows down, check journalctl.log
        - Log suggests that there’s something wrong with gdm; you can try to install a different session manager (for example lightdm) and use it instead of gdm.
    - [https://forums.debian.net/viewtopic.php?f=5&t=149954&p=741823#p741823](<https://forums.debian.net/viewtopic.php?f=5&t=149954&p=741823>)
- Hard disk usage
    - less than 70%
- memory leaks
    - free -h
- gnome
- swap
    - swapon -s
    - free -m
    - if swap memory would be heavily used, it would slow down the OS both in SSD ad HDD
- cpu fan
    - sensors

### auto-rebooting & lost desktop session

- screen Lock or suspension in desktop
    - Lock: shows login
    - suspension save power but may cause more problem
- Lost session and clean desktop session
    - when login, session is lost and desktop is clean
        - auto-reboot or session restart
- checking reboot
    - uptime
        - 13:54:25 up 104 days, 20:24,  1 user,  load average: 2.37, 2.20, 1.78
            - rebooted 104 days before
    - who -b
        - system boot  2025-07-02 17:30
            - rebooted Jul 02
    - sudo journalctl -e \| tail -n 50
        - stdout
            - Oct 15 05:12:20  system will suspend now
            - ...
            - Oct 15 10:37:27  PM: suspend exit
            - Oct 15 10:40:48  AMDGPU(0): DPMS capabilities: StandBy Suspend Off
        - at 05:12 computer enter suspend mode
    - conclusion
        - computer entered suspend
        - upon wake, GDM or GNOME session restart incorrectly
            - login prompt to appear again
            - First login attempt fails (old session partially locked)
            - On second attempt, you get a fresh empty session
        - This is not rebooting but resume-from-suspend glitch
- Checking suspension error
    - sudo dmesg \| grep -i segfault
        - zoom caused segmentation fault error
        - remove zoom or prevent suspension
    - fix zoom in suspension error
        - turn off in entering sleep
        - update and upgrade # sometimes help
    - prevent suspension
        - run out of conda
            - # Disable suspend when idle on AC power
            - gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 'nothing'
            - # Disable suspend when idle on battery (if a laptop)
            - gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery-type 'nothing'
        - check
            - gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type
            - gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-battery-type
            - this should return nothing
        - need to run only once if not set as ‘nothing’ in
        - .bashrc
            - # Disable automatic suspend only when in GNOME graphical session
            - if \[ -n "$DISPLAY" \] && \[ -n "$DBUS\_SESSION\_BUS\_ADDRESS" \] && command -v gsettings \>/dev/null; then
            - current\_ac=$(gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 2\>/dev/null)
            - if \[ "$current\_ac" != "'nothing'" \]; then
            - gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 'nothing'
            - fi
            - current\_bat=$(gsettings get org.gnome.settings-daemon.plugins.power sleep-inactive-battery-type 2\>/dev/null)
            - if \[ "$current\_bat" != "'nothing'" \]; then
            - gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-battery-type 'nothing'
            - fi
            - fi

### Low disk space on Filesystem root

- hard disk usage&#9;&#9;cf. du
    - error: Low disk space on Filesystem root
        - Filesystem root has only 100MB disk space remaining
    - check
        - du -hx --max-depth=1
        - /var/cache/apt/archives has 27G
    - solve
        - rather than remove files
        - ` sudo apt clean ( & sudo apt autoremove --purge) `
            - Avail: 1 G  9.7 G&#9; 11 G
            - Used: 97 %  63 %&#9; 61 %

<br>

## Linux common structure

## Skills

### ssh

- login without passwd asking&#9;&#9;&#9;&#9;&#9;cf Common ssh
- -X or -Y doesnot working
    - error
        - connect localhost port 6000: Connection refused
        - Error: Can’t open display: localhost:28.0
    - set DISPLAY
        - check DISPLAY
            - localhost:11.0 in iron
        - .bashrc
            - ` export DISPLAY=localhost:11.0 `

### hard disk

- insert new hdd
    - system recognize hdd
    - partition hdd
    - store uuid in fstab

### editor

- ` make vim use copy and paste `

### Xerr & Making new home

- When
    - X was broken
- procedure
    - ` make a new id `
        - adduser david
        - check no X problem when login David
            - then
    - ` make HOME at /home `
        - ` sudo mv joonho joonho_Xerr `
        - ` sudo mkdir joonho `
        - ` chown -r `
        - chgrp -r
        - copy . file from joonho\_ini
            - ` cp -r /home/joonho_ini/.* . `
        - login with joonho
            - no Xerr
    - several steps in moving files to new HOME
        - using env in .bashrc
            - ` cp /home/joonho_Xerr/.bashrc . `
        - using VB
            - ` rsync -avz –exclude=”.*” /home/joonho_Xerr/vmware /home/joonho `
            - ` rsync -avz –exclude=”.*” /home/joonho_Xerr/’VirtuslBox VMs’ /home/joonho `
        - move data file at home
            - ` rsync -avz –exclude=”.*” /home/joonho_Xerr/ /home/joonho `
    - do not move . files
- find error source
    - check .file
        - ls -al \| grep "\\." \| wc -l
    - allowed files
        - desktop and system
            - .bashrc
                - color in dir
                - some setting
                - remove $DISPLAY
            - .bash\_aliases
                - to run ~/bin/alias.sh
            - .ssh
                - ssh-keys and config
            - gnome
                - .gconf
                    - normally animation off
                - .config
                    - setting in gnome tweaks
                - if version is changed, error can occur
        - app hidden files
            - .vmware
            - .virtualbxo
            - .team
            - .skypeforlinux

### man

- Usage format
    - ip \[options\] objects \{command\|help\}&#9;cf. what is \{ \}
        - objects = \{link \| address …\}
        - options = \{ -V \| -s\[tatistics\] \| …
    - objects should follow command “ip”

## dual booting system

### Linux option

- for server
    - debian or centos
- for desktop
    - ubuntu LTS
    - Debian
    - centos

### w. two SSD

- hardware connection of M.2
    - two SATA M.2 SSD
        - new SSD for linux to first primary sata: sda
        - Windows SSD to first secondary sata: sdb
        - the other hdd to second primary and secondary: sdc, sdd with ext4 format
    - NVMe and SATA M.2 SSD
        - NVMe for linux
        - SSD for Windows
- OS install
    - Install order
        - First install Windows
        - 2<sup>nd</sup> install Linux
    - check: does boot recognize windows and try dual booting automatically?
    - set uuid for sdc and sdd with ext4
- VM
    - ` make vmdk file `
        - using VB
            - VB can make vmdk file&#9;cf.
        - using VMware
            - use VMware to make VMware object
                - ` make VMware recognize the Windows SSD `
            - run VB to run VMware object
    - VB object
        - Windows cannot be run independently
        - Data need to be backed up to common directory

### from Windows.doc (below)

- double try for installation
    - to fix up network error
        - during installation network connection is disconnected, then ssh is very slow
    - first boot Ubuntu using usb
        - set up network ip/DNS
            - upper bar connection icon/Edit connection
        - set up repository such as Japan
            - software center::upper bar/Edit/software source/Download from
    - second install again using usb
        - Install This icon is for installation directly without reboot.
        - Select hangle
        - Install option:
            - 3<sup>rd</sup> one: edit partition
            - Do not choose automatic partition (it might take partition in window7)
        - Choose keyboard hangle
        - Boot loader should locate in window driver
            - Boot driver in CMOS cannot conceive Ubuntu driver
- after install: monitor, Korean, ssh
    - terminal: 12.04
        - Dash home(left 1<sup>st</sup> icon)/”input terminal in input box” and click
    - Power icon/system management/Language-한국어
        - There appear keyboard on top right tray
    - .ssh
        - Ubuntu desktop has ssh for connection to server but no function for server
        - Install
            - Sudo apt-get install openssh-server
            - Openssh-client for Ubuntu server
    - Reboot option for OS
- after update
    - New desktop such as 12.04
        - Install from program add ( + magnifying icon )
            - Search: terminal
            - Install
- utility
    - main Menu(11.04): Application, Places, System
    - Network
        - Network was disconnected during installation
            - Window7 has no problem in network but Ubuntu cannot recognize it
        - Setup manually
            - System/Preferences/Network Connections
            - Find Mac address at terminal
                - ifconfig –a
                    - Eth0: explain for Ethernet card
    - Automatic update
        - But 11.04 does not active support anymore
        - Is there OS update without complete installation
    - User
        - adduser id
        - deluser id&#9;&#9;&#9;&#9;: delete just account
            - deluser –remove-home id&#9;&#9;: delete home directory
            - deluser –remove-all-files id&#9;: delete all the files made by id&#9;
    - root or sudo
        - sudo
            - require passwd whenever to use it.
        - Ubuntu is not allowed to use root account
            - Sudo passwd root
                - Put in the previous user passwd
                - Enter new passwd
            - Log out and log in as other/root and new passwd
            - Optional
                - System/Administration/Login display
                    - Click “view display during selecting user in login
- Utility 2
    - Hangle
        - Whether installed or not
            - System/administration/Language Support
                - Tag Language/Korean, Install/Remove Languages
                    - Confirm or install
                    - Ibus or nabi (nabi has priority if it is installed)
        - Keyboard icon in the upper bar
            - Tag General/keyboard shortcuts/^space is default
            - Tag Input Method/Korean -\> add
- etc
    - screen save and log out
        - 절전모드 goes to power out
        - Screen save in software and monitor work together
            - Uncheck screen saver in monitor
            - Disable screen saver in ubuntu
        - Google “disable Ubuntu desktop screen auto locking”
            - 12.04 at terminal
                - gsettings set org.gnome.desktoop.screensaver idle-activation-enable false
            - uninstall
                - ` sudo apt-get purge gnome-screensaver `
            - install
                - ` sudo apt-get install xscreensaver xscreensaver-gl-extra xscfeensaver-data-extra `
                - next run: sudo gedit /etc/xdg/autostart/screensaver.desktop

## Reinstall dual booting

### How to reinstall

- How to change of windows SSD
    - Disconnect Linux, (re)install windows
    - Just reinstall windows  overwrite boot section by Windows
        - Linux becomes not bootable
            - how to fix
                - grub-rescue using live-linux
                - reinstall linux
                    - overwrite home directory
                    - possible overwrite only boot directory?

### Change of SDD for windows

- Prerequisite
    - Check hard disk list
        - NVMe for linux
            - Size, partition, linux version (Debian 10 or 11)
        - Sda for windows
            - Size, partition
        - Sdb for data
            - Size, partition (one or two for data division)
    - Two booting usb for linux (live version) and Windows
        - Rufus for Windows
        - Dalanetcher for live-linux

### Install Windows w. linux connected

- Boot through usb
    - F10 (Samsung) shows bootable device
        - The same as CMOS/boot/boot priority
    - CMOS
        - Advance/bootable usb  appear
        - Boot
            - Fast  inactive
            - Secure  inactive
    - UEFI: usb should appear in boot priority
        - If not
            - Check bootable usb (FAT32 for windows)
- Install Windows
    - Select the target, not partitioned disk with the same size of the new hard disk
    - Install

### Make Linux runs

- “Boot repair”: Restoring Grub after installing Windows
    - [https://www.cybrary.it/blog/restoring-grub-installing-windows](<https://www.cybrary.it/blog/restoring-grub-installing-windows>)
    - GRUB: Grand Unified Bootloader
        - Default bootloader used in Linux
    - Why this happen?
        - Windows doesn’t recognize neighboring system
- Three ways to solve
    - Live CD or live usb
        - Boot it in test (try not to install)
        - Open a terminal
            - ` $ sudo fdisk -l `
                - Installed linux partition
            - ` $ sudo mount /dev/sda3 /mnt `
            - ` $ sudo mount –bind /dev /mnt/dev `
            - ` $ sudo chroot /mnt `
            - ` $ grub-install /dev/sda `
            - ` $ sudo update-grub			cf grub update `
        - GRUB has been installed successfully
    - easyBCD
    - boot-repair
- Linux bootable device cannot boot (Windows is OK)
    - Boot by live-linux bootable usb
        - Set boot options  inactive
            - If not, error message
    - @F1 or F2 or …  new terminal ?
        - Terminal: using command sudo, mount, etc, you can reach to linux server
            - Same as “Boot-repair”?

### Make GRUB works

- source
    - [https://askubuntu.com/questions/725290/windows-doesnt-start-anymore-from-the-grub-boot-menu/725309#725309](<https://askubuntu.com/questions/725290/windows-doesnt-start-anymore-from-the-grub-boot-menu/725309>)
- status
    - in boot
        - both work
    - in grub
        - Windows fails with error
            - no such device and cannot find /EFI/Microsoft/boot/microsoftcf.efi
- remedy
    - sudo update-grub2

### Make a new VM

- previous vmdk fails
- ` make vmdk file via VB `

## Partition

### basic

- try to make /home as principle partition
    - LVM: logical volume cannot be conserved when system is reinstalled

### swap & 3 partitions in sda

- /boot, swap, /home, / about 50 G
    - is it possible to make all principle partition?
        - if using gdisk
- present partition
    - /boot &#9;500M ~ 1G
        - standard format, ext4
        - after all set-up: 24% 212 M used
    - swap&#9;10G
        - standard format, swap
            - up to harddisk 500 G
        - doesn’t appear at df
    - /home&#9;2077
        - take all the possible space except / w. about 30 G
        - now 51% 95G used at present work space
    - /&#9;remainder about 50G, 27G exactly
        - it will be 50G later
            - intel has about 15G for root installation
        - 27%, 7G was used
- go to centos, debian

### chi disks

- only sda is partitioned at installation
    - for sd-b,c,d check them w. df after mount
- sda
    - 250G
- sdb, sdb1
    - 2T, Data directory 18% used
    - rather than sdd, make a partition in sdb for /scratch of Q-Chem
- sdc
    - shared directory
        - change sdc to sdb by changing data cable
        - UUID follows hard disk format. So, data cable change does not make any change in system.
    - sdc1 for Windows 10
        - is not shown in df before temporary mount
    - sdc2 ?
    - sdc3 1T /shared directory, 31% used
- sdd, sdd1
    - sdd hard disk makes problem in grub.
        - going to remove sdd

### uuid & fstab & mount & backup

- how to conceive hard disk by linux system
    - installing linux kernel
        - /, /boot, /home, etc are conceived by linux system and stored in /etc/fstab
    - need to make linux conceive new hard disk
    - linux makes harddisk uuid through partition and format (gdisk, mkfs)
    - for permanent mounting of harddisk, write in /etc/fstab
- device is detected
    - /dev/sda, sdb, sdc, sdd, etc
        - only /dev/sda denotes it is detected but not partitioned
    - /dev/sda, sda1, sda2, etc
        - when it is partitioned, sda1, 2, 3 appears
- hard disk partition and format
    - gdisk
        - ` make partition in harddisk driver `
        - gdisk /etc/sdd
            - confirm the number of partition and the each size before start
            - after making partition, go to making filesystem
        - subcommand (sequential)
            - use ? or help
            - p
                - shows present partition
            - o
                - remove all data and make a protective MBR
            - n
                - ` make new partition `
                - L shows filesystem
                    - 8300 default for linux filesystem
                - start&#9;1
                - last&#9;&#9;+500G&#9;&#9;#G, T, etc can be used
            - for several partition
                - continue n of above stage
            - w
                - write and exit
        - confirm
            - ls /dev
                - Now sdd has sdd1, sdd2, etc
            - format each partition: mkfs
    - mkfs
        - making file system with format
        - mkfs –t ext4 /dev/sdd1
            - ext4 for linux data file system
        - whenever format new disk
            - register uuid in fstab
- UUID
    - ls -al /dev/disk/by-uuid
        - all the partitions are assigned
        - the new partitions appears
- cat /etc/fstab
    - this is static file system
        - permanent mounting harddisk
        - if not listed here
            - the partition will not appear in this file system
                - cannot be seen by “ls “ and “df”
    - following the fstab format
        - ` UUID=___uuid__________    /scratch    ext4   rw, defaults 0 2 `
            - ` UUID=uuid  mount_point linux_fs readwrite, defaults 0 2 `
        - if not uuid format,
            - fix up using uuid
    - load new partition manually in fstab
    - mount -a
        - will upload all the partition in /etc/fstab
        - df will shows all the partitions and mounting points
        - succeed in mounting new harddisk driver --finish--
- mount vs UUID
    - mount
        - temporal identification with device and directory
        - temporally mount Windows partition
            - not list in fstab
        - for backup
            - mount Windows partition in rsync file
            - and umount
    - UUID
        - Constant assign of position of device with directory
- mount: backup for Windows partition
    - df
        - sdc2 is sharewin
        - sdc1 is not shown, which is used for window
        - sdc3 is for Windows 10 OS
    - mount
        - mount /dev/sdc3 /mnt/win
            - if there was /mnt already, it is hidden
            - if not /mnt/win, make it
        - can access to Windows 10 data
            - /mnt/win
        - network mount
            - $mount.cifs //ip/dirname /mount/point -o user=username,
            - $mount -t cifs -w -o username=name -o password=pass //….
            - unmount
                - unmount -f /mount/point
    - rsync
        - rsync.sh for automatic mount and umount
        - scheduling by crontab
    - umount
        - umount /mnt/win
        - note
            - if you do not unmount and modify /mnt by mistake, it will make a problem
- more for format
    - ls –al /dev/disk/by-uuid
        - Id\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ ../../sda5&#9;&#9;for ssd card 4<sup>th</sup> partition
            - The 1<sup>st</sup> partition of 4<sup>th</sup> logical partition is 5<sup>th</sup> partition
    - Copy id into fstab
        - ` UUID=Id_____________________________ /mnt/ssd ext4 defaults 0 2 `
        - ` UUID=Id____________________________ /home ext4	   rw, defaults 0 2 `
        - ` UUID=Id____________________________ /shared ext4    rw, defaults 0 2 `

### summary for new disk

- more detail above 4. uuid & fatab
- ls /dev/sdd\*
    - sdd
        - means sdd is recognized by system but not partitioned yet
- ` make partition using gdisk `
    - check partition
        - sudo fdisk -l
    - gdisk /etc/sdd
        - o, n, 1, enter, enter, enter, w(write and exit)
    - this shows sdd1, sdd2 etc
- format each partition using mkfs
    - mkfs –t ext4 /dev/sddn where n=1, 2, …
- include uuid in /etc/fstab
    - blkid
- how to mount the modified /etc/fstab
    - mount -a

## more (Partition/File System)

### Basic Term: partition, format, filesystem

- Hard disk
    - A hard disk can be divided into several partitions
    - use Hitach, HGST, WD-Gold, not use Seagate
    - bad harddisk makes trouble in whole system
        - linux tries to read harddisk continually
- Partition
    - each partition is one large dataset
        - a partition is formatted with a specific file system
        - At the BIOS level, a disk partition contains sectors numbered 0, 1, etc
    - OS add a directory structure to break the partition up into smaller files
        - assign names to each file
        - manage the free space available to create new files
- File system
    - directory structure and methods for organizing a partition is called a File System
    - kinds
        - Unix and other its clones or Linux
            - “sample.txt” and “Sample.txt” are different
        - DOS and its descendants (Windows 95, OS/2, Windows NT)
    - a hard disk can have different file systems in each partition
        - OS ignores different file system
- DMI
    - Desktop Management Interface
    - requirement to use DMI
        - computer and management software package

### file system

- whatitis
    - also filesystem
    - difference in portability and file size
        - https://www.howtogeek.com/73178/what-file-system-should-i-use-for-my-usb-drive/
- kinds
    - FAT32: basic Windows FS
        - individual file size less than 4G
    - NTFS: upgraded Windows FS
    - Ext2,3,4: linux filesystem
    - NFS: network filesystem
- portability

|  | Linux | Windows 10 | MacOS |
| --- | --- | --- | --- |
| FAT32 | Yes/Yes | Y/Y | Y/Y |
| NTFS | Y/Y | Y/Y | Read only |
| Ext4 | Y/Y | Y w third-party softw | No |

- also dependent on MacOS version
- NFS
    - whatitis
        - share remote directories
        - mount remote directories on your system and work on it as if they are local
        - no need to run the same OS in both systems
    - ` make NSF server `
        - includes three facilities
            - portmap
                - not required in NFSv4
            - nfs
                - translate remote file sharing requests into requests on the local filesystem
            - rpc.mountd
                - responsible for mounting and unmounting
        - nsf-service should run in NSF server
        - important files
            - /etc/exports
            - /etc/fstab
            - /etc/sysconfig/nfs
    - install and running
        - install NFS client
            - ` sudo apt install nfs-common `
                - nfs-utils (centos)
    - mount
        - mount option NFS\_SERVER:exported\_dir mount\_pt
        - e.g.
            - mount -t nfs 10.10.0.10:/backups /home2
                - 10.10.0.10 is IP of NFS server
    - automatic mounting
        - ` make mount_pt `
        - write fstab
            - 10.10.0.10:/dir mount\_pt nfs defaults 0 0
        - run mount by one of the belows to mount the NFS share
            - mount mount\_pt
            - mount 10.10.0.10:/dir
    - unmounting
        - one of two
            - umount /var/backups
            - umount 10.10.0.10:/backups
        - when unmounting fails, check a user
            - fuser -m mount\_pt
        - umount when it is lazy
            - umount -l mount\_pt
        - when NFS system is unreachable, -f for force unmount
            - umount -f mount\_pt

### Directory tree

- detail
    - /&#9;&#9;: root
        - /root&#9;: root home directory
        - in partition, root includes all the directories such as /, /bin, /dev … except /home
    - /bin&#9;&#9;: basic Linux command&#9;cf. /usr/bin
    - /sbin&#9;&#9;: basic Linux command for system manager
    - /boot&#9;: boot loader (grub, conf)
    - /dev&#9;: device file
        - sda, sda1, sda2, sdb, sdb1, etc
    - /opt&#9;: foreign or third-party software packages like INTEL
        - self-contained and not rely on the system’s core libraries or configuration
            - copy as a folder
        - e.g.: Mendeley, Google Chrome, CLion/PyCharm, Zoom, Intel, Teamviewer
    - /etc&#9;&#9;! Linux setting file
        - rd.c, hosts, profile, profile.d, bashrc, passwd, fstab, rc.local
    - /home&#9;: home for users added by useradd
    - /usr&#9;&#9;: package, lib, commander for users
        - /bin&#9;: Debian app manages, sudo apt install …
        - /local&#9;: locally built or installed software for all users
            - /bin: user compiled command
            - e.g. vesta, mendeley
        - /share :
            - /applications: formal app storage installed by apt
                - .desktop \[toml\]
                    - Name=name on menu
                    - Exec=path to file when icon is clicked
                    - Icon=path to image for icon
                    - Categories=name of categories in Menu
                        - cf. mendeley.desktop
    - /var&#9;&#9;: for temporal storage
    - /proc&#9;&#9;: system info
- /proc
    - system information
    - files
        - /proc/cpuinfo
        - /proc/device
        - /proc/filesystems
        - /proc/meminfo
        - /proc/modules
- /etc
    - system configuration file such as
        - /etc/sysconfig, /etc/passwd, /etc/named.conf (DNS conf)
    - debian
        - /etc/apt/sources.list
            - repository sources
        - /etc/debian\_version
            - to see the debian version, cat /etc/debian\_version
    - files
        - /etc/fstab
            - file system table
            - info of UUID
                - names devices in a robust way
                - it works even if disks are added or removed
        - hostname&#9;# chi in chi.kaist.ac.kr
        - /etc/hosts&#9;# ip of nodes and other servers (hostfile, node ip)
            - 127.0.0.1&#9;&#9;localhost localhost.localdomain localhost4 loc…
            - ::1&#9;&#9;localhost …
            - is this nodefile?
        - hosts.allow
            - to open ssh port to a specific ip
            - sshd: 143.248.1.1/32, …
        - hosts.deny
        - /etc/mtab -\> /proc/self/mounts
        - /etc/vimrc
            - setting vi editior
                - do not modify /etc/vimrc
        - /etc/profile
        - /etc/profile.d/&#9;! initial files
        - /etc/bashrc
        - /etc/passwd
            - username:encrypted passwd:UID:GID:full name:home:login shell
            - encrypted passwd=x
                - stored in /etc/shadow file
    - directories
        - /etc/init.d
            - does one thing for your entire system, so it’s very important
            - contains a number of start/stop script for various services
                - from acpid to x11-common
            - command
                - /etc/init.d/command option
                - option
                    - start, stop, reload, restart, force-reload
            - e.g.
                - stop gdm3 before install video card
                    - gdm3 stop
        - /etc/rc.d&#9;&#9;# booting script file depending on the booting level
        - /etc/rc.local&#9;# gather all the executable command in booting
- /dev
    - all the devices
        - hard disk name
            - sda, sda1, sda2 ..
                - sda: total a hard disk
                - sda# is partition
    - /dev/disk
        - directory&#9;by-id
            - id name file is linked to hard disk
                - ata-ST20000DM001-1ER164\_Z4Z3MSXQ -\> ../../sdc1
                - wwn-ST20000DM001-1ER164\_Z4Z3MSXQ -\> ../../sdc1
        - directory by-uuid
            - universally unique identifier for a device
            - uuid file is also linked to hard disk
                - 4668105668104759 -\> ../../sdc1
            - this is used in fstab
- /var
    - temporary stored files
        - installed package using apt is install in /var/cache/apt/archives
- /usr
    - /usr/local
        - /usr/local/Modules
            - install environmental modules
    - /usr/share

### several partitioning technique

- 1 partition method
    - as for ssd, if a part is breaking, whole section will be broken
    - swap has a default partition
    - partition
        - sda1 for / where / includes everything
- sda2 for swap
- 3 partition method
    - /
        - 50 GB, ext4, bootable
    - swap
        - 10 GB, swap
            - used as “file system: ext4, swap”
                - swap is like a memory
    - /home
        - remaining, ext4, not-bootable
- 4 partition method: present
    - 1<sup>st</sup> primary partition: /boot&#9;300M
    - 2<sup>nd</sup> primary partition: /&#9;&#9;60G
        - All other /.. directories will be assigned by system
        - /opt, /var, /usr, etc
    - 3<sup>rd</sup> primary partition: swap&#9;2G
        - Swap: when memory is full, the system goes down or it can use swap
        - To date: rather than expand swap, expand memory
    - 4<sup>th </sup>logical partition: /ssd&#9;&#9;the remaining
        - It will be used personally
        - For large data or fast data analysis
    - Result of installation
        - /dev/sda1/boot&#9;268M
        - /dev/sda2/&#9;55G
        - /dev/sda3 does not appear
- Other disk partitioning
    - 1 disk for 1 partition
        - Ext4 fs (file system) for linux
        - Mount /home here
        - Cf. UUID
    - 1 disk for 2 partition
        - Divide disk into 2 partition
        - Format each partition
            - Ext4 for linux for shared directory
            - Ntfs for window
    - Result
        - /dev/sdb1&#9;/home
            - Should be loaded by UUID and mount –a
        - /dev/sdc1&#9;not shown
            - Ntfs is not shown in linux (df)
        - /dev/sdc2&#9;/shared
- my system – 4 partition
    - /&#9;/dev/sda5&#9;27G/15G/11G&#9;# Storage/Used/Available
    - /boot&#9;/dev/sda3&#9;283M/145M/120M
    - /home&#9;/dev/sdb1&#9;1.8T/40G/1.7T
    - /sharewin /dev/sdc2&#9;917G/3.1G/867G
        - /dev/sdc1&#9;&#9;for window
    - devtmpfs /dev&#9;&#9;24G/0
    - tmpfs&#9;/dev/shm&#9;24G/3.9M
    - tmpfs&#9;/run&#9;&#9;24G/122M
    - tmpfs&#9;/sys/fs/cgroup&#9;24G/0
    - tmpfs&#9;/run/user/1001&#9;4.8G/28K
- fdisk for partitioning
    - dividing storage
        - divide following the storage size rather than % of hard disk
        - /
            - 300M if alone, detail separation&#9;&#9;# 27G, 16G used
        - if devided 3 parts
            - /home, /, swap&#9;3G
                - /home should be larger
        - /boot
            - 50 ~ 100 M&#9;&#9;&#9;&#9;# 300 M (my), 145M is used
        - /var
            - 2G
            - if server for mail, take more
                - if not, 300~500 is ok
                - mail box can locate at home
        - /tmp
            - 500 M for X Window and tmp of window
        - /swap
            - double of memory with enough memory
        - /home
            - the remaining
        - all are reserved in file system table of /etc/fstab
    - e.g. 1
        - su –
        - ` make partition `
            - fdisk /dev/sda
                - m, p, -\> num
                - p
                - 1&#9;possible up to 4 without extension
                - 300M
        - boot partition definition
            - a
                - 1&#9;1<sup>st</sup> partition as boot partition
    - e.g 2
        - general
            - /, /usr, /home, swap, /boot
        - 1<sup>st</sup> boot
            - n, p, 1, +300M
        - /
            - n, p, 2, +30G
        - /usr
            - n, p, 3, +10G
        - extension
            - n, e, 4, (to the end)
        - swap and /home
            - n, +500M, n
        - change swap partition id to 82
            - t, 6, 82
    - check disk
        - fdisk –l
            - /dev/sda: 256 GB
                - /dev/sda1&#9;boot&#9;HPFS/NTFS/exFAT
                - /dev/sda2
                - /dev/sda3&#9;&#9;Linux
                - /dev/sda4&#9;&#9;Extended
                - /dev/sda5&#9;&#9;Linux
                - /dev/sda6&#9;&#9;Linux swap / Solaris
            - /dev/sdb: 2TB
                - &#9;&#9;&#9;Linux filesystem
            - /dev/sdc: 2TB
                - /dev/sdc1&#9;boot&#9;HPFS/NTFS/exFAT&#9;&#9;window system
                - /dev/sdc2&#9;&#9;Linux&#9;&#9;&#9;sharewin

### mount /home in sdb

- sda for ssd
    - move large storage directory to sdb
    - move /usr/local to /home/usr/local
        - ` cd /home `
            - ` mkdir –p usr/local `
                - p for subdirectory
            - ` cp -dpR /usr/local/* ./local `
                - r, R for recursive
                - d for –no-dereference –preserve=links
                - p –preserve=mode, ownership, timestamps
        - ` cd /usr/local `
            - rm –rf MATLAB&#9;&#9;# remove large storage
        - ` cd /usr `
            - ` mv local local_orig	# for system files saving `
            - ` ln –s /home/usr/local `
                - ` make a soft link in the name of local `
    - check
        - du –h /usr/local
        - du –h /home/usr/local
- sdb
    - Move /home, /var to sdb using mount
    - /var
        - mount /dev/sdb1 /mnt
        - ` cp –dpR /var/* /mnt `
        - umount /mnt
    - /home
        - mount /dev/sdb2 /mnt
        - ` cp –dpR /home/* /mnt `
        - ` cd /mnt `

### services

- list the services that are running
    - sudo lsof -iTCP -sTCP:LISTEN -P

### automatic startup

- locate at
    - ~/.config/autostart/name.desktop
    - e.g.
        - teams.desktop
- disable automatic startup
    - tweak/Automatic Starup
        - remove teams
    - method 2
        - add ~/.profile
        - rm ~/.config/autostart/teams.desktop

## Network (LCS)

### Networking

- network connection
    - WAN: Wide Area Network
        - home: ip from outside
    - LAN: Local Area Network
        - home: ip inside home
- connection
    - DHCP: dynamic host configuration protocol e.g. at home
    - manual ip setting

### IPs, loopback, private

- terminology
    - domain: kaist.ac.kr
    - hostname: chi, eta, etc
- netmask or subnetmask
    - to make partial networks
    - IP: &#9;&#9;143.248.247.232&#9;10101010.10101010.10101010.10101011
        - hostname (domain name?) & domain address
        - 143.248.247: Network ID, fixed id, domain address
        - 232:&#9;Host ID, not fixed id&#9;
    - subnetmask&#9;255.255.255.0&#9;11111111.11111111.11111111.00000000
        - 1 for network field
        - 0 for Host field
        - AND operate
            - 143.248.247.0  Network ID
        - and expressed with IP
            - 143.248.247.232/24&#9; this is subnet: address in CIDR form
                - 8 + 8 + 8 = 24 bit is exposed but 232 is masked
    - network prefix &#9;243.248.247.0&#9;10101010.10101010.10101010.000000
        - makes sub networks
    - host&#9;&#9;0.0.0.232&#9;&#9;00000000.00000000.00000000.10101011
- special ip’s
    - Loopback address
        - traffic stays inside the local system and never reaches the network
        - entire 127.0.0.0/8 range (from 127.0.0.1 - 127.255.255.255) is for loopback
        - 127.0.0.1 is most commonly used for self-computer
            - 0.0.0.0, 127.0.0.0 are not used for general usage
        - using 127.x.x.x  always loops back to your machine
    - private network address
        - 192.168.x.x or 10.x.x.x  they require actual network connection
- gateway = router
- name server
    - /etc/resolv.conf
        - nameserver 143.248.1.177
    - …resolvconf
        - this command is optional
        - if resolvconf is installed, do not modify /etc/resolv.conf file
        - if you need to add nameserver manually, add in interfaces
            - /etc/network/interfaces
                - dns-nameservers 1.1.1.1

### IP setting

- how to check
    - ip a
    - ip address
        - replace ifconfig (this is not default, need to be installed)
- setting in top bar menu
    - disconnect
    - set ip
    - connect
- setting in file: /etc/network/interfaces
    - man interfaces
        - what is mapping ?
    - interfaces
        - original
            - ` source /etc/network/interfaces.d/* `
            - auto lo
            - iface lo inet loopback
    - find the names of your interfaces
        - ls /sys/class/net/
            - eth0 eth1 lo vmnet1 vmnet8
    - configuring the interface manually
        - auto eth0
        - iface eth0 inet static
            - address 143.248.247.232
            - netmask 255.255.255.0
            - gateway 143.248.247.1

### ip clusters

- defined at /etc/hosts
    - 127.0.0.1   localhost
    - ### LOCAL network
    - 143.248.247.45 sham.kaist.ac.kr sham
    - ### Cluster group hosts
    - 192.168.100.1    tgm-master.hpc           tgm-master   master master.hpc
    - 192.168.100.1    this\_host
    - 192.168.100.1    home1.hpc                home1
    - ## Infiniband/Omni-path master
    - 192.168.200.1  tgm-master-ib0.hpc       tgm-master-ib0   master-ib0
    - 192.168.200.1  home1-ib0.hpc            home1-ib0

### setup in installation

- Manually input
    - need to be properly set for mirror
    - Domain name, which includes only later parts except computer name
        - kaist.ac.kr
    - local server.local domain = chi.kaist.ac.kr

### two NICs w. two IPs

- ip setting 1
    - ip: &#9;&#9;143.248.37.74
    - gateway: &#9;143.248.37.1
    - netmask&#9;&#9;255.255.255.0
    - DNS:&#9;&#9;143.248.1.177, 143.248.2.177
- check printer id and ip permission of the printer
- ip set 2 (doesn’t need anymore)
    - 143.248.37.48
    - 143.248.37.1
- goto centos, debian

### ip check

- show ip/gateway/nameserver
    - ip a
        - sudo “ip a”:  show enp6s0f1 with inet
    - route –n
    - netstat -rn
    - nameserver
        - cat /etc/resolv.conf
- act/deact network disconnection
    - deact
        - sudo ifdown enp6s0f1
        - “ip a “ show enp6s0f1 w.o. ip
    - activation
        - sudo ifup enp6s0f1
- ssh
    - from pt to eta
        - ` ssh eta or ssh 143…. `
            - ssh: connect to host 143…. Port 22: Connection refused
        - check sshd
            - sudo systemctl status sshd

### iptables – firewall

- iptables is a command-line firewall utility that uses policy chains to allow or block traffic&#9;&#9;&#9;&#9;&#9;cf. apache
- three chains
    - input
        - pkts pytes target port
    - forward
    - output
- default rule
    - iptables –L \| grep policy
        - if ACCEPT: define ip’s to prohibit connection
        - if DROP: define ip’s to permit connection
    - setting
        - iptables –policy INPUT ACCEPT
            - ACCEPT/DROP/REJECT
            - INPUT/OUTPUT/FORWARD
- ping
    - reply from     : bytes time
        - allowing
    - request timed out
        - dropping
    - reply from   : destination unreachable
        - rejecting
- options
    - -L -v

### command line setting

- (or) command line
    - check
        - ifconfig
    - ifdown enp6s0f1
    - ifconfig eth0(enp6s0f1) ip netmask netmask up
    - check
        - route –n
    - route add default gw gateway eth0(enp6s0f1)

### speedtest

- prerequisite
    - ` sudo yum install python-pip `
- ` sudo pip install speedtest-cli `
    - only works for over 2.7 version
- ` pip install speedtest-cli --upgrade `
- ` wget https://github.com/sivel/speedtest-cli/archive/master.zip `
- unzip master.zip
- ` cd speedtest-cli-master `
- ./speedtest.py --bytes

### port

- definition
    - software used as docking point in server
- number
    - range: 0~65535
        - due to 16 bit of tcp/ip
    - well known port: 0 ~ 1023
        - default port in /etc/services
            - 20 – ftp data (transfer data)
            - 21 – ftp control (starting ftp connection)
            - 22 – ssh
            - 23 - telnet
            - DNS: 53
            - 80 – http/www(Apache)
            - x11: 6000
            - http-alt: 8080
- related files
    - named.conf
    - squid have port entry in its squid.conf
- port information
    - /etc/services
    - apache
        - /etc/httpd/conf/httpd.conf
- check port is open
    - sudo lsof -I -P -n \| grep LISTEN
- logical contact location
    - internet protocol: TCP/IP
    - upper protocol than TCP/IP uses pre-assigned port number
    - to use a certain server program, should connect to and bind the set port
    - after bound
        - through TCP/IP, it reaches to the final IP
    - when data arrived, computer transfer the data to the proper software, how
        - using port
    - data flow
        - \[hardware\] -  \[kernel\] -    \[layer\] -    \[application\]
            - lan card  - row level - super deamon - ftp, web, etc
        - super server: inetd
            - always listen after booting
            - if client call comes in
                - read port and server in inetd.conf,
            - application: generate its own port
                - respond to the call through port
- port number
    - 16 bit
        - well known port defined by IANA (Internet Assigned Numbers Authority)
            - 1 ~ 1023
            - HTTP 80
            - HTTPS 443
                - /etc/httpd/conf/httpd.conf
            - FTP 21
            - Telnet 23
            - SMTP 25
        - registered port
            - 1024 ~ 49151
            - ` git 9814 `
        - other port
            - assigned by application service
            - dynamically assigned
    - port number save
        - unix: /etc/services
- check ports in use
    - view port number and service mapping
        - cat /etc/services
    - check opened port
        - sudo lsof -I -P -n \| grep LISTEN
        - ss -tulpn \| grep LISTEN
        - netstat
            - -tuplen \| grep LISTEN
        - nmap&#9;&#9;# yum install nmap
- open 22 for ssh in case
    - a problem when come into the server from external host
        - error: ssh connection rejected
    - check
        - sudo systemctl status sshd
    - ` sudo apt install openssh-server `
        - check again
- open port 443
    - ` sudo vi /etc/httpd/conf/httpd.conf `
        - Listen 80 → Listen 443
    - systemctl restart httpd.service
- terminology
    - inbound vs outbound
        - inbound: for data flow which comes into server
        - outbound: for data flow which goes out of server

### TCP vs UDP

- TCP: Transmission Control Protocol
    - server: make socket
    - client: make socket, allot address, request connect
- UDP: User Datagram Protocol

### https

- whatitis
    - using SSL (secure socket layer), information is encrypted
    - now if you try [https://chi.kaist.ac.kr/~joonho](<https://chi.kaist.ac.kr/~joonho>)
        - makes error
- how to setup
    - Host with a dedicated IP address
        - fixed ID
    - Buy a certificate
        - you need to pay money for SSL for your dedicated IP
        - can not go more
        - try to run Java applet on http rather than https
    - Activate the certificate
    - Install the certificate
    - Update your site to use HTTPS

### apache (httpd)

- check hostname
    - hostname
    - hostname -d&#9;&#9;&#9;! domain
    - hostname -f&#9;&#9;&#9;! full
- installation
    - (debian)
        - ` sudo apt update `
        - ` sudo apt install apache2 `
        - sudo apache2 -version
    - (centos)
        - ` yum update `
        - install FTP server
            - ` yum –y install vsftpd `
            - systemctl enable vsftpd.service
            - systemctl start vsftpd
    - (ubuntu)
- version
    - Debian: sudo apache2 -v
    - CentOS: httpd -v
- configure apache webserver
    - sudo systemctl status apache2
- techniques
    - stop apache from starting in linux
        - (debian) sudo systemctl disable apache2 && sudo systemctl stop apache2
            - sudo systemctl status apache2
            - sudo systemctl is-enabled apache2
            - sudo systemctl disable apache2
            - sudo systemctl stop apache2
            - sudo systemctl mask apache2
            - delete package
                - ` sudo apt remove apache2 `
        - (centos)
            - sudo systemctl status httpd: check running
            - sudo systemctl is-enable httpd: enable at boot time
            - sudo systemctl disable httpd: disable it if enable in boot time
            - sudo systemctl stop httpd
            - sudo systemctl mask httpd
            - verify
                - sudo systemctl status httpd
                - sudo systemctl is-enabled httpd
    - restart apache2 after modifying apache2.conf
        - sudo systemctl restart apache2
        - or
            - sudo /etc/init.d/apache2 restart
            - sudo service apache2 restart
- dd
    - install httpd
        - ` yum install httpd `
        - httpd -v
        - service httpd start
            - the same as systemctl start httpd.service
    - other sources (not now)
        - open firewall for httpd
            - firewall-cmd –add-service=http –permanent
            - firewall-cmd –add-service=https –permanent
            - systemctl restart firewalld
- use iptables (failed) -- this is recommended
    - systemctl stop firewalld
    - can skip if iptables are already installed
        - after firewall installation, port enable
            - ` vi /etc/sysconfig/iptables `
                - -A INPUT …. –dport 80 \[, 22, 21, 3306\] –j ACCEPT
            - port 80 for apache(HTTP), 22 for SSH, 21 for FTP, 3306 for MySql
    - open port for apache in /etc/sysconfig/iptables
        - add two line for port 80
        - -A INPUT -i virbr0 -p udp -m udp --dport 80 -j ACCEPT
        - -A INPUT -i virbr0 -p tcp -m tcp --dport 80 -j ACCEPT
            - what are udp & tcp ?
        - systemctl restart iptables.service
    - skip if already done in OS installation
        - firewall start, automatically started in booting
            - systemctl mask firewalld
                - systemctl start iptables&#9;&#9;&#9;
                    - this will mask firewalld
                - systemctl enable iptables.service&#9;&#9;! start in booting
        - install Apache
            - ` yum install httpd `
            - systemctl enable httpd.service
            - systemctl start httpd
        - open web browser
            - chi.kaist.ac.kr in /usr/share/httpd/noindex/index.html
                - reboot if web browser does not appear in “chi.kaist.ac.kr”
        - to show chi.kaist.ac.kr/~joonho
            - continue below to set UserDir in /etc/httpd/conf.d/userdir.conf
                - UserDir public\_html
            - apache restart: sudo systemctl restart httpd
- structure of Apache2-centOS
    - configuration
        - ServerRoot
            - /etc/httpd
    - main configuration file
        - /etc/httpd/conf/httpd.conf
        - ServerRoot
            - top of directory tree under which the server’s configuration are kept
            - ServerRoot “/etc/httpd”
                - donot add ‘/’ at the end of the directory path
        - Listen
            - allow you to bind Apache to specific IP addresses and/or port, instead of default
        - DocumentRoot “/var/www/html”
            - Relax access to content within /var/www
    - conf.d/\*.conf is loaded
    - default html
        - /usr/share/httpd/noindex/index.html
    - modules
        - modules -\> /usr/lib64/httpd/modules
- setting to use home directory
    - user configuration
        - /etc/apache2/apache2.conf
        - /etc/httpd/conf.d/userdir.conf
            - use userdir module of Apache: mod\_userdir.c
    - configure in conf.d/userdir.conf for apache2-centos
        - UserDir
            - the name of the directory that is appended onto a user’s home directory if a ~user request is received
            - the path to UserDir is accessible
                - ~userid 711
                - ~userid/public\_html 755
                    - otherwise: the client will have 403 forbidden
        - set UserDir
            - #UserDir disabled
            - UserDir public\_html
        - what are these
            - UserDir disabled root
            - UserDir enable joonho
    - how to restart apache?
        - apachectl restart
    - process apache2
        - [https://priyankacool10.wordpress.com/2012/07/21/how-to-configure-public\_html-folder-in-home-dirctory-same-as-varwww-in-apache2/](<https://priyankacool10.wordpress.com/2012/07/21/how-to-configure-public_html-folder-in-home-dirctory-same-as-varwww-in-apache2/>)
        - modified httpd.conf
            - setting UserDir
        - permission
            - /home 711, /joonho 711, /public\_html 755, files 744
        - activate
- setting website view
    - as admin, add web contents to
        - /var/www/html/
    - to suppress the above directory, consult
        - /etc/httpd/conf.d/welcome.conf
- setting user’s website
    - setting
    - web
        - http://server.kaist.ac.kr/~joonho
- another setting
    - modify httpd.conf
        - ` vi /etc/httpd/conf/httpd.conf `
            - add
                - \<IfModule prefork.c\>
                - …
                - \</IfModule\>
    - ` make vhost.conf `
        - ` vi /etc/httpd/conf.d/vhost.conf `
            - NameVirtualHost \*:80
            - \<VirtualHost \*:80\>
                - ServerAdmin
                - ServerName chi.kaist.ac.kr
            - \</VirtualHost\>
- Document Root
    - directory designated for holding web pages
    - it depend on the server setting
        - htdocs, httpdocs, html, public\_html, web, empty
- open website
    - in server
        - [http://localhost](<http://localhost>)
        - [http://127.0.0.1](<http://127.0.0.1>)
        - localhost
            - equivalent to 127.0.0.1 in loopback address
                - cf. /etc/hosts
                    - 127.0.0.1&#9;&#9;localhost
                    - 127.0.1.1&#9;&#9;chi
    - in guest with ip
        - [http://147.248.148.4](<http://147.248.148.4>)&#9;&#9;&#9;# it should be
    - in guest with domain name
        - [http://chi.kaist.ac.kr](<http://chi.kaist.ac.kr>)&#9;&#9;&#9;# it should be
    - in guest with domain name and directory
        - [http://chi.kaist.ac.kr/~joonho](<http://chi.kaist.ac.kr/~joonho>)&#9;&#9;# make apache recognize my id
            - if not conceivable, make it with apache’s UserDir module

### Error in apache2

- it is open locally
    - open
        - [http://localhost](<http://localhost>)&#9;&#9;localhost=127.0.0.1
    - not open
        - but can’t open the webpage in other computer
    - fix up
        - try to open with ip
            - open with ip
        - ` make apache recognize server with name `
        - sudo a2enmod userdir
            - makes recognize [http://chi.kaist.ac.kr/~joonho](<http://chi.kaist.ac.kr/~joonho>) (id=joonho)

### firewall vs iptables

- use firewall
    - [https://blog.lael.be/post/1721](<https://blog.lael.be/post/1721>)
    - stop iptable
        - systemctl stop iptables.service
        - systemctl mask iptables.service
    - install firewall
        - ` yum install firewalld `
        - ` yum install system-config-firewall-tui `
        - systemctl start firewalld
        - firewall-cmd --zone=public --add-port=80/tcp --permanent
        - firewall-cmd --reload
- black list vs white list
    - black list: permit all the IPs then hacker IP is blocked
    - white list: block all the IPs then permit the listed Ips

### Error

- DNS missing
    - Symtom
        - GUI/setting “wired connection” is missing
        - ping google.com is not working
            - But, pint ip is working
            - DNS problem
        - ip a
            - enp1s0 is missing&#9; No problem
            - enp2s0 is working
        - systemctl status networking
            - Active: active (exited)&#9; No problem
    - Modify /etc/resolv.conf
        - ` vi /etc/resolv.conf `
            - nameserver 147.248.1.177
            - nameserver 147.248.2.177
    - restart networking
        - ping ip is working
        - or try service networking restart
    - if you modified /etc/network/interfaces
        - service networking restart
    - cf. /etc/network/interfaces

### Security

- web (httpd)
    - from terminal (including Windows) run curl
        - ` curl -I chi.kaist.ac.kr `
            - show OS versions of chi
    - fixed
        - setting
            - /etc/apache2/apache2.conf
                - ServerTokens ProductOnly
                - ServerSignature Off
            - web restart&#9;(apache2)
        - [https://bloodguy.tistory.com/entry/Apache-%EC%9D%91%EB%8B%B5-%ED%97%A4%EB%8D%94%EC%97%90%EC%84%9C-%EC%84%9C%EB%B2%84%EB%B2%84%EC%A0%84-OS-PHP%EB%B2%84%EC%A0%84-%EB%93%B1-%EC%88%A8%EA%B8%B0%EA%B8%B0-Remove-server-info-and-PHP-info-from-response-header](<https://bloodguy.tistory.com/entry/Apache-%EC%9D%91%EB%8B%B5-%ED%97%A4%EB%8D%94%EC%97%90%EC%84%9C-%EC%84%9C%EB%B2%84%EB%B2%84%EC%A0%84-OS-PHP%EB%B2%84%EC%A0%84-%EB%93%B1-%EC%88%A8%EA%B8%B0%EA%B8%B0-Remove-server-info-and-PHP-info-from-response-header>)

## System

### flask

### update error

- gpg key error
    - (debian)
        - apt
        - gpg --keyserver pgpkeys.mit.edu --recv-key  010908312D230C5F
        - gpg -a --export 010908312D230C5F \| sudo apt-key add -
            - change 010908312D230C5F with keys in error
- error: configured multiple times in /etc/apt/sources.list and /etc/apt/sources.list.d/virtualbox.list
    - multiple times
        - /etc/apt/sources.list
            - deb http://download.virtualbox.org/virtualbox/debian bullseye contrib
    - remove /etc/apt/sources.list.d/virtualbox.list

## Graphic card (CLS)

### centos, debian

- how to check version
    - nvidia-smi
    - lspci –nn \| grep VGA
    - lspci \| grep –I –color ‘vga’
        - … VGA … NVIDIA … \[GeForce GTX 750 Ti\]  -- supermicro (present)

### nvidia - installation

- source: [http://sunyzero.tistory.com/218](<http://sunyzero.tistory.com/218>)
- install C compiler
    - it requires development tools such as C compiler, make
    - command 1: (redhat) centos, fedora, rhel
        - ` yum -y install gcc gcc-c++ make binutils libtool autoconf automake patch pkgconfig redhat-rpm-config gettext `
    - (Debian)
        - ` apt –y install gcc make `
- install kernel header, development header,
    - kernel-headers, kernel-devel which are with the same kernel version
    - redhat
        - command 2
        - ` yum install kernel-headers-$(uname –r) kernel-devel-$(uname –r) dkms `
            - no package dkms
            - install dkms (not necessary)
                - cf. [https://github.com/shawfdong/hyades/wiki/DKMS-on-CentOS-7](<https://github.com/shawfdong/hyades/wiki/DKMS-on-CentOS-7>)
                - ` yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm `
                - ` yum –y install dkms `
        - necessary (?)
            - ` yum install kernel-devel `
            - ` yum install kernel-headers (?) `
    - Debian
        - ` apt –y install kernel-headers-$(uname –r) `
- nvidia driver download
    - install wget
        - ` yum –y install wget `
    - find driver in nvidia website
        - [www.nvidia.com](<http://www.nvidia.com>)
        - driver with .run extension
        - ` wget https://us.download.nvidia.com/XFree86/Linux-x86_64/390.77/NVIDIA-Linux-x86_64-390.77.run `
- blacklist nouveau
    - whatitis
        - nouveau is NVIDIA default driver
        - it conflict with another NVIDIA driver if it is installed
        - so it should be inactive
            - it can be done in the installation procedure, but manually
    - manual method
        - inactive file should be kept in /etc/modprobe.d
            - in installation process, it askes, and if yes, the file is written in /etc/modprobe.d
            - file: nvidia-installer-disable-nouveau.conf
        - command 3: file generation
            - cat \<\< HERE \> /etc/modprobe.d/nvidia-installer-disable-nouveau.conf
            - blacklist nouveau
            - options nouveau modeset=0
            - HERE
- initramfs generated after nouveau inactive
    - initial ram file system – renewal
        - ` cd /boot `
        - ` mv initramfs-$(uname -r).img{,_backup} `
        - redhat
            - command 4: dracut
                - if not this file, booting fails (recover the backup file)
        - debian
            - update-initramfs –u
        - ls initramfs-$(uname -r).img&#9;&#9;! check the new file is generated
    - command 5: reboot
        - if nouveau is running, font would be still small due to graphic card effect
        - if not running, font would be big
    - command 6: check nouveau
        - lsmod \| grep nouveau
- nvidia
    - ctl+alt F2
    - login as root in console
    - X stop
        - recent linux uses systemd which replaces SysV runlevel, so X should stop using systemctl
        - command 7: (centos 7)
            - systemctl isolate multi-user.target
        - Debian
            - init 1
    - command 8: install
        - if preinstalled nvidia
            - nvidia-uninstall
        - ` chmod nvidia…run `
        - ./nvidia….run
            - almost  yes
            - do not make kernel using dkms  no
            - licence  yes
- check
    - nvidia-settings

### nvidia-setting

- command
    - nvidia-setting
- nvidia-setting
    - X Server Display Configuration
        - ordering monitor by moving Layout
            - control mouse continuity
        - click one monitor in Layout
            - check: Make this the primary display for the X screen
                - top bar menu appears

### CUDA

- what is cuda
    - cuda is nvidia’s parallel computing architecture
        - Compute Unified Device Architecture
    - computing evolves
        - cpu to co-processing cpu and gpu
    - cuda is shipped in GeForce, ION, Quadro, and Tesla gpu
    - cuDNN  nvidia cuda Deep Neural Network library
- pre-installation action
    - [https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#introduction](<https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html>)
    - CUDA-capable GPU
        - lspci \| grep -I nvidia
    - a supported version of Linux
        - uname -m && cat /etc/\*release
    - gcc installed
        - gcc --version
    - correct kernel headers and development packages installed
        - Therefore, it is best to manually ensure the correct version of the kernel headers and development packages are installed prior to installing the CUDA Drivers, as well as whenever you change the kernel version.
        - If you perform a system update which changes the version of the linux kernel being used, make sure to rerun the commands below to ensure you have the correct kernel headers and kernel development packages installed. Otherwise, the CUDA Driver will fail to work with the new kernel
        - ` sudo yum install kernel-devel-$(uname -r) kernel-headers-$(uname -r) `
    - download NVIDIA CUDA Toolkit
    - handle conflicting installation method
        - choose installation method
            - distribution-specific packages (rpm and deb)
            - distribution-independent package (runfile packages)
- install cuda toolkit
    - [https://linuxconfig.org/how-to-install-nvidia-cuda-toolkit-on-centos-7-linux](<https://linuxconfig.org/how-to-install-nvidia-cuda-toolkit-on-centos-7-linux>)
    - download repository package
        - [https://developer.nvidia.com/cuda-downloads](<https://developer.nvidia.com/cuda-downloads>)
            - select
                - linux, x86\_64. CentOS, 7
                - one of runfile(local) rpm(local) rpm(network)
    - install cuda repository package
        - rpm -i cuda-repo-\*.rpm
        - if failed
            - check LD\_LIBRARY\_PATH
                - not necessary paths such as anaconda be removed
    - handle the previous version
        - how to remove cuda 7.5
            - ` yum list installed `
                - cuda.x86\_64 1:7.5.18-3.el7.nux @nux-dextop
            - ` yum remove cuda.x86_64 `
            - disable nux\_dextop repo
                - edit nux-dextop.repo in /etc/yum.repos.d/
                    - enabled=0
                - without disabling nux\_dextop, cuda-7.5 in nux\_dextop is firstly found
    - ` yum install cuda `
    - set path and library path
        - ` export PATH=/usr/local/cuda/bin:$PATH `
        - ` export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH `
    - ` source ~/.bashrc `
    - ` which nvcc `
- confirm installation
    - nvcc --version
    - nvidia-smi&#9;&#9;# for nvidia installation
    - compile CUDA sample program
        - ` mkdir cuda-samples `
        - cuda-install-samples-10.1.sh cuda-samples/
        - ` cd cuda-samples/NVIDIA_cCUDA-10.0_Samples/0_Simple/clock `
        - make
            - makes clock in ../../bin/x86\_64/linux/release/
- cuDNN
    - CUDA Deep Neural Network library
    - cuDNN version    supported NVIDIA HW   CUDA version    CDUA Driver version
        - 7.6.2&#9;&#9;Pascal 6.x&#9;&#9;10.1.105       r418.39
    - one of the following architecture with OS is supported
        - On x86\_64 for installing cuDNN with Debian files
            - Ubuntu 18.04, 16.04, 14.04
        - On x86\_64 for installing tgz files
            - any Linux distribution
        - On POWER 9 and POWER 8
            - RHEL 7.5 or later, Ubuntu 18.04
    - one of the following supported CUDA version and NVIDIA graphic driver
        - NVIDIA graphics driver R418 or newer for CUDA 10.1
            - top menu/Applications/others/NVIDIA X Server Setting/… 430
            - CUDA 10.1
    - download and copy
        - tgz file for linux
        - tar
        - ` cp cuda/include/cudnn.h /usr/local/cuda/include `
        - ` cp cuda/lib64/libcudnn* /usr/local/cuda/lib64 `
        - ` chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn* `
    - verifying
        - samples
            - /usr/src/cudnn\_samples\_v7
                - when is this installed?
- cf. tensorflow-gpu

### nvidia-smi

- cuda version
- Processes

### nvidia – old

- installation source
    - install dkms
    - two sources
        - youtube: [https://www.youtube.com/watch?v=\_5RJzZxQ62U](<https://www.youtube.com/watch?v=_5RJzZxQ62U>)
        - Debian wiki: [https://wiki.debian.org/NvidiaGraphicsDrivers#stretch](<https://wiki.debian.org/NvidiaGraphicsDrivers>)
- step by step installation
    - sources.list
        - add contrib, non-free
        - add stretch-backports
            - deb http://httpredir.debian.org/debian stretch-backports main contrib non-free
    - ` apt-get update `
    - ` apt-get install nvidia-detect `
        - nvidia-detect
            - verify driver package
    - dpkg –add-architecture i386
        - might be skipped
        - 32 bit architecture for game
    - ` apt-get install libavcodec-extra `
    - ` apt-get install firmware-linux-nonfree `
    - ` apt-get install vlc gimp smplayer `
    - ` apt-get install –t stretch-backports linux-headers-$(uname –r:sed ‘s,[^-]*-[^-]*-,,’)- `
        - or apt-get install linux-header-$(uname –r:sed ‘s,\[^-\]\*-\[^-\]\*-,,’)
            - did not checked
    - ` apt-get update `
    - ` apt-get install –t stretch-backports nvidia-driver `
    - reboot
- optional – not working
    - ` apt-get install nvidia-smi `
        - to communicate gpu temp to sensors/conky
    - ` apt-get install libgl1-nvidia-glx:i386 `
        - required to game through steam
- installation - old
    - update message
        - mismatching nvidia kernel module loaded
        - now being installed(v 340.106) not match loaded v 340.102
        - how to fix
            - reboot after installation
            - or
                - stop X server (gdm3, kdm, xdm)
                - manually unload moduel “rmmod nvidia”
                - restart X server
    - overall
        - first stop X then install
        - other detail install process, go to nvidia
    - Stop X (gdm of gnome)
        - exit X
            - Ctrl+alt+F1
        - check gdm
            - /etc/init.d
            - find any of gdm
        - stop X
            - sudo /etc/init.d/gdm3 stop
    - install nvidia
        - reference
            - [http://m.blog.naver.com/rbar/220593394847](<http://m.blog.naver.com/rbar/220593394847>)
            - https://linuxconfig.org/nvidia-geforce-driver-installation-on-debian-jessie-linux-8-64bit
        - update
            - add repository address in /etc/apt/sources.list
                - deb [http://ftp.au.debian.org/debian/](<http://ftp.au.debian.org/debian/>) jessie main contrib non-free
                - deb-src [http://ftp.au.debian.org/debian/](<http://ftp.au.debian.org/debian/>) jessie main contrib non-free
            - ` apt-get update (takes time) `
                - you may use us instead of au for faster download
        - install driver
            - ` apt-get install nvidia-driver (takes time) `
    - install nvidia-xconfig
        - ` apt-get install nvidia-xconfig `
    - execution
        - nvidia-xconfig
            - this makes a file
    - reboot, then
        - nvidia-setting
- to protect log-in error
    - keep .profile and .bashrc
        - the role of initial files
- purge and reinstall – very difficult
    - completely remove nvidia
        - [https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](<https://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely>)
        - dpkg -l \| grep –i nvidia
            - shows all the package
        - ` sudo apt-get remove --purge nvidia-* `
            - remove all the related packaged
            - this remove nvidia-common and it is related to “task-desktop (Ubuntu-desktop in ubuntu)
        - ` sudo apt-get install task-desktop `
            - it takes long time
        - sometimes nouveau is blacklisted when nvidia is installed
            - so unblacklist nouveau
            - if you force nouveau to run when booting

### Video card setup - old

- Find model
    - lspci –nn \| grep VGA
    - lspci \| grep –I –color ‘vga’
        - … VGA … NVIDIA … \[GeForce GTX 750 Ti\]  -- supermicro (present)
- nvidia install
    - install nvidia for Debian 8.5, go to Debian 8.5
    - Stop x
        - Exit x
            - Ctrl+alt+F1
        - Check gdm
            - /etc/init.d
        - stop x
            - sudo /etc/init.d/gdm3 stop
    - find, get, and install driver file
        - ` wget http://address `
        - ` chmod 744 driver `
        - ./driver
            - error: unable to find kernel tree
            - [https://ubuntuforums.org/showthread.php?t=1481731](<https://ubuntuforums.org/showthread.php?t=1481731>)
                - ` apt-get install linux-source `
    - in case of fail
        - uninstall
            - ` chmod 755 nvidia_driver `
            - systemctl stop gdm(3)
                - or gdm3
                - gdm: gnome displayer manager
                    - display graphic interface, x window, xorg
                - stop present video to install nvidea
            - nvidia-installer –uninstall
        - install driver
            - NVIDIA-Linux-x86\_64-340.46.run
                - ` module copy error `
                    - be made before CentOS 7
            - run driver program
                - NVIDIA-Linux-x86\_64-352.63.run
            - previous one
                - NVIDIA-Linux-x86\_64-361.42.run
            - present one
                - doesnot support X11 properly
- xorg conf
    - /etc/X11/xorg.conf
- reinstall history
    - ` apt-get install nvidia-installer `
        - ` apt-get purge nvidia-driver `
        - ` apt-get purge nvidia-kernel `
        - ` apt-get purge nvidia-installer-cleanup `
    - ` cd /usr/bin `
        - ls Xorg\*
        - ` cp Xorg.binary Xorg `
        - cat Xorg.wrapper
            - exec /usr/bin/Xorg.binary +iglx
        - startx
        - nvidia-xconfig
    - nvidia-installer --uninstall
    - ` cd /etc/apt `
        - ` vi sorces.list `
    - ` cd sources.list.d `
        - ` mv mendeleydesktop.list ../mendeleydesktop.list.disable `
        - kill –KILL 1802 1809
            - to clean update
        - dpkg –configure -a
        - ` apt-get update `
        - ` apt-get upgrade `
        - ` apt-get install nvidia-driver `
        - dpkg –l \| grep nvidia
            - it shows dirver version: 340.96-1
    - reboot
        - ` apt-get install nvidia-driver `
        - ` apt-get install nvidia-installer nvidia-smi nvidia-xconfig `
        - ` apt-get install nvidia-xconfig `
        - nvidia-xconfig
    - reboot
    - ` cd /etc/X11 `
        - cat xorg.conf
        - nvidia-xconfig
        - ` apt-get install –reinstall X.Org, X, X11 `
        - nvidia-xconfig
            - using X configuration file: /etc/X11/xorg.conf
                - warning: unable to parse X.Org version string
                - Error: unable to write to directory /etc/X11
                    - due to user mode
        - nvidia-settings
            - after install, it gives window
                - X-server information
                    - vendor: X.Org Foundation
        - ` cp xorg.conf.saved xorg.conf		# save before modify to recover original xorg.conf `
- video check
- X-window check (cf. xwindow)
    - checking commander
        - xeyes
        - xclock
        - glxgears
        - glxinfo
    - basic working program
        - gnuplot, molden
            - not working program with error in glxinfo
    - vmd, vesta, cerius

## Hangul

### general

- two step procedure
    - install Hangul
    - setup Hangul
- find what I am using
    - ibus\|nabi
        - ps aux \| grep -E ‘ibus\|nabi’
    - Input Sources
        - Gnome
            - setting/Keyboard (debian 12)
                - Input Sources
                    - Korean (Hangul)
                    - English (US)
            - setting/Region & Language (for other OS)
    - Input Method&#9;&#9;&#9;&#9;&#9;
        - terminal
            - im-config -l
            - im-config -m
- ibus vs nabi
    - nabi
        - after setup, it is not working
            - after install ibus, it is working
    - ibus
        - would work

### ibus

- Hangul installation (Debian 10, 12)
    - ` sudo apt-get install ibus ibus-hangul `
    - ibus is included in CentOS 7.6
- setting
    - ibus-setup
        - tab: input method
            - add Korean-Hangul
    - setup Korean (Hangul) in debian 12
        - setting/keyboard/add Korean (Hangle)
    - if en appears in top bar
        - select 한글
        - setting
            - check: select at the start
    - reboot
    - if it is not working
        - try again several times: setting and reboot
            - till 한 appears on top bar
- setting alternative
    - setting ibus
        - .xprofile: overwrites env setting in .profile
            - for switching IM (input method), write in .xprofile
        - .xprofile
            - ` export GTK_IM_MODULE=ibus `
            - ` export QT_IM_MODULE=ibus `
            - ` export XMODIFIERS=@im=ibus `
            - ibus-daemon -drx
    - setting fcitx5
        - .xprofile
            - ` export GTK_IM_MODULE=fcitx `
            - ` export QT_IM_MODULE=fcitx `
            - ` export XMODIFIERS=@im=fcitx `
            - ibus-daemon -drx
            - fcitx5 -dr
- setting in Debian 10
    - setting/region & language/Input Sources
    - remove other Korean Input source
        - add(+) \> Korean (Hangul) for ibus
            - Korean(hangul) should appear
                - if not, can’t use hangul
        - Be cautious, there are three option
            - Korean,
            - Korean(101/104) obsoleted MS standard
            - Korean (hangul)
    - hangul mode appears on top-bar
        - check Korean (Hangul)
    - reboot
    - ibus has problem with google chrome in debian 12
        - back space and return keys are not working
- if not seen Korean (hangul) - ubuntu
    - install gnome tweaks
    - tweaks
        - keyboard & mouse \> additional layout options \> select Korean Hangul/Hanja keys \> Right Alt as Hangul, right Ctrl as Hanja
    - settings
        - region & language \> manage installed languages \> install Korean
    - logout & re-loginfont
- when brocken in debian
    - install Nanum Gothic in Debian
        - ` sudo apt-get install fonts-nanum `

### nabi

- general
    - scim developed by Chinese
    - ibus developed by Japanese
    - old method
- install
    - ` sudo apt-get install nabi `
- ` vi ~/.gnomerc `
    - ` export XMODIFIERS="@im=nabi" `
        - ` export XIM_PROGRAM=/usr/bin/nabi `
            - ` export GTK_IM_MODULE=xim `
            - ` export QT_IM_MODULE=xim `
            - nabi &
- update
    - im-config
        - im update
            - Yes
        - check hangul
        - or im-config -s nabi
    - reboot (?)
        - etc
            - (?) setting in .imhangul.conf
            - enable\_status\_window = false
            - hangul\_keys = “Hangul”, “\<Shift\>space”, “Alt\_R”
            - hanja\_keys = “Hangul\_Hanja”, “F9”, “control\_R”
    - nabi panel appears on desktop
        - to mv nabi panel to top bar
            - install TopIcons Plus in Gnome Extension
            - then nabi icon mv to top bar
        - mouse right click to see properties
- setting Hangul would be same
- reboot after setting Hangul

### others

- (skip) nabi is not perfect
    - Kwonnam page
        - [http://kwonnam.pe.kr/wiki/linux/inputmethod](<http://kwonnam.pe.kr/wiki/linux/inputmethod>)
    - IM: Input Method
        - nabi + imhangul
        - Nimf (old: dasom)
        - iBus
        - uim
            - no bug
            - uim-byeoru: Hangle input module
            - ` sudo apt-get install uim uim-byeoru `
        - do not install
            - Fcitx
            - scim
    - when error
        - try each method
        - recommend: fcitx, nimf
    - im-config (old: im-switch)
        - change input method
- nabi
    - ` GTK_IM_MODULE=”xim” not to be down in Ajax sites `
        - but context menu disappears
            - nabi + imhangul
                - GTK: imhangul (Firefox is bases on GTK)
                - QT: nabi
    - install (install with ibus would be ok)
        - ` sudo apt-get install nabi `
        - im-config
            - change system configuration -\> yes
            - select “hangul”
        - check .xinputrc
            - run\_im hangul
        - reboot ?
        - check env
            - ` GTK_IM_MODULE=‘hangul2” `
            - ` QT4_IM_MODULE=“xim” `
            - ` XMODIFIERS=“@im=nabi” `
            - if not, add in ./xinputrc
                - e.g. for ibus
                    - ` GTK_IM_MODULE=“ibus” `
                    - ` QT4_IM_MODULE=”ibus” `

### error - ibus

- hangul is not typed
    - fixation
        - in the system change such as nvidia reinstall, home change, reset Korean input sources
        - abrupt Korean disable
            - system – language –
                - remove Korean (hangul) and re-set

### hangul error in VM windows

- encode using Unicode not ANSI
- notepad w. .txt file
    - save
        - error: this file contains Unicode if you proceed the data will be lost
    - cancel
        - check encoding: UTF-8

### Unicode vs EUC-KR

- encoding
    - UTF-8/UTF-16
        - Unicode: 1 to 1 matching with key and letter
        - U+ code table
        - UTF has Hangul of combinational format and complete format
    - EUC-KR/CP949
        - code for 2 byte
        - ascii has still 1 byte
        - CP949
            - extension of EUC-KR
            - EUC-KR has some missing Korean letter -\> Microsoft 949 page of code
    - ASCII
        - 128 code for letter
- test with vi
    - ` vi a.txt `
        - 안abcd녕?
    - depending on system setting and vi file encoding setting
    - file –i a.txt
        - a.txt: test/plaini; charset=utf-8

### hwp viewer

- debian
    - standard method
        - web: [http://www.hancom.com/cs\_center/csDownload.do](<http://www.hancom.com/cs_center/csDownload.do>)
        - download: Linux(Ubuntu)-64 bit
        - sudo dpkg –i hwp…amd64.deb
        - icon appears Application/Office
        - open
            - hwp files are open automatically
            - change default program
    - the second method
        - when standard method fails
            - error in looking for library
        - install updated new library
            - su -
            - ` apt install libjavascriptcoregtk-4.0-dev libwebkit2gtk-4.0-dev `
                - install many libraries
        - link the new library to the necessary library name
            - ` cd /usr/lib/x86_64-linux-gnu/ `
            - ` ln -s libjavascriptcoregtk-4.0.so.18 libjavascriptcoregtk-3.0.so.0 `
            - ` ln -s libwebkit2gtk-4.0.so.37 libwebkitgtk-3.0.so.0 `
        - include library
            - ldconfig
            - include /usr/lib/x86\_64-linux-gnu/ to LD\_LIBRARY\_PATH in .bashrc
        - when hangul…deb fails use rpm file
            - download rpm
            - ` apt-get install alien `
            - alien --to-deb filename.rpm
            - dpkg -I new.rpm
        - when dpkg fails, there occurs error when go to next stage
            - then remove dpkg failure error then proceed
            - ` apt --fix-broken install `

## /proc/version gnome desktop

### X window

- properties
    - X window system (X11 or simply X) is a windowing system for bitmap display, common on UNIX-like OS. &#9;&#9;&#9;cf X11 apps
    - draw on the display device and interacting with mouse and keyboard
    - architecture-independent system for remote graphical user interface
- server
    - X.Org server
        - support 2D rendering acceleration
    - 2D graphic driver
        - Debian
            - 2D graphic drivers: /usr/lib/xorg/modules/drivers
    - package
        - xserver-xorg-video-nouveau installs nouveau\_drv.so
        - Nvidia GeForce driver installs nvidia\_drv.so
- guest
    - Xlib and XCB
- others
    - GTK and GDK are toolkit library for program development
    - DRM: direct rendering manager
        - linux kernel for interfacing with GPU of video card
    - API: application programming interface
        - API can ease the work of GUI components
- adoption
    - unix and linux
    - window: Cygwin/X, Xming
    - OS X: XQuartz
- X11 apps
    - xeyes, xclock, oclock, xcalc, xgc, xedit, xlogo, xman

### gnome, KDE, CDE

- display in desktop
- gnome
    - Graphic interface in Linux environment
    - version
        - gnome-session --version
        - gnome-shell --version
    - install
        - ` apt-get install task-gnome-desktop `
    - GDM: Gnome Display Manager
- KDE
    - based on qt+

### GTK+

- ` GTK = GIMP Toolkit `
    - Library for creating GUI (graphical user interfaces)
    - GtkWidget: Start from widget and end with widget
- version check
    - debian
        - dpkg -l libgtk\*
        - dpkg -l libgtk\* \| grep -e '^i' \| grep -e 'libgtk-\*\[0-9\]'
- GTK input system is X

### GDK

- Inbetween GTK and X Window

## Basic Settings

### setting

- Region & Language
- Universal Access
- Sound
- Power
- Network
- Device

### 4K monitor

- mouse size
    - setting/Universal Access

## GNOME (LCS)

### basic

- GNU Network Object Model Environment
- version?
    - gnome-shell --version
        - 3.28
    - rpm –qa \| grep gnome-shell&#9;&#9;! centos
        - 3.28
- saved gnome-settings
    - sometimes gnome desktop is broken
        - workspace selector disappears
    - when it is working, save by rsync (crontab)
        - ~/.local/share
            - gnome-shell
                - application\_state notifications
            - gnome-settings-daemon
                - input-sources-converted

### install tweaks & extensions

- check tweaks
    - if not
        - install tweak
            - from terminal
                - ` sudo apt install gnome-tweaks `
            - from software center
    - following things
        - [https://itsfoss.com/gnome-tweak-tool/](<https://itsfoss.com/gnome-tweak-tool/>)
        - change themes
        - disable animation to speed up desktop
        - change fonts and scaling factor
    - tweaks/Extensions
        - nothing or just a little
        - install gnome-shell extensions
- install gnome-shell extensions
    - using chrome browser
        - renamed: chrome-gnome-shell  gnome-browser-connector
        - debian
            - ` sudo apt-get install chrome-gnome-shell `
    - check gnome-shell-browser-plugin
        - if not
            - ` yum install gnome-shell-browser-plugin `
    - Ubuntu
        - ` sudo apt install gnome-shell-extensions `
        - relogin
            - tweak/many extension
        - go to website: gnome shell integration add-on
            - [https://addons.mozilla.org/ko/firefox/addon/gnome-shell-integration/](<https://addons.mozilla.org/ko/firefox/addon/gnome-shell-integration/>)
            - click yes
            - click to the extensions repository
                - https://extensions.gnome.org/
                - add extension through website
        - ` sudo apt install chrome-gnome-shell `
            - might be already installed
    - centos
        - ? tweak from yum install gnome-tweak-tool
- install gnome full package
    - ` yum grouplist `
        - exit from anaconda
    - ` yum groupinstall “GNOME Desktop” `
- error in ubuntu
    - tweaks shows only general without side bar
        - drag tweaks pane wider  side menu appears
    - remove side activity bar in desktop
        - setting/appearance/dock/auto-hide when another windows overlaps

### gnome desktop

- GNOME 3
    - gnome shell
        - top bar
            - Activities Overview, clock and calendar, system status icons, system menu
        - system menu
            - update settings, wi-fi info, switch user, log out, turn off system
        - Activity Overview
            - running applications, search entry, dash, workspace list
- top menu
    - power icon
        - setting, lock\_screen, power-off
            - lock\_screen
                - logout
                - screen turns black, sometimes blue ?
            - in case blue
                - click to log on mode
                    - then it goes to lock\_screen
                - otherwise stop internet makes screen out
- size control of title bar of window
    - [https://unix.stackexchange.com/questions/276951/how-to-change-the-titlebar-height-in-standard-gtk-apps-and-those-with-headerbars](<https://unix.stackexchange.com/questions/276951/how-to-change-the-titlebar-height-in-standard-gtk-apps-and-those-with-headerbars>)
    - ~/.config/gtk-3.0/gtk.css
- add application to favorite
    - Application \> Activity Overview \> Show Application \> icon – right click

### tweak

- location of tweak app
    - Applications/System tools/tweak
- Appearance
    - animation ? - default=ON off?
    - try to change shell theme
- Desktop
    - show icons → off
- Extensions
- fonts&#9;&#9;&#9;cf fonts1
    - Window Titles&#9;\> NanumGothic Bold 4
    - Interface&#9;&#9;\> Cantarell Regular 11
    - Monospace&#9;&#9;\> Monospace Regular 11
    - Hinting &#9;&#9;\> Slight
    - Antialising&#9;&#9;\> Rgba
    - Scaling Factor&#9;\> 2.0 -\> 1.5 is better
        - this controls all the size
- Keyboard and Mouse&#9;
    - Mouse
        - Acceleration &#9;&#9;\> default
        - Middle-click Paste&#9;\> on
- Power
    - suspend
        - off
- Sound
- Top Bar
    - Show Application Menu&#9;\> on
- Window Titlebars
    - Titlebar Actions
    - Titlebar Buttons (Windows-like panel max, min-imize)
        - Maximize on
        - Minimize on
        - Placement right
- Windows
    - Attached Modal Dialogs&#9;\> on
- Workspaces
    - Workspace Creation&#9;&#9;\> static
    - Workspaces only on primary display \> on
    - etc
        - gnome-classic
            - appears at bottom bar as consecutive boxes
        - originally
            - appeared in main terminal on rightside
        - now
            - at bottom bar on right side as ¼
                - this is not working properly now

### tweak/Extension

- whatitis
    - after turn on extension, more options appear on each tab
    - if not, controlled in web page
- install
    - ` yum install gnome-extension `
- Usage
    - [https://extensions.gnome.org/](<https://extensions.gnome.org/>)
        - [로그인 정보 삭제]
        - install add-on in mozilla
    - search name of extension
    - click gnome-shell version
        - find: gnome-shell --version in terminal
    - select extension version
    - do not save
    - click ON button above
        - automatically installed
    - reopen tweak
        - involves installed extension
- Extensions
    - usage
        - open extensions.gnome.org at Mozilla
        - login with gmail and hope\*\*\*\*
        - find below apps and turn on: click if it is “OFF”
            - then download
            - reopen tweak
                - it will show the apps
    - Alternatetab
    - Application menu \> on
    - Frippery panel favorites \> on
    - Favorites Menu  Off, not necessary if Frippery panal Favorites is used
    - Horizontal workspaces
        - click Activities or window button
            - off: workspaces appear on right side
            - on: workspaces flap over when page goes over with mouse drag
    - Places status indicator \> on
    - Top icons&#9;&#9;\> on
    - User themes&#9;&#9;\> on
        - “user themes” in gnome-tweak is necessary
            - tweak/Extension
                - if not “user themes”
                    - click “Get more extensions” \> into the web
                    - automatic installation by ON/OFF keys
                    - download file in a certain directory and include in /Extension
    - window list&#9;&#9;\> on
        - display window list at bottom
        - can group when space is limited
    - Workspace indicator
        - indicator on panel (top menu)
        - can put workspace name
    - Workspaces to dock
        - on: appear workspace on left side
        - general
            - position
                - primary monitor
                - right side
            - height
                - center
            - appearance
                - opacity
        - behavior
            - autohide
            - intellihide
            - partial dock
                - show partial
                    - partially hide if not mouse touches
    - dash to dock
        - to remove Ubuntu dock pane on left side
        - might be error
            - turn on/off of dash to dock is not working
        - dconf-editor
            - org-\>gnome-\>shell-\>extensions-\>dash-to-dock
                - find dock-fixed -\> false
                - not yet ?
                - intelihide -\> false
        - on-off switch is working

### dconf-editor for gsetting

- historical change
    - transition from GConf (storing user preference) to GSettings (API, high-level configureation system) and dconf (back end)
    - dconf: key-based configuration system
        - backend of GSettings
        - a range of different settings
    - GSettings: high-level API for application settings, frontend of dconf
    - gsettings: command-line tool to view and change user settings
- dconf
    - low level configuration modifier
- dconf-editor
    - properties
        - dconf GUI
        - ` yum install dconf-editor `
        - shell command
        - top menu can be selected
    - five subdirectories
        - apps, ca, desktop, org, system
- animation to false
    - search mode
        - anima
            - three rules including …/email/..
            - false
    - /org/gnome/desktop
        - unable animation which can affect machine speed
            - /org/gnome/desktop/interface/enable-animation → false
- power saving to blank screen
    - GUI
        - Settings \> Power
            - Power Saving -\> Blank Screen = can be set from 1 - 15 min
    - CLI
        - gsettings get org.gnome.desktop.session idle-delay&#9;   ! show value
        - gsettings set org.gnome.desktop.session idel-delay 3600&#9;   ! (s) 1 hour
    - dconf-editor
        - go to /org/gnome/desktop/session/idle-delay
            - use default value -\> off
            - Custom value \[input\] by second

### font

- font&#9;&#9;&#9;&#9;&#9;&#9;cf terminal setting
    - ` mv nanumfonts ./nanumfonts-ttf `
    - font scale is added in Tweak Tool
        - Scaling Factor is not applied to all the pane
            - better to scale in linux setting
    - some works in Tweak Tool
    - update
        - fc-cache

### terminal

- Preferences
    - Unnamed
        - text:
            - 145 col, 31 rows&#9;cf. different for font size
            - 134 columns 34 rows
        - encoding: Unicode – UTF-8
- font
    - open terminal \> menu (edit) \> Preference \> Profiles \> Unnamed \> Edit
        - terminal size
        - cursor shape
        - custom font
    - font size short cut
        - ctrl + “+/-“
- operation
    - mouse
        - scroll wheel
            - scroll monitor
            - error: scroll history  terminal scroll
- command
    - tput smcup: into alternative screen
        - terminal input: start cup
    - tput rmcup: recover original screen
        - remove cup
    - reset
    - $TERM: terminal type

### gnome-shell theme

- download a new gnome-shell
    - [https://www.gnome-look.org/browse/cat/134/](<https://www.gnome-look.org/browse/cat/134/>)
    - ` mv theme to ~/.themes `
- font size
    - ` vi theme/gnome-shell.css `
        - /\* default text style \*/
            - font-size: 10 pt
        - and so many

### non-solved

- gsettings set org.gnome.desktop.interface document-font-name ‘Droid Sans 14’

## Printer

### Setting

- common
    - power button/setting/Printers
        - shows auto-detected printer
        - error: not detected
            - check printer IP
            - after changing printer IP to an available IP, it is detected automatically
- CentOS,
- Debian
    - Applications/Other/Printer Settings

### error

- installed properly but printing error
    - installation is done,
    - ping works
    - web opens print
    - only printing document invokes error
- check printer permission for ip contact
- “printer in use”
    - printer is not working
    - reboot printer
- printer is inactive

### CUPS – not used now

- cups install
    - Common Unix Printing System
        - computer w. cups: server
            - client request print to server
        - composed of
            - unix print spooler, scheduler filter system, backend system
            - fiter: transform data to recognizable format for printer
            - backend: send new data to printer
        - cups-config for commander
    - install
        - [https://wiki.debian.org/SystemPrinting](<https://wiki.debian.org/SystemPrinting>)
            - ` apt-get install task-print-server `
            - ` aptitude install cups `
        - start the software
            - service cups start
    - version check
        - cups-config --version
- open browser
    - \[eta\]: [http://localhost:631](<http://localhost:631>)
    - one way: you can add printer in
        - for permission to use “add printer”
            - add joonho in /etc/cups/cups-files.conf, the line of SystemGroup
            - sudo systemctl restart cups
            - renew the web page
        - web interface is working
        - change driver using print setting
            - Menu::/Applications/Sundry/Printer Setting
            - Make and Model/ you can change (M651 not M452dw)
                - try to connect but “the printer is not responding”

### install HP

- install hp color laserjet M452dw
    - ` apt-get install hplip `
        - remove dependency and reinstall
            - ` apt-get purge lib_name `
            - ` apt-get install lib_name `
- bellows are unconvinced
    - hplip provided by HP
        - [http://hplipopensource.com/hplip-web/models/color\_laserjet/](<http://hplipopensource.com/hplip-web/models/color_laserjet/>) hp\_color\_laserjet\_m452dw.html
        - download: HP Linux Imaging and Printing – HPLIP
        - dpkg –l hplip
            - check current version
        - get newest version
            - download hplip-3.16.11.tar
            - untar into hplip-3.16.11.run
            - sh hplip-3.16.11.run
                - request su passwd
                - error due to not-supporting Debian 8.7 yet
        - after install hplip
            - go on
    - another way: find driver
        - google: install hp printer in Debian
            - hp site does not support Debian
            - Debian Printing (Common UNIX Printing System)
        - Install printer
            - package system-config-printer supplied by CUB
                - wheez (oldstable) (python)
                    - python-minimal\_2.7.3-4+deb7u1\_all.deb
                    - python\_2.7.3-4+deb7u1\_all.deb

## VM (LCS)

### quick survey for VB: Q&A

- if already have vmware vdk file
    - just install VB to read vmware directory
- The small VM windows problem
    - problem
        - the VM windows does not take a whole panel
    - fix up
        - after booting, install guest addition
            - menu/device/Guest Addition…
                - click it, then it comes into windows driver
        - click Windows driver of Guest Addition, which start installation
            - it takes time and finish installation
        - restart VM
            - at the moment of booting login GUI, the Windows claim the whole area
- usb claim
    - Setting/USB: activate usb2, usb3
        - cannot activate usb in Setting
        - install VB extension pack
    - VM windows:Menu:Devices/USB
        - No USB devices available in VB
            - only USB settings… appears
            - cannot claim usb from menu/device in VM windows
        - fixup
            - sudo adduser joonho vboxusers
            - reboot
                - working with usb 2.0
        - fixup --  similar to VM permission error
            - sudo vigr
            - sudo vigr -s
    - VM windows/Menu/Devices/USB/SanDisk
        - error
    - the inserted usb appears but can’t be read
        - try USB2, USB3 in Settings and retry (reboot VM)

### general

- whatitis&#9;&#9;&#9;&#9;&#9;&#9;cf debian centos
    - virtual machine of Vmware
    - using virtual machine as guest in host
        - host: linux, guest: Windows 10
    - Two ways
        - VMDK  Vbox
            - use bootable disk as VM
            - to make new VM with existing OS
                - VMware can connect new VM to pre-existing OS
                - use VMware to make new .vmdk file
                - VB reads vmdk file
        - vdi
            - ` make directly VM as app `
            - ` make new Virtual Box VM w. installation of new OS `
            - vdi file is generated
        - Otherways
            - Install VMware with trial version
                - VMware Player is also installed but it is also trial version
            - Make vmdk
            - uninstall Vmware
                - sudo vmware-installer -u vmware-workstation
            - Install VMware player
                - This is free-ware
    - Vmware (Workstation and Player) vs VirtualBox
        - virtual box and VM player are freeware
        - Vmware Workstation is commercial for $300 or 30 days trial version

### VB Install

- install sites
    - [https://vitux.com/how-to-install-virtualbox-on-debian-10/](<https://vitux.com/how-to-install-virtualbox-on-debian-10/>)
    - [https://computingforgeeks.com/install-virtualbox-ubuntu-debian/](<https://computingforgeeks.com/install-virtualbox-ubuntu-debian/>)
- straightforward installation
    - update and upgrade
        - ` sudo apt update && sudo apt -y upgrade `
    - download and install
        - dpkg -I Vbox…deb
    - other method
        - (can skip) if kernel update is required
            - \[ -f /var/run/reboot-required \] && sudo reboot -f
        - (can skip) VB apt repo
            - ` sudo apt -y install curl wget gnupg2 lsb-release `
            - ` curl -fsSL https://www.virtualbox.org/download/oracle_vbox_2016.asc|sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/oracle_vbox_2016.gpg `
            - ` curl -fsSL https://www.virtualbox.org/download/oracle_vbox.asc|sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/oracle_vbox.헿 `
            - (old)
                - ` wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add - `
                - ` echo "deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian bionic contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list `
                - (jessie) in sources.list
                    - deb http://httpredir.debian.org/debian/ jessie main contrib
        - add VB repo
            - ` echo "deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list `
        - install VB
            - ` apt-get update `
            - ` sudo apt install linux-headers-$(uname -r) dkms  this might be error `
            - ` sudo apt install virtualbox-6.1 `
        - Download extension pack
            - ` wget https://download.virtualbox.org/virtualbox/6.1.34/Oracle_VM_VirtualBox_Extension_Pack-6.1.34.vbox-extpack `
            - double click in nautilus
                - launch
- VB upgrade
    - Debian
        - gives information
        - select upgrade
            - automatically installs extension pack
        - upgrade guest addition
            - turn on VB
            - in Windows guest OS, there is VB drive
            - click VBoxWindows Additions
                - automatically upgrade
            - NB
                - x86 for 32 bit
                - amd64 for 64 bit

### Make Virtual Machine

- Make vmdk file
    - general
        - ` make VM as a content in hard disk `
            - raw disk vs vdi
                - raw disk: write in Windows hdd
                - vdi: use image of Windows then all the data is written in vdi image
        - possible to make VM with an entire hard disk  raw hard disk access
    - ` make vmdk file for whole region of raw hard disk (use UUID rather than sdx) `
        - VBoxManage createmedium disk --filename /home/joonho/virtualbox/Windows10\_x64.vmdk --format=VMDK --variant RawDisk --property RawDrive=/dev/sdc
            - RawDrive= /dev/disk/by-id/ata-Samsung\_SSD\_870\_EVO\_500GB\_S6R0NM0W309187A
        - N.B. in booting sata device would change, so check by df -h which one is guest OS windows
            - /dev/sda
                - If different, all the shortcut in Windows might be changed
                - Try reboot again to get the same hard disk lable of “sda”
                - If wrong hard device might raise disk space error
            - /dev/sdb or /dev/sdc
        - present device
            - eta
                - nvme0
                    - nvme0n1
                    - nvme0n1p1 ~ p2
                - sda
                    - sda1 ~ 4
                - sdb
                    - sdb1
                - sdc
                    - sdc1 ~ 4
    - sdx can be changed. rather than that, use UUIP
        - UUIP check
            - lsblk  shows sdx partition and size
        - if vmdk was made by sdx, modify vmdk file
            - goto $HOME/virtualbox/….vmdk file
            - modify sda
                - RW 976773168 FLAT "/dev/sda" 0
                - RW 976773168 FLAT "/dev/disk/by-id/ata-Samsung\_SSD\_870\_EVO\_500GB\_S6R0NM0W309187A" 0
            - find UUID
                - ls -l /dev/disk/by-id
                - ata-Samsung\_SSD\_870\_EVO\_500GB\_S6R0NM0W309187A
                - → ../../sdb
- generate VM in VB
    - select New
    - VM is maded in a folder with a name
    - Hardware
        - check Enable EFI (or not)
    - Virtual Hard disk
        - (Do not) create VHD (virtual hard disk)
        - Use an Existing VHD file, that is, vmdk file
            - select the vmdk file (confirm the size of whole disk)
        - (No) do not add a VHD
- more go to setting
    - add guest addition for large VM panels
        - download
    - extension pack
    - check usb
    - shared directory
- get disk permission
    - because the VM – OS is in the different disk, the group disk authority is required for user to touch sdc in VM-Window2 10
        - groups
            - should show: disk
    - vigr
        - add joonho in the line of disk
            - disk:x:6:joonho
    - vigr –s
        - shadow file of vigr
        - do the same thing
    - reboot
- Make VM in VB from vmdk of VMware
    - two branches
        - ` make VM from vmdk (Virtual Machine Disk) of VMware `
            - this is explained here
            - can be tried using 31 day permission of VMware pro
                - VMware player cannot make vmdk file
        - ` make vdi app (v) `
    - Execution
        - Application \> System tools \> VirtualBox OSE
        - $virtualbox or VirtualBox
        - server
            - VBoxHeadless –startvm “VMName”
    - new
        - Name
            - Version is automatically changed
    - Memory
    - HD
        - Do not add a VHD
        - Create a VHD now (vdi)
        - Use an existing VHD file
            - Select the existing vmdk file made by VMware Workstation
- VB extensions and guest addition
    - VB extensions
        - For mouse sync
        - Execute
            - Download
            - Execution by double click at “Files” menu
    - Guest Additions in application
        - For VM OS window size
            - Too small inside VM panel
        - menu:/Device/Insert guest edition…
        - if not autorun
            - file browser: CD driver
                - click VBoxWindowsAdditions.exe (Host+D)
            - (not default) otherwise
                - 내 컴퓨터/CD
                    - VBoxWindowAddisions-amd64, 실행
                    - X86 은 32bit 용
                    - Reboot
- VB extra works
    - Copy & paste
        - Setting: Devices  Shared Clipboard  bidirectional
    - Mouse
        - how to take out mouse during installation
            - Try ctl^shift\_f&#9;or ctl^alt@del
    - Share directory
        - 장치//공유폴더 설정…//공유폴더/ +추가-Directory 선택
        - setting is possible with VB running
- ` make new VB disk as app (make vdi) `
    - New
        - OS 설정
        - 설정 // 저장소 // 컨트롤러:IDE +추가
            - Find window iso file
    - minimum 50 GB
    - select VDI: VirtualBox Disk Image
        - for VMDK (Virtual Machine Disk) go to VMware
    - fixed size vs dynamically allocated
    - after make vdi
        - setting/storage
        - if there is no ide
            - add ide controller
            - input iso file to ide controller empty CD
- install previous
    - debian 10
        - download
            - [www.virtualbox.org](<http://www.virtualbox.org>) / download -\> Windows hosts x86/amd64
                - For 64bit machine
        - after installation of extension pack
            - virtualbox will work
    - install Virtual Box and VB extension pack
        - Virtual box
            - binary installation
                - different on each system such as centOS 7,
            - install with source package
                - [https://www.virtualbox.org/wiki/Downloads](<https://www.virtualbox.org/wiki/Downloads>)
                - VB linux distribution and VB VM VB Extension Pack
        - install VB extension pack
            - for windows size and USB 3.0
            - download
                - version follows the version of Virtual Box
                - \*.vbox-extpack
            - double click in the naustiler (folder explore)

### VB errors

- list
    - share clipboard error
- VBoxMange error
    - VBoxMange
        - vboxdrv kernel module is not loaded, or no module, install it by sudo /sbin/vboxconfig
    - sudo modprobe vboxdrv
        - ` module vboxdrv is not found cf. apt list --installed “v*” `
    - ` apt-get install virtualbox-dkms `
        - virtualbox-dkms is not available
        - just install dkms rather than virtualbox
            - `` sudo apt-get install linux-headers-`uname -r` ``
                - not sure: sudo apt-add-repository main
            - ` sudo apt-get install aptitude `
            - ` sudo aptitude install dkms `
    - VBoxMange: No vboxdrv kernel module again
        - sudo /sbin/vboxconfig
            - vboxdrv.sh  stop VB service and restart VB service
    - ….vmdk with UUID already exists
        - how to remove all the vmdk
            - remove VM in VB
            - remove all the data in the directory
                - might clean
- cannot mount vmdk file
    - it complains a missing operating system
        - vmdk file might be wrong
- Kernel error
    - Kernel driver not installed (rc=-1908)
- hard disk error
    - No disk space
        - Check VM raw disk label is the same such as sda or sdab?
        - If raw disk label changes, the shortcut would be change after booting guest OS
    - in booting, sdx can be changed
        - sda  can change hard disk  use UUID
- UEFI problem
    - does not boot
        - problem
            - bootable error
        - fixup
            - Setting/System/Extended Features
                - enable EFI for EFI cmos system
    - Boot failure
        - In the running process, when start VB-VM after VB-VM installation from VMware
        - Err message
            - FATAL: INT18: BOOT FAILURE
            - FATAL: No bootable medium found! System halted
        - Fix up
            - Settings  System  check “Enable EFI (special OSes only)
                - When guest booting disk has EFI
        - Other checkpoint (not used)
            - Boot order
                - Settings  System  Boot Order
                    - Change order
    - guest VM is stuck in UEFI interative shell mode
        - check off “Enable EFI” but this will fail in another stage
- Device permission error
    - “modprobe vboxdrv” failed
        - error
            - modprobe: FATAL: Module vboxdrv not found
        - fix
            - ` apt-get update `
            - ` apt-get install linux-headers-$(uname –r) `
            - dpkg-reconfigure virtualbox-dkms
                - makes /dev/vboxdrv
            - modprobe vboxdrv
- EFI error
    - symptom
        - Kernel driver not installed (rc=-1908) The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall virtualbox-dkms package and load the kernel module by executing 'modprobe vboxdrv' as root.
        - other warning
            - vboxdrv kernel module is not loaded. Either there is no module
            - available for the current kernel (4.19.0-5-amd64) or it failed to
            - load. Please recompile the kernel module and install it by
                - sudo /sbin/vboxconfig
            - if using EFI Secure Boot, you may need to sign the kernel modules (vboxdrv, vboxnetflt, vboxnetadp, vboxpci) before you can load them.
    - fix up
        - after running
            - sudo /sbin/vboxconfig
                - vboxdrv.sh: Stopping VirtualBox services.
                - vboxdrv.sh: Starting VirtualBox services.
                - vboxdrv.sh: Building VirtualBox kernel modules.
        - can boot
    - if sudo /sbin/vboxconfig fails
        - ` sudo apt install aptitude `
        - ` sudo aptitude install dkms `
        - ` sudo apt install --reinstall virtualbox-dkms `
- fail to share clipboard&#9;&#9;&#9;
    - symptom
        - copy & paste error between host and guest
        - guest to host is working but opposite direction is not.
            - host Linux to guest Windows is not working
    - try
        - 0<sup>-th</sup> try: for next
            - in Excel, click Esc to release copy state
            - open Windows memo, copy short text
            - copy text in Debian terminal  paste in Windows memo
        - 1<sup>st</sup> try: Menu/Devices/shared clip board
            - change into disable
            - turn on bidirectional
        - 2<sup>nd</sup> try: Kill and restart VBoxTray.exe
            - 1. finish job
                - Task manager (short key: ctrl + shift + Esc )/Details
                    - find VBoxTray.exe  finish job (mouse right button)
            - 2. restart job
                - win + R
                - C:\\Program Files\\Oracle\\VirtualBox Guest Additions\\VBoxTray.exe
            - This is working
        - 3<sup>rd</sup> try to restart VBoxTray.exe (not necessary yet)
            - open Dos
                - ctrl + shift + Esc  this is process
            - taskkill /f /im VBoxTray.exe&#9; turn off
            - start “” “C:\\Program Files\\Oracle\\VirtualBox Guest Additions\\VBoxTray.exe”
            - try copy and paste from host to guest
    - origin of error
        - Excel copy claims copy & paste to clipboard
            - after then, Windows
        - Do not use Excel copy
- other errors
    - 한/영 is not working in 103/106 keyboard
        - change to 101(3), then can use shift+space
    - Slow in opening shared directory
        - solved but don’t know why
    - slow in mouse response
        - symptom
            - in click of icon
            - in click of cursor in MS word
        - reboot host
    - lagging in mouse move
        - turn off System/process, Acceleration
    - Gnome is stuck w.r.t. mouse
        - if Devices/USB devices/Logitech USB Receiver is checked
            - encourage not to use wireless mouse
        - solve – how to escape from virtual box
            - Ctrl+alt+del makes virtual box stop and can wake a linux screen
            - It happens when switch to full screen works,
                - mouse is still somewhere on virtual box
            - fix: anyway close virtualbox
                - click window icon which shows all the application small
                - then click any application, then all things work
    - claim USB
        - first USB is claimed by host
        - check Devices/USB devices/the USB connected
            - automatically host loses USB and new driver appears in Computer/
        - setting/USB
            - check enable USB controller
            - check enable USB 2.0 controller
- VB Windows 11 blackout error
    - trial to awake
        - Host + F  full screen&#9;&#9;Host is right control
        - Display reset
            - View/virtual screen 2  reset guest display
        - ctrl + alt + del
            - Host + del or Input/Keyboard/ctrl+alt+del
        - in power-off options
            - sent the shutdown signal
    - If all fails,
        - Power-off
        - reinstall Guest Additions
    - further setting
        - only VBoxSVGA is working for Windows VB
        - chipset ICH9

### VM error

- VM update error
    - GPG error
        - Err:4 http://download.virtualbox.org/virtualbox/debian buster InRelease
        - The following signatures couldn't be verified because the public key is not available: NO\_PUBKEY A2F683C52980AECF
        - W: GPG error: http://download.virtualbox.org/virtualbox/debian buster InRelease: The following signatures couldn't be verified because the public key is not available: NO\_PUBKEY A2F683C52980AECF
    - strategy
        - ` wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add – `
        - ` wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add - `

### VMware/VB setting

- General
- System
    - Motherboard
        - Base Memory 8G
        - Boot Order: hard Disk
        - chipset: PIIX3&#9;&#9;&#9;# chatgpt advices ICH9 after VB blackout
        - Pointing device: USB Tablet
        - Extended Feature
            - Enable I/O APIC
            - Enable EFI: UEFI
                - in case using physical hard disk for independent booting
                - use the same firmware of the host OS
    - Processor
        - Processors 4 cpu
        - turn off
            - enable nested VT-X/AMD-v &#9;#
                - can make “mouse lagging” and “movie lagging” problem
                - can make VM in VM
        - turn off
            - Enable PAE/NX&#9;# this is for old cpu
            - cf. np=1, ncpp=2
                - visualization engine: Automatic mode, Virtualize Intel VT-x/EPT or AMD-V/RVI
                - only np = 1, ncpp = 1 is allowed due to socket setting
    - Acceleration
        - Paravirtualization interface:
            - Default
        - Hardware Virtualization
            - Turn on: Enable Nested Paging
                - If not, windows booting may fail
- Display
    - VBoxSVGA for VB
        - VMSVGA might be for linux Guest.
            - in Windows VM, guest addition (windows resizing) is not working
- Storage
    - SATA
        - vmdk in Port 0
        - VBoxGuestAddision download and insert in Port 1
- Audio
    - mic and speaker in teams
        - Menu/Device/Audio/
            - Enable Audio
                - ALSA Audio Driver is working for SamSung machine
                    - try all the drivers: ALSA, PULSE, …
                    - Intel
                - extended feature
                    - Check: Audio input
                    - Check: Audio output
- Network
    - Adapter
        - need to assign both NAT and Bridged Adapter
        - Adapter 1: NAT
            - Network Address Translation
            - Let VM use the HOST network
            - Host setting: DHCP
        - Adapter 2: Bridged Adapter
            - Name: enp2s0 - Host’s IP name
            - Let VM connect local network to find computers in network
                - this make to run network printer also
        - Adapter 3: Bridged Adapter
            - Name: find wifi hardware
            - To sync onedrive which might be blocked through wired network
    - memory: 4096 MB
    - hard disk = scsi (default)
        - LSI Logic SAS
    - virtual disk type
        - IDE, SCSI, SATA, NVMe
            - Now the device is connected by SATA
    - Disk
        - use a physical disk
            - error: physical disk is not shown
                - get permission
        - select id of physical disk of guest OS
            - ls -al /dev/disk/by-id
                - select sda rather than sda1 for part1 and choose “entire disk”
                - eta
                    - windows 10 locates at /dev/sda
                    - with sda1, sda2, sda3, sda4
                    - sda1: EFI
                    - sda2: reserved
                    - sda3: data
                    - sda4: recovery
        - usage
            - use entire disk
                - or partition
    - ignore last message
        - need to install OS in new machine
        - need to install Vmware Tools
            - power on VM
            - load os and log in if necessary
            - menu: VM \> install Vmware Tools…
- Serial port
- USB
    - 2.0 & 3.0 are possible with VB Extension pack
- Shared Folders
    - + add shared folder
        - find the linux folder then make a mount point
    - checkbox: auto-mount
        - if check, the windows driver letter is assigned by default
        - if uncheck, you can assign driver letter in windows
            - location of shared folder
                - network driver/
- User Interface
- Another Settings…
    - Hardware
        - memory: 4096 MB
        - turn off
            - Virtualize Intel VT-x/EPT or AMD-V/RVI
            - np=1, ncpp=2
                - visualization engine: Automatic mode, Virtualize Intel VT-x/EPT or AMD-V/RVI
        - hard disk = scsi (default)
            - LSI Logic SAS
        - CD(sata): status=connected, connect at power on,
            - connection: use a physical drive: Device /dev/sr0
        - Network Adapter NAT
        - sound card: auto detect
        - printer
        - usb: 1.1, automatic, share Bluetooth
        - display: auto detect
            - do not accelerate 3D graphics
            - monitors: use host settings for monitors
            - graphics memory: 1GB (recommended)
    - Options
        - general: OS
        - power: no options,
        - shared directory
            - VM/setting…/options/shared directory
                - it is better to close OS and set
            - it appears in network as host
                - vmware-host
            - setup the directory path from / of root, not use link\_directory at $HOME and use the same name for nick name as the name of linux\_dir
        - snapshots: just power off
        - autoprotect disable
        - guest isolation: enable both
        - access control: not encrypted
            - allow usb devices to be connected to the guest
        - vmware tools: time sync off
            - updates: use application default (update manually)
        - vnc connection: disable
        - appliance: nothing
        - autologin: log in as root
        - advanced: nothing
    - copy host and paste guest
        - install VMware Tools installation
            - VM/Install Vmware Tools
    - window fit to monitor size
- Problem
    - Now slow in running MS-Word, especially making new line with list indentation
        - turn off 3D acceleration of display
    - not communicate between host and guest
        - fixed after Vmware Tools installation
    - network is on but internet is not working
        - host ip should be working
        - set guest network with DNS only
    - in searching shared directory at first time and saving there is so slow
        - setup shared directory in the name of linux directory
        - better to use the original directory path rather than use $HOME/link\_dir
- Mouse
    - Grab: mouse click&#9;# Edit/Preference/
    - Release: Ctrl + Alt

### VB setting more

- Host key
    - default
        - Host Key Combination&#9;Right Ctrl
        - shown in bottom right corner
        - in notebook there is no right^
            - use different key
        - do not use alt
            - alt is used for short key in linux, windows, etc
    - change host key
        - env/input/host key combination: short key
- on VM
    - Input/Keyboard/keyboard setting…
- VirtualBox/View
    - screen
        - host + F: for full screen &#9;# be careful to use this
- VirtualBox/Devices
    - claim usb
        - USB Devices – select the proper one
    - when usb is connected, first claimed by host
    - virtual box can claim the usb by choosing usb devices
- Settings
    - setup of virtual box
    - number of cpu
    - share directory of ext4 fs
        - ` mkdir win under mounted directory `
            - do not share /shared of linux device
                - share normal directory of /sharewin/win in virtual box
        - cf. shared directory in Windows Host and linux guest
            - install guest addition
                - after booting guest linux
                - through menu of device/Guest Addition….
            - ` make shared directory in Windows Host `
                - e.g. C”\\virtualbox\_share
            - register the shared directory of Windows Host in Virtual Box
                - left menu: shared folder/ use green plus icon for generation
                - check “always use”: auto-mount may not work well
            - mount the shared directory in linux-guest
                - generate directory
                    - $sudo mkdir /mnt/share
                - mount
                    - $sudo mount –t vboxf virtualbox\_share /mnt/share
                        - virtualbox\_share is the directory name in Windows Host
            - confirm: the file in the directory can be seen in both OS’s.
- preference is saved in ~/VirtualBox\\ VMs
    - ini-setup
        - operating system: Win 7 64x
        - shared directory
            - appears as driver not network
- Win X64 in Virtual Box
    - time & region
        - region of seoul if it is set in Linux properly
    - language
        - install Korean
    - printer
        - install wizard for printer
            - using network ip
- VMware technique
- VMDK
    - usage
        - using VMware Workstation, make VM of vmdk
        - let VB (virtual box) make VM in ‘Virtual Box’ directory using vmdk made by Vmware workstation
    - similar packages
        - virtual box can be installed through network
        - VMware-player…
            - just player
        - VMware-Workstation…
            - can make virtual machine and run it
    - sub tool package
- Install as root
    - run install package
        - ./Vmware-Workstation-Full-12.0.1-316…x86\_64.bundle
    - with license file
        - [로그인 정보 삭제]
        - GCC version error
    - if fails,
        - download and install version 16 at the moment
- ` make virtual machine as user `
    - execution
        - icon in Applications/System Tools/WMware Workstaion
        - vmware in terminal
    - File/New virtual machine…
        - custom:
        - typical: generates new OS
    - custom
        - I will install OS later
        - Bios rather than EFI
            - in case using physical hard disk for independent booting, use the same firmware of the host OS
        - disk
            - use a physical disk
            - error: physical disk is not shown
                - get permission
            - select uuid of physical disk of guest OS (windows 7)
        - ignore last message
            - install OS in new machine
- permission error
- install VMware Tool package
    - general
        - every VM machine needs to install Tool package
    - menu bar
        - VM/Install Vmware Tool Package
            - making CD driver in /computer/D
    - /computer/D
        - execute /setupx64.exe
        - long installation time
    - rebooting
        - VM/ menu is changed into
            - Reinstall Vmware Tools…
    - solve problem
        - ^C (ctrl+C) and ^V is working between host and guest computer
        - fit virtual screen to VM window
- Setting in menu VM/Settings…
    - Hardware
        - memory: 4096 MB
        - np=1, ncpp=2
            - visualization engine: Automatic mode, Virtualize Intel VT-x/EPT or AMD-V/RVI
        - hard disk = scsi (default)
        - CD(sata): status=connected, connect at power on,
            - connection: use a physical drive: Device /dev/sr0
        - Network Adapter NAT
        - sound card: auto detect
        - printer
        - usb: 1.1, automatic, share Bluetooth
        - display: auto detect
            - do not accelerate 3D graphics
            - monitors: use host settings for monitors
            - graphics memory: 1GB (recommended)
    - Options
        - general: OS
        - power: no options,
        - shared directory
            - VM/setting…/options/shared directory
                - it is better to close OS and set
            - it appears in network as host
                - vmware-host
            - setup the directory path from / of root, not use link\_directory at $HOME and use the same name for nick name as the name of linux\_dir
        - snapshots: just power off
        - autoprotect disable
        - guest isolation: enable both
        - access control: not encrypted
            - allow usb devices to be connected to the guest
        - vmware tools: time sync off
            - updates: use application default (update manually)
        - vnc connection: disable
        - appliance: nothing
        - autologin: log in as root
        - advanced: nothing
    - copy host and paste guest
        - install VMware Tools installation
            - VM/Install Vmware Tools
    - window fit to monitor size
- Problem
    - Now slow in running MS-Word, especially making new line with list indentation
        - turn off 3D acceleration of display
    - not communicate between host and guest
        - fixed after Vmware Tools installation
    - network is on but internet is not working
        - host ip should be working
        - set guest network with DNS only
    - in searching shared directory at first time and saving there is so slow
        - setup shared directory in the name of linux directory
        - better to use the original directory path rather than use $HOME/link\_dir
- Mouse
    - Grab: mouse click&#9;# Edit/Preference/
    - Release: Ctrl+Alt
- from windows file
    - download
        - [www.virtualbox.org](<http://www.virtualbox.org>) / download -\> Windows hosts x86/amd64
            - For 64bit machine
    - ` make new machine `
        - In “Oracle VM virtualBox” / new make -\> OS, version (Microsoft Windows, Window 7 – this is for 32 bit)
        - 새 가상 디스크 만들기
            - 새로만들기 -\> OS 설정
            - 설정 // 저장소 // 컨트롤러:IDE +추가
                - Find window iso file
        - Window 7 설치 후
            - 창이 너무 작음
                - 장치//게스트 확장 장치 설치 (Host+D)
                - Option
                    - 내 컴퓨터/CD
                        - VBoxWindowAddisions-amd64, 실행
                        - X86 은 32bit 용
                        - Reboot
            - 공유폴더 설정
                - 장치//공유폴더 설정…//공유폴더/ +추가-Directory 선택
    - dynamic extension storage
        - Operating machine: select / icon “=\>”
    - mouse sync
        - 장치/게스트 확장 설치… -\> VBoxWindowsAdditions.exe 실행
- how to take out mouse during installation
    - Try ctl^shift\_f&#9;or ctl^alt@del
- how to see directory of guest machine
    - 장치/공유폴더/+&#9;# you can see the host machine (main server)
    - 장치/공유폴더/+&#9;# you can see the host machine (main server)
- others
    - dynamic extension storage
        - Operating machine: select / icon “=\>”

### VMware

- install
    - basic
        - download .bundle
        - sudo sh Vmware-Workstation.bundle
            - superuser passwd
    - To install non-commercial VM player
        - uninstall VM workstation limited
            - as superuser
            - in terminal
            - vmware-installer –u vmware-workstation
- Make vmdk via VMware
    - VMware has 30 days trial version and commercial for $300
        - virtualbox and VMplayer are freeware
    - it can make VM with connection to the pre-existing OS
        - virtualbox cannot do this though it can make its own VM?
- download and install
    - download and install the recent version
        - v. 16 can be install
            - ` wget https://download3.vmware.com/software/wkst/file/VMware-Workstation-Full-16.1.0-17198959.x86_64.bundle `
            - ` chmod a+x …bundle `
            - $vmware
                - ` make error in root, graphic error `
        - old version is not installed anymore (due to gcc version error)
            - v.12 error in centos 7
            - ./Vmware-Workstation-Full-12.0.1-316…x86\_64.bundle
                - installed /var/lib/vmware/Shared VMs
                - https port: 443
                - error in centos 7
                - with license file
                    - [로그인 정보 삭제]
- ` make VM (vmdk) `
    - execution
        - icon in Applications/System Tools/WMware Workstaion
        - $vmware (or)
    - VM panel
        - Create a New VM
    - VM configuration
        - Custom (advance):
            - select Custom (advanced) to select device with OS
        - typical: generates new OS
    - Hardware compatibility
        - check
    - Install OS from
        - use a physical drive
        - use ISO
        - I will install OS later
            - The VM will be created with a blank HD (hard disk)
            - select this
    - Select guest OS
    - set VM name
- permission error
    - symptom
        - when you make new virtual machine, no available physical disk is shown
        - when trying to open VM, permission error occurs
    - get disk permission
        - vigr
            - add joonho in the line of disk
                - disk:x:6:joonho
            - you have modified /etc/group
            - you may need to modify /etc/gshadow for consistency
            - use ‘vigr –s’
        - vigr –s
            - shadow file of vigr
            - do the same thing
        - reboot
    - not reliable
        - ` chmod 666 for /dev/sdc, /dev/sdc1, /dev/sdc2 `
- (not used hereafter) install VMware Tool package
    - general
        - every VM machine needs to install Tool package
    - menu bar
        - VM/Install Vmware Tool Package
            - making CD driver in /computer/D
    - /computer/D
        - execute /setupx64.exe
        - long installation time
    - rebooting
        - VM/ menu is changed into
            - Reinstall Vmware Tools…
    - solve problem
        - ^C (ctrl+C) and ^V is working between host and guest computer
        - fit virtual screen to VM window

### VM Player

- When VB fails in opening vmdk
    - VM Player might open the vmdk after windows booting succeeds
        - cf. Debian supports dual booting correctly
- version
    - bunch version with Vmware
        - (Expired license) but still working
- Reading vmdk
    - read almost all the existing properties
    - additional setting
        - Shared directory
- install VMware Tools for full size windows pane
    - in menu in VM panel
        - Virtual Machine/(bottom) Install Vmware Tools…/
            - should appear new windows
                - Download and Install
            - if not automatically start
                - Windows+R  d:setup.exe
- Setting in Windows
    - fonts in 4K monitor
        - mouse  right button, display setting  size magnification rate
            - 150 %
    - screen saver stop
        - mouse  right button, display setting
            - 안 함, 안 함

### VM & VB error

- contents
    - permission error
    - mouse is not working in VM pane
- permission error in opening VM
    - symptom
        - when you make new virtual machine, no available physical disk is shown
        - when trying to open VM, permission error occurs
    - not reliable
        - ` chmod 666 for /dev/sdc, /dev/sdc1, /dev/sdc2 `
- permission error in writing on shared directory
    - check directory authority in linux
- cannot see shared directory
    - insert guest additions CD
- Failed to open a session for …
    - message: USB 2.0 controller stat is part of ….
        - To fix this problem,
        - install Oracle VM VirtualBox Extension Pack or disable USB 2.0 support
    - cannot start VM due to usb setting in VM
        - normally it happens after update of OS
    - other symptom
        - cannot load usb
    - fix
        - download extension pack and install
- VB error
    - mouse error in VM
        - mouse is working in main OS
        - mouse does not appear inside VB
            - only a present pane in VB is working
        - fix
            - ^@del: save VM and quit but do not turn off main OS
    - after stop windows update
        - lagging occurs later
        - fail to reboot
            - cf. VM player is working
- VMware technique
    - error: Collide with KVM?
        - when KVM is used for switching
        - Error
            - mouse point does not activate the pointed icon
                - when you put the mouse pointer on an icon, the icon should be activated
        - solution
            - turn off VM and on again
            - recommend
                - do not use KVM rather than that, use remmina
    - shared folder is not seen after windows update
        - reinstall “Guest Additions”
    - ^C & ^V in guest and host machine
        - Ubuntu
            - select VM in VM window
            - setting/general/advance/
- VM Error
    - VB error: cannot connected
        - procedure
            - open VB
            - icon: unconnected
            - detail: Cannot attach medium '...xxx.iso' \{...\}: medium is already associated with the current state of machine uuid \{...\}!"
        - not working
            - File/Virtual Media Manager/Optical disks
            - remove the problem disk
            - click refresh
        - remove in vb text file
            - ` cd VirtualBox\ VMs/ `
            - ` cd VB_Windows10		! name of VM `
            - ` vi VB_Windows10.vbox `
                - remove problematic image tag
                    - \<image uuid….
                - refresh or reopen VB
            - VM is normal

### VM Windows error

- symptom
    - Han/Eng key is not working in Guest Windows
    - 103/106 key was set and Han/Eng key is working in Host Windows
- fix up 1
    - set keyboard to key 101(type 3)
        - shift+space for Han/Eng conversion
- fix up 2

### VM performance

- Problem & solved
    - “modprobe vboxdrv” failed
        - error
            - modprobe: FATAL: Module vboxdrv not found
        - fix
            - ` apt-get update `
            - ` apt-get install linux-headers-$(uname –r) `
            - dpkg-reconfigure virtualbox-dkms
                - makes /dev/vboxdrv
            - modprobe vboxdrv
    - Slow in opening shared directory
        - solved but don’t know why
    - slow in mouse response
        - symptom
            - in click of icon
            - in click of cursor in MS word
        - reboot host
    - Gnome is stuck w.r.t. mouse
        - if Devices/USB devices/Logitech USB Receiver is checked
            - encourage not to use wireless mouse
        - solve – how to escape from virtual box
            - Ctrl+alt+del makes virtual box stop and can wake a linux screen
            - It happens when switch to full screen works,
                - mouse is still somewhere on virtual box
            - fix: anyway close virtualbox
                - click window icon which shows all the application small
                - then click any application, then all things work
    - claim USB
        - first USB is claimed by host
        - check Devices/USB devices/the USB connected
            - automatically host loses USB and new driver appears in Computer/
        - setting/USB
            - check enable USB controller
            - check enable USB 2.0 controller
                - 3.0 is not working
- using virtual box after setup
    - VirtualBox/View
        - screen
            - host + F: for full screen &#9;# be careful to use this
    - VirtualBox/Devices
        - claim usb
            - USB Devices – select the proper one
        - when usb is connected, first claimed by host
        - virtual box can claim the usb by choosing usb devices
- preference is saved in ~/VirtualBox\\ VMs
    - ini-setup
        - operating system: Win 7 64x
        - shared directory
            - appears as driver not network
- Win X64 in Virtual Box
    - time & region
        - region of seoul if it is set in Linux properly
    - language
        - install Korean
    - printer
        - install wizard for printer
            - using network ip

### VM printer

- as normal as Windows
- network printer
    - [http://printer\_ip](<http://printer_ip>)
    - ping in command window
    - check ip permission in printer
        - requires admin passwd
    - cf. network adapter setting for network printer

### VM w. system change

- disk permission for direct use
    - physical hard disk check: the same
    - group “disk” authority is needed
        - /etc/group and /etc/gshadow
            - disk:x:6:joonho
        - using
            - sudo useradd –G disk joonho
            - sudo usermod –a –G disk joonho
                - vigr –s is not working in fedora
        - check $groups
            - joonho, wheel, disk, vboxusers

### make new VM – VM setting

- General
    - Basic
        - Name: Windows 10
        - Version: Windows 10 (64-bit)
    - Advanced
        - Sahred Clipboard, drag & drop = bidirectional
- system
    - Mother board
        - memory 8 G
        - chipset PIIX3
        - Pointing device: usb tablet
        - Extended Feature enable I/O APIC
    - processor 4 cpu
        - execution cap 100%
    - acceleration
        - Paravirtual..default
        - Hardware virtual.. all check
- Display
    - video memory 128
- Storage
    - Storage tree
        - Controller: SATA
            - Vind7\_6d….vmdk&#9;&#9;! vmdk is source made by vmware
        - create virtual hard disk
            - new
            - VDI&#9;&#9;&#9;! made by virtualbox
- network
    - Adapter 1
        - enable network adapter: &#9;NAT
        - if you are using separate ip, different from linux
            - Bridged Adapter
- serial ports: none
- usb
    - enable USB controller
        - enable usb 2.0
- shared folder
    - + for add
        - full path from /
        - - dir name = shared directory name
        - auto mount
    - share directory of ext4 fs
        - ` mkdir win under mounted directory `
            - do not share /shared of linux device
                - share normal directory of /sharewin/win in virtual box
        - cf. shared directory in Windows Host and linux guest
            - install guest addition
                - after booting guest linux
                - through menu of device/Guest Addition….
            - ` make shared directory in Windows Host `
                - e.g. C”\\virtualbox\_share
            - register the shared directory of Windows Host in Virtual Box
                - left menu: shared folder/ use green plus icon for generation
                - check “always use”: auto-mount may not work well
            - mount the shared directory in linux-guest
                - generate directory
                    - $sudo mkdir /mnt/share
                - mount
                    - $sudo mount –t vboxf virtualbox\_share /mnt/share
                        - virtualbox\_share is the directory name in Windows Host
            - confirm: the file in the directory can be seen in both OS’s.
- extension pack in download fold
    - Guest Additions in application
        - menu:/Device/Insert guest edition…
- update
    - ` apt-get –t Jessie-backports install virtualbox `

## Docker

### install

- centos
    - [https://www.itzgeek.com/how-tos/linux/centos-how-tos/install-kvm-qemu-on-centos-7-rhel-7.html](<https://www.itzgeek.com/how-tos/linux/centos-how-tos/install-kvm-qemu-on-centos-7-rhel-7.html>)
    - QEMU-KVM
        - cpu spec
            - egrep '(vmx\|svm)' /proc/cpuinfo
                - it should show “vmx" or “svm"
        - ` yum install -y qemu-kvm qemu-img virt-manager libvirt libvirt-python libvirt-client virt-install virt-viewer `
        - check
            - /usr/libexec/qemu-kvm --version
            - but no kvm in command
- Debian
    - https://docs.docker.com/desktop/install/linux-install/
        - sudo modprobe kvm
        - sudo modprobe kvm\_intel
            - kvm\_amd
        - check
            - lsmod \| grep kvm
        - add user to kvm in order to access kvm device
            - ls -al /dev/kvm
            - sudo usermod -aG kvm $USER
                - check
                    - groups
    - Gnome
        - install
            - AppIndicator and KStatusNotifierItem
    - install using apt repo
        - [https://docs.docker.com/desktop/install/debian/](<https://docs.docker.com/desktop/install/debian/>)
        - install docker engine
            - [https://docs.docker.com/engine/install/debian/#install-using-the-repository](<https://docs.docker.com/engine/install/debian/>)
        - download deb package
        - ` sudo apt-get install ./docker-desktop-4.25.2-amd64.deb `
        - post-install script
            - automatic
    - launch docker desktop
        - icon://Applications/Programming/Docker Desktop
        - sign up for login
            - credentials management for linux user
                - [https://docs.docker.com/desktop/get-started/#credentials-management-for-linux-users](<https://docs.docker.com/desktop/get-started/>)
            - “pass” to store credentials in gpg2-encrypted files
            - initialize pass
                - gpg --generate-key
                    - [로그인 정보 삭제]
                    - [로그인 정보 삭제]
                    - rsa3072
                    - [로그인 정보 삭제]
                    - expired by 2025-12-03
                - [로그인 정보 삭제]
                    - password store initialized for pub
- check docker is running
    - docker command
        - ` which docker `
        - sudo docker info
    - systemctl
        - sudo systemctl is-active docker
        - sudo systemctl status docker
        - sudo service docker status
    - docker --version

### Whatitis

- docker
    - container-based open source virtual platform
- container
    - package with a project and its environment
    - if a container is downloaded, it is guaranteed that it runs in the save env
- why docker
    - packaging project and runs consistently
    - docker includes environment so it can run any env
    - each container is maintained separately
    - doesn’t need OS  diminish resources
    - benefit in managing a container
        - maintain several containers  Kubernates

### Running structure

- Docker daemon
    - api receiver, manage docker service
- docker client
    - docker user interact with docker
    - through docker command, communicate with docker daemon
- docker registry
    - save docker image
    - docker hub
        - common registry
    - private registry
    - usage
        - docker pull, run: get required images
        - docker push: save to registry
- docker object
    - docker image:
        - large size: files and params running in docker container
        - params does not change in any container
    - container:
        - status where an image executes  changing values are saved in container
            - image doesn’t change
        - a single image can produce several containers

### Component

- engine
    - execute container
- image
    - independent project which can be run in a container
    - image is invariant, once it is generated, it can’t be change
- container
    - execution instance for docker image
    - using one image, several containers can be made and run
    - container vs VM
- Dockerfile
    - build docker image
        - text file to make docker image
        - each command in Dockerfile  make layers in image
    - if Dockerfile changes, in docker build, only the changed layers are rebuild
- composer
    - like batch file of script, it can run several containers in a series
- volume
    - container has temporary life time.  if container finishes, all data in the container are deleted
- Docker

### remove

- [https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes](<https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes>)

### e.g.

- Node.js
    - sudo docker run -it node
        - try to find node.js in local  find it in docker hub
        - download node
        - open container with cli
            - \>
    - \> console.log(‘hello’)
        - hello
    - docker images&#9; in other terminal
        - node image is added
    - docker ps&#9; shows present working container
        - ….. created &#9;STATUS&#9;NAMES
        - modest
    - sudo docker exec -it modest bash
        - get into docker of modest and run shell with bash
    - ls
        - shows linux root
        - container has its own linux env
            - wherever this container runs in any OS, this container runs in the same env

## System Error (LCS)

### memory

- memory slot should follow the manual
- use memories from the same company
- memory can be checked by dmidecode

### hard disk error

- debian
    - whenever reboot, booting scan hard disk
        - it might have error in hard disk
        - copy or rsync
    - smartctl /dev/sdc&#9;&#9;etc
- centos
    - login to emergency mode
        - large amount of error message
            - ata4: .. status changed
            - comreset failed
            - err=-35
    - emergency mode
        - journalctl –x
            - failed command: Read DMA
            - status: DRDY ERR
            - error: abort
            - error in sdd
    - I/O error can be ascribed to hard disk error
- change hard disk

### graphical user login failure or automatic logout

- whatitis
    - after updating OS and GNOME
        - symptom
            - automatically logged out in a minute after logging in
            - GNOME is initialized
            - Other ID’s are OK
- difficult to follow X – route
    - bypass fixing X
- correction
    - if other ID’s are OK, check .bashrc
    - log-in collision with anaconda virtual environment
        - do not load anaconda module so activate virtual environment
        - after login you can use .bashrc for loading module
    - if modifying .bashrc fails,
        - ` make new home directory which will work correctly `

### make a new home (if required)

- in case .bashrc problem for anaconda activation
    - just correct .bashrc then logout-login again
- for login failure, generate new home directory without initial files
    - ` mv joonho joonho_err `
    - ` mkdir joonho `
        - nothing at home
    - ` sudo chown -R username:group directory `
        - -R changes all the sub-directory and files
        - ` sudo chown -R joonho:joonho joonho `
    - ` make initialize `
        - copy initial files made at adduser
            - ` cp /etc/skel/.bashrc . `
            - ` cp /etc/skel/.bash_logout . `
            - ` cp /etc/skel/.bash_profile . `
        - first login as graphic makes other files
            - .cash/ .config/ .local/ .viminfo .esd\_auth .ICEauthority .dbus
            - copy hidden file from original
                - .bashrc was some modified
                - from .c, .cache … copied
                    - an error occurred
                - from .f copied
    - ` mv ../joonho_err/* . `
        - will copy all except hidden files of .name
    - copy some initial files, not related to X
        - hiddenfiles are automatically generated
        - excluded files
            - .configure, .local
        - include files
            - .bashrc, .bash\_profile, .vim\*, .icon, .font, .vmware
- for automatic log-out, creating new ID
    - ` rsync avz –-delete /home/joonho/ /Data/Back_home/joonho `
    - log out & ^@F6
        - log in as root
        - ` cd /home `
        - userdel –r joonho
            - if there is a process for ID
                - kill -9 PID
        - adduser joonho
    - ` rsync avz --delete /Data/Back_home/joonho/ /home/joonho/ `

### reinstall after making a new home

- hangul
- gnome tweak
    - gnome shell extension
- sudo nvidia-settings

### UID, GID and permission

- when UID is changed
    - change sda and install new OS
    - delete id and make it again, the UID changed
- check
    - ls -l /home/joonho
    - id -u joonho&#9;&#9;# UID of joonho
    - id -g joonho&#9;&#9;# GID of joonho
    - ` grep joonho /etc/passwd `
    - ` grep joonho /etc/group `
- how to change UID and home directory permission
    - change UID
        - #usermod -u 1002 joonho
    - change GID
        - #groupmod -g 1002 joonho
    - all the files at home changes automatically into new UID (and GID ?)
    - manual change of file permission for files out of home or somewhere
        - #find / -group 1006 -exec chgrp -h joonho \{\} \\;
        - #find / -user 1006 -exec chown -h joonho \{\} \\;

### can’t mount NTFS in CentOS

- ls /dev
    - /dev/sdc is for whole disk c
    - /dev/sdc1 sdc2 sdc3 for each partition
    - windows 10 in sdc1
- mount sdc1 (ntfs)
    - centOS
        - mount is not working
            - unknown filesystem ‘ntfs’
        - ` yum install ntfs-3g `
    - common
        - su –
        - mount /dev/sdc1 /mnt/tmp
            - df&#9;&#9;! check mount
            - ` rsync for backup of window data `
        - umount /mnt/tmp
            - Or umount /dev/sdc1

### VM – notepad does not save Hangul

- encode Unicode not ansi

## superuser jobs

### backup for error

- disconnect /home from system
    - umount /home&#9;&#9;
    - umount /var
    - reboot
    - check /etc/fstab
- ` make a directory and format? `
    - ` mv joonho joonho_orig (where is it copied? ) `
    - ` mkdir joonho `
    - ` chown joonho joonho `
- format gdisk /dev/sdb
    - new partition
    - mkfs –t ext4 /dev/sdb1
    - format the new partition
- mount and install hard disk
    - mount /dev/sdb1 /home
    - fsck –a –f /dev/sdb1
    - ls -al /dev/disk/by-uuid/ \| tail -3 \| head -1 \| awk '\{print $9\}' \>\> /etc/fstab
    - modify /etc/fstab using /dev/disk/by-uuid
- backup in server
    - permitted hard: idft:/qcfs
        - scp idft:/qcfs/Joonho/backup&#9;# from qch or other machine

### personal backup hard

- basic
    - you can reach window
    - external hard will appear in /dev found by df
        - confirm directory for backup hard
- ` rsync –avz dir /run/media/joonho/Seagate\ Backup\ Plus\ Drive/Chi_Linux `
    - window directory name with blank can be written “\\ “
    - recursive copy
    - copy only updated file
- vmware window
    - df
        - sdc2 is sharewin
        - sdc1 is not shown, which is used for window
    - mount
        - mount /dev/sdc1 /mnt(/tmp)
            - if there was /mnt already, it is hidden
    - can reach window data
    - rsync
    - umount
        - umount /mnt
            - if you do not unmount and modify /mnt by mistake, it will make a problem
- scheduling
    - backup & cron&#9;#yagi815.tistory.com/172

### file system scan: fsck/e2fsck

- boot in linux single user mode
- command mount without argument
    - for checking devices
- umount the checking partition
- mount
- let system recognize device such as disk, cdrom
- umount
- umount /dev/sdb1 /backup
- fsck –y /dev/sdb1
- as for recover, yes
- touch /forcefsck
- 30 mount or 6 months, scan.
- when rebooting, scan

### Switch Linux OS

- Only sda are changed
    - no interaction with sdb, sdc
    - all the data in sdb, sdc will conserved
    - all the setup files will be stored in /home (sdb)
- Partition can be changed or conserved
    - Sda1 for /boot
    - Sda2 for /
    - Sda3 for swap
    - Remainings are logical partition
        - It can be reached by sda5
- All the programs will be installed again
    - But setup would be saved in /home (sdb)

### Add new hard

- Briefs
    - check hdd installation
        - /dev/sd\[a-d\] is shown if it is conceived by system
        - not assigned uuid: ls -al /dev/disk/by-uuid
    - check all storages: sudo fdisk -l
        - confirm disk info
    - ` make partition `
        - sudo gdisk /dev/sd\[a-d\]
        - /dev/sd\[a-d\]1, …2, etc are shown
    - format a partition
        - mkfs -t ext4 /dev/sdb1
        - ls -al /dev/disk/by-uuid
            - displays the formatted hdd
    - register in fstab and sudo “mount -a”
        - ` make vim to use copy and paste `
- overall
    - outline
        - prepare and mount it by UUID
    - strategy
        - is it used only by Debian?
        - or need to be accessed by windows?
        - how many partitions?
            - each entry need to be included in /etc/fstab, not just the drive
    - FS for OS
        - ext3/ext4 for only linux
        - for sharing with window, FAT32 is recommended although NTFS works well also.
- confirm hardware installation
    - /dev
        - check a new disk is conceived by system
        - /dev/sdd  --new disk without partition
    - confirm hdd info
        - sudo fdisk –l
        - Disk /dev/sdd: 1.8 TiB, …
        - with no Device for partition “Device Start End Sectors…”
    - partition disk
        - gdisk /dev/sdd
    - format /dev/sdd1, sdd2, etc
        - mkfs –t ext4 /dev/sdd1, etc
- ` mkdir in / and mount `
    - create a new directory where the disk will be mounted
    - blkid
    - write uuid of new partition in /etc/fstab
    - mount -a

### Error in keyboard and mouse

- Mouse & keyboard is not working
    - still OS is running
- prescription
    - login from other computer
        - in top, turn off firefox
    - method 1
        - force to logout
        - cancel then it works
    - method 2
        - in terminal
            - su –
            - systemctl restart gdm

### users & su

- check users
    - getent
        - display all uid
        - getent passwd uid
            - check uid’s id number, home directory, shell
        - getent passwd \| grep ‘/home’ \| cut -d: -f1
- su -
    - change to superuser: su passwd is required
    - can do user job
        - su - userid&#9;&#9; do not ask user passwd
            - can login without user passwd
            - whoami
                - userid
            - modify files as user not su

### manage directory

- can write under root-directory
    - ls -l /home&#9;&#9;: root/root
    - ls -l /home/joonho&#9;: Joonho/Joonho
        - Joonho can write in /home/joonho
- ` make a new directory for user under root-directory `
    - ls -l /NAS1 &#9;&#9;&#9;: root/root
    - ` sudo mkdir /NAS1/Shared		: root/root `
    - ` chown [-R] joonho:joonho /NAS1/Shared	: joonho/joonho `
        - can write to /NAS1/Shared

## Basic package

### pip

- package management system to install software packages written in python
    - PIP: Pip Installs Python package
    - ` sudo apt install python-pip `
        - to downgrade pip
            - remove and reinstall
            - ` sudo apt remove python-pip `
- usage
    - ` pip install packagename `
        - method 1
            - ` apt-get install python-pip `
            - ` pip install –upgrade pip `
                - for latest version
                - ls –s /usr/local/bin/pip /usr/bin/pip
        - method 2
            - ` curl https://bootstrap.pypa.io/get-pip.py | python `
        - method 3
            - install Setuptools including easy\_install
                - ` wget https://pypi.python.org/packages/source/s/setuptools/setuptools-0.6c11.tar.g `
                - ` tar xvfz setuptools-0.6c11.tar.gz `
                - pushd setuptools-0.6c11
                    - sudo python setup.py install
                - popd
                - sudo rm -rf setuptools-0.6c11\*
            - sudo easy\_install pip
        - e.g.
            - ` pip install package `
                - installed in /usr/local/lib/python2.7/dist-packages
                    - cf. /usr/lib/python2.7/dist-packages using apt-get
            - ` pip install package –user `
                - will install under $HOME/.local/lib
            - ` sudo pip install package –user `
                - will install package under /root/.local/lib
            - ` pip install –editable . `
    - depending on pip version
        - pip$\{version\} install package
        - pip3, pip3.4
- subcommand
    - update/upgrade
        - ` pip install --update/upgrade pakcagename `
        - ` pip install pip --upgrade `
        - ` pip install -–update pip `
            - when it makes SSL security error
        - ` pip install –trusted-host pypi.org –trusted-host files.pythonhosted.org –upgrade pip `
    - uninstall
        - ` pip uninstall package `
        - ` sudo pip uninstall package `
            - remove python package installed under /root
    - show installed package list
        - ` pip list `
    - version check
        - ` pip show packagename `
- error
    - command python setup.py egg\_info failed with error code 1
- setuptools
    - sudo -H pip3 install --upgrade --ignore-installed pip setuptools

### chrome

- Pro/Con
    - firefox
        - charges large memory
    - google-chrome
        - collision with Hangul depending on input method (IM)
            - ibus: Backspace and Enter keys are not working
                - change into Eng mode and use Backspace and Enter keys
            - ifczi: Cannot write Hangul in chrome
- install
    - download
        - ` wget https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm `
    - centos
        - install
            - ` yum install google-chrome-stable_current_x86_64.rpm `
        - error in XZ
            - [https://blog.csdn.net/ningyanggege/article/details/105823447](<https://blog.csdn.net/ningyanggege/article/details/105823447>)
            - modify .bash\_profile
            - ` export LD_LIBRARY_PATH=/lib64/:$LD_LIBRARY_PATH `
            - ` source .bash_profile `
    - debian
        - download at website
            - [https://www.google.com/chrome/?platform=linux](<https://www.google.com/chrome/?platform=linux>)
        - root
            - dpkg -x google-chrome-stable\_current\_amd64.deb
            - ` apt install ./google-chrome-stable_current_amd64.deb `
        - home
            - dpkg -x google-chrome-stable\_current\_amd64.deb ../.local/share/chrome
        - $google-chrome
- Usage
    - save current bookmark
- chromium and google-chrome are different

### my package - python

- search package
    - want to install expect module of python
    - ` aptitude search expect `
        - python-pexpect …
- install
    - ` sudo apt-get install python-pexpect `
- made my own python package called setup.py
    - sudo python setup.py install

### babel

- /sur/bin/babel
    - babel –version : 2.3.2
- (debian jessi)
    - download: [http://openbabel.org/wiki/Category:Installation](<http://openbabel.org/wiki/Category:Installation>)
    - install
        - dpkg –I file
    - run
        - ` which obabel `

### boost

- version check
    - rpm –qa \| grep boost
        - 1.53

### cmake

- whatitis?
    - cross platform makefile
    - higher version is required for boost
    - home installation is possible
- system install
    - ` yum installs only 2.7 `
    - already have cmake 2.7
        - ` yum remove cmake, cmake-data `
    - download binary
    - configure, make, make install
    - install site: /usr/local/share/cmake-3.11
        - ` cp $Home/bin/* /usr/local/bin `
        - ` cp $Home/bin/* /usr/bin		! necessary ? `
- home install
    - method1
        - configure
        - gmake
        - use $Home/bin/cmake
        - e.g.
            - ` cd Avodagdor1 `
            - ` mkdir build; cd build `
            - ../../cmake-2.8.11/bin/cmake ../
- run cmake
    - ` cmake dir[CMakeList.txt | source] options `
        - src\_dir should locate CMakeLists.txt
    - Directory structure
        - Package\_Home/src,\[CMakeLists.txt\],
            - ` make build	! make build directory and work there `
            - ` cd build `
            - if no CMakeLists.txt in Package\_Home
                - ` cmake ../src options `
                    - ../src/CMakeLists.txt should exist
            - if CMakeLists.txt exist in Package\_Home
                - ` cmake .. options `
    - overall process
        - serial
            - ` cmake –DCMAKE_INSTALL_PREFIX=/… ../ `
            - make
            - ` make install `
        - parallel
            - ` cmake .. –DCMAKE_C_COMPILER=mpicc -DCMAKE_CXX_COMPILER=mpiCC –DCMAKE_Fortran_COMPILER=mpifort –DCMAKE_INSTALL_PREFIX=/… `
                - mpiCC → mpicxx
- more detail
    - in build directory
        - ` cmake source_directory `
            - ` cmake ../source_directory/CMakeLists.txt `
            - read CMakeLists.txt
                - all the subdirectory has its own CMakeLists.txt
            - makes Makefile, CMakeCache.txt, cmake\_install.cmake, \[CMakeFiles\]
            - only once executed then use Makefile
        - use Makefile to build
            - make
                - first check CMakeLists.txt is changed
                    - if changed, regenerate Makefile then build
                - /CMakeFiles
                    - sub makefiles for each target
    - ` cmake option `
        - command line
            - ` cmake ../ –D<VARIABLE1>=var1 –D<VAR2>=var2 –D…. `
        - install directory
            - CMAKE\_INSTALL\_PREFIX
                - –DCMAKE\_INSTALL\_PREFIX=$QC\_EXT\_LIBS/openblas.cmake
        - C complier – cc, gcc, mpicc
            - CMAKE\_C\_COMPILER
                - –DCMAKE\_C\_COMPILER=mpicc
        - c++ compiler – c++, g++, mpiCC
            - CMAKE\_CXX\_COMPILER
                - -DCMAKE\_CXX\_COMPILER=mpiCC
            - CMAKE\_CXX\_FLAGS
                - -DCMAKE\_CXX\_FLAGS=”-DFINTP -03 -DNDEBUG”
        - Fortran compiler – gfortran, mpifort
            - CMAKE\_Fortran\_COMPILER
            - –DCMAKE\_Fortran\_COMPILER=mpifort
        - library
            - intel mkl
                - MKL\_INCLUDE\_DIR
                - -DMKL\_INCLUDE\_DIR=$MKLROOT/library
        - GMX options
            - ` GMX_DOUBLE=ON `
            - ` GMX_GPU=OFF `
            - ` GMX_MPI=ON `
            - ` GMX_THREAD=OFF `
            - ` GMX_FFT_LIBRARY=mkl `
- CMakeLists.txt
    - ` cmake works on CMakeLists.txt `
        - all the subdirectories have their own CMakeLists.txt
        - doesnot describe object files, head files
        - analyze dependency automatically
        - ADD\_EXECUTABLE(output binary, sources)
    - top-level CMakeLists.txt
        - bring all the modules into scope
        - adding the subdirectories for all Cmake projects
        - finding external libraries
    - syntax
        - import external libraries
            - add\_library(boost INTERFACE IMPORTED)
        - SET(\<var name\> \<value\>)
            - SET(list\_name val1 val2)
        - dereference
            - $var\_name
            - $\{var\_name\}
        - e.g.1
            - SET(SRC\_FILES main.c foo.c bar.c)
            - ADD\_EXECUTABLE(app.out $\{SRC\_FILES\})
        - command
            - cmake\_minimum\_required(VERSION number)
            - project(project\_name)
            - cmake\_project\_name&#9;! var for project()
            - message($\{CMAKE\_PROJECT\_NAME\})&#9;! write to console
            - cmake-build\_type
                - Debug, Release
            - CMAKE\_INSTALL\_PREFIX&#9;&#9;! install directory
                - SET(CMAKE\_INSTALL\_PREFIX /home/joonho/sciware)
            - cmake\_c\_compiler &#9;&#9;! path to compiler
- build directory
    - output of cmake
        - Makefile, CMakeCache.txt, cmake\_install.cmake, \[CMakeFiles\]
    - each directories has its own Makefile, cmake\_install.cmake
    - CMakeCache.txt is unique
- Makefile vs CmakeLists.txt
    - case 1
        - main.c foo.c bar.c -\> app.out
    - Makefile
        - ` OBJS=main.o foo.o bar.o `
        - ` TARGET=app.out `
        - all:$(TARGET)
        - clean:
            - rm –f \*.o
            - rm –f $(TARGET)
        - $(TARGET): $(OBJS)
            - $(CC) –o $@ $(OBJS)
        - main.o: foo.h bar.h main.c
        - foo.o: foo.h foo.c
        - bar.o: bar.h bar.c
    - cmake
        - CMakeLists.txt
            - ADD\_EXECUTABLE(app.out main.c foo.c bar.c)
        - ` cmake CMakeLists.txt `
            - makes makefile
        - make

### openbabel

### qt

- whatisit
    - cross flatform to develop graphic interface
- version check
    - qmake --version
    - qmake-qt5 --version
        - qmake6 --version
    - qtdiag
- version dependence
    - Avogadro
        - for Avogadro v. 1
            - qt-version = 4
        - for Avogadro v. 2 (v 1.9)
            - qt-version = 5
- setting
    - env
        - ` QTDIR=/usr/lib64 `
            - qt-3.3, qt4, qt5
        - no path for qmake
    - install qmake
        - ` yum install qt-devel `
        - qt4/bin/qmake, qt5/bin/qmake
- how to switch in installation
    - change default
- Qt in python
    - import inspect
    - import PyQt5 import Qt
    - vers = \['%s = %s' % (k,v) for k,v in vars(Qt).items() if k.lower().find('version') \>= 0 and not inspect.isbuiltin(v)\]
    - print('\\n'.join(sorted(vers)))

### Intel

- register
    - [로그인 정보 삭제]
        - different email goes into different status of user
- installation
    - [로그인 정보 삭제]
        - needed in the installation procedure
    - installation w. full package of “Intel R Parallel Studio XE 2019 Custer Edition for Linux”
        - about 30G is required for full package
        - includes
            - C++ and Fortran Compiler
            - Distribution for python, intelpython3
            - GNU Project Debugger
            - software lib(MKL, DAAL, TBB, IPP)
            - Advisor, Inspector, VTune, MPI lib,
    - some prerequisite for i386
- setting after installation
    - initialize tools
        - ` source $intel_home/parallel_studio_xe_2019.update.package_num/bin/psxevars.sh `
            - in module file
                - add “psxevars.sh intel64”
        - all the path, env’s are set such as
            - MKLROOT
    - lib home
        - which
            - icc, mpicc
        - $intel\_home/compilers\_and\_libraries\_2019.3.199/linux
            - /bin/intel64/icc, ifort
            - /mkl/bin/mklvars.sh&#9;! no need to run
            - /mpi/intel64/bin/mpicc, mpicxx, mpifort, mpirun, mpivars.sh

### fftw

- fftw2
    - qchem
- fftw3
    - gromacs
- install
    - configure&#9;&#9;&#9;&#9;&#9;
        - gcc - serial&#9;&#9;cf install-qchem
            - ` ./configure CC=gcc F77=gfortran --prefix=/path/to/qcextlibs/fftw `
        - gcc - parallel
            - ` ./configure CC=gcc CXX=g++ F77=gfortran FC=gfortran --prefix=/path/to/qcextlibs/fftw --enable-mpi `
        - intel - serial (2019)
            - ` ./configure CC=icc CXX=icpc F77=ifort FC=ifort --prefix=/path/to/qcextlibs/fftw `
        - intel - parallel
            - ` ./configure CC=icc CXX=icpc F77=ifort FC=ifort --prefix=/path/to/qcextlibs/fftw --enable-mpi `
                - --enable-mpi is not working for fftw3
        - gromacs options
    - make
    - ` make install `

## common packages (LCS)

### installation method

- download
    - download .rpm in download page
    - wget
- install
    - ` sudo yum localinstall ./slack*.rpm `
- updating
    - cat /etc/yum.repos.d/slack.repo
        - or make the repo

### evince: pdf reader

- built-in package
- No need acroread
    - FoxitReader was replaced by acroread
    - install
        - download
            - ` wget http://cdn01.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.1/en_us/FoxitReader1.10.0225_Server_x64_enu_Setup.run.tar.gz `
        - gzip –d “….run.tar.gz’
            - uncompress
        - ` tar xvf ‘….tar’ `
        - installation
            - user
                - ./’……run’
            - systemwide
                - sudo ./….run
                    - /opt/foxitsoftware/foxitreader
    - uninstall
        - ` cd /opt/FoxitReader/../ `
            - sudo ./maintenance.sh
                - uninstall
    - error
        - anaconda3 collide with FoxitReader
            - /opt/foxitsoftware/foxitreader/FoxitReader: /opt/foxitsoftware/foxitreader/lib/libstdc++.so.6: version \`CXXABI\_1.3.8' not found (required by /home/joonho/anaconda3/lib/./libicui18n.so.58)
            - uninstall foxitreader and reinstall as anaconda is loaded

### Application Installer: libreoffice

- Application/System tools/Application Installer
    - libreoffice
        - download all the components respectively
            - calc, express, base, etc
    - open
        - libreoffice a.odt
            - if it abnormally finished, use app in menu

### snap (Donot install)

- whatisit
    - like a container
    - firefox is installed through snap only from version 22.04
- do not use this for standard package such as code
    - it raises error in remote login
    - stop & remove
        - sudo systemctl disable snapd.service
        - sudo systemctl disable snapd.socket
        - sudo systemctl disable snapd.seeded.service
        - sudo snap list
        - sudo snap remove snap-store (also firefox)
        - ` sudo apt autoremove –purge snapd `
- package format developed by Canonical
    - does not come in with bullseye package
    - ` sudo apt update `
    - ` sudo apt install snapd `
    - sudo systemctl status snapd
        - though it is run automatically, if not,
            - sudo systemctl start snapd

### adobe reader

- following installation method
- (bullseye: debian 11)
- http://armandocaussade.org/computing/install\_adobe\_reader.txt
    - ` $ wget ftp://ftp.adobe.com/pub/adobe/reader/unix/9.x/9.5.5/enu/AdbeRdr9.5.5-1_i386linux_enu.de `
    - md5sum AdbeRdr9.5.5-1\_i386linux\_enu.deb

### firefox  chrome

- use chrome
    - firefox takes large memory
- Mozilla
    - bookmark
        - log in firefox (different from gmail)
            - bookmark is synced
    - font setting
        - Add-ons/Zoom page WE
            - preference
                - Zoom Levels & Font Size/Default Full Level (%): All: 120
                    - save
        - use Zoom page WE icon on menu bar for temporary font size
    - Mozilla flash plugin?
        - setting for flash movie
            - symptoms
                - lock is orange
                - connection is not secured
            - unblock shockwave flash
                - menu/Add-ons/Plugins
                    - Shockwave Flash/Preferences
                        - uncheck: Block dangerous and intrusive Flash contents
        - Install w. su
            - ` apt-get install flashplugin-nonfree `
        - uninstall
            - update-flashplugin-nonfree –uninstall
            - ` apt-get remove flashplugin-nonfree `
    - restore the previous session
        - menu/”restore previous session” is activated
    - bookmark the present tab
        - put mouse on tab
            - click right button
            - Select all Tabs
                - it presents blue line on all Tabs
            - to deselect
                - click any tab
        - put mouse on tab
            - click right button
            - Bookmark Tabs…//New Bookmakrs
                - input (folder) Name
                - select Folder to put folder name
                    - if there is the same folder name already
                        - remove the folder in advance
    - Firefox error
        - some movies are not playing
            - setting shockwave flash
    - if child popup is not open in “javascript:void(0)”
        - Ctrl+F5 or “^Shift+R”
            - fixed
- apach
    - file upload is not updated
        - remove cache
            - menu::/History/Clear Recent History..
                - Time range: Everything
                - Details: Cache only check
- bookmark
    - reopen the latest closed tabs
        - cnrl+shift n

### Image Viewers

- the same as eog
    - whatitis
        - gnome package == Eye of GNOME (eog)
        - GNOME system application
            - shown as “Image Viewer” in Applications/Utilities
            - eog&#9;# in command line
    - properties
        - view single images or images in a collection
        - fullscreen slideshow mode
        - set an image as the desktop wallpaper
    - details
        - system integration
    - error
        - Image Viewer is working while eog command makes error
            - symbol lookup error: /lib64/libgtk-3.so.0: undefined symbol: g\_log\_structured\_standard
    - turn off anaconda
- showimage
    - /usr/bin/showimage
        - it displays almost the same plot with display in ImageMagick
    - where does it come from?
- ImageMagick/convert/animate
    - ` yum install ImageMagick `
        - command
            - convert –io inputf –oo outf
    - display
        - display -version
        - display imagefile
    - animate
        - run git animation file
        - animate animation.gif
        - animate -resize 1920\*1080 animation.gif

### movies

- whatitis
    - capture only
        - obs-studio
            - best quality, control
    - run movie
        - vlc
            - ` sudo apt install vlc `
            - vlc movie.mp4
        - mpv
        - gnome videos (aka totem)
    - kinds
        - simplescreenrecoder
            - ease of use, good performance
        - kazam
        - ffmpeg
        - for wayland
            - wf-recorder for sway/wlroots
            - gnome-screenshot + gnome-screen-recoder (basic)
- format
    - mp4
    - mov
    - avi
- obs-studio
    - open broadcaster software
    - install
        - deb
            - ` apt install obs-studio `
            - ` $ obs `
    - first-time setup
        - Auto-configuration wizard
            - optimize for recording only or streaming
            - set resolution and frame rate
            - can this later
    - quick step to start recording
        - Set up your scene
            - go to source (bottom panel)
                - default will start Scene,
            - if not, click + under Scene/, choose Screen Capture (XSHM) or window capture
                - to create new scene
        - Add a window capture source
            - Under sources, click + and choose
                - Linux: Windows Capture (Xcomposite)
                    - give it a name
                - add select display to record
        - Choose the window to capture
            - In the new window, click “Window” dropdown to select panel for recording
            - click OK
        - Resize & arrange
            - In the preview, click and drag the window to fit the canvas
            - scale, crop (Alt+drag), move
        - Start recording
            - start recording (bottom right)
            - stop recording
        - save
            - default
                - ~/Videos as .mkv or .mp4
        - find file
    - setting
        - a custom resolution
            - file format .mp
            - audio off
        - recording directory
        - file format: Settings \> Output \> Recording format
        - Hotkeys: Settings \> Hotkeys to start/stop recording easily
    - merge two mp file  ffmpeg
    - caption
        - Sources/+//ab Text
            - title: no meaning
            - input text in text box
            - choose font, color etc
            - move text box in the preview
    - problem
        - extra padding or empty frame space is captured
            - remove the black space
            - crop the video with Ffmpeg
        - two movie has different size, so when I merge both and crob, the second file is crobbing more  use the same red box
- ffmpeg
    - ` sudo apt install ffmpeg `
    - concatenate MP4 files
        - this works only for if the videos use the same codec, resolution, framerate
            - ` make a text file listing the videos `
                - ` vi files.txt `
                    - file ‘in1.mp4’
                    - file ‘in2.mp4’
                - ffmpeg -f concat -safe 0 -i files.txt -c copy output.mp4
        - if files have different format
            - ffmpeg -i input1.mp4 -i input2.mp4 -filter\_complex "\[0:v:0\]\[0:a:0\]\[1:v:0\]\[1:a:0\]concat=n=2:v=1:a=1\[outv\]\[outa\]" -map "\[outv\]" -map "\[outa\]" output.mp4
- simplescreenrecorder
    - install
        - Debian
            - Sudo apt-get install simplescreenrecorder
        - centos
            - ` yum install simplescreenrecorder `
                - from epel
    - Following the below
        - general
            - might use default and confer tooltips with mouse on icon
    - turn on
        - Application/Sound & Video/simplescreenrecoder
            - or $simples+Tab
    - Continue
    - check
        - Video input
            - Record a fixed rectangle
                - ` make a rectangle with dragging the mouse `
                    - sometimes it appears later
                    - click Select rectangle…
                - select window…
                    - then click the window
        - Audio input
            - check box, if you need to record audio
    - continue
    - check
        - File for filename
            - check filename and directory by Browser
            - Container for file format
                - use MP4 for PPT file upload
                - Other… shows all the other format such as
                    - avi, ffm, gif, almost all the video format
        - can check Video Codec
            - so many choices
            - default: H.264
                - without this, it makes error in recording
    - continue
    - click Start recording
        - just after start movie - click at the same time
    - click Save recording
        - the file will be in the directory
    - otherwise Cancel recording
        - will stop the present recording

### Remote access

- apps
    - NoMachine, Google Remote Desktop, teamviewer
- Remote desktop vs remote login
    - Remote shell/terminal access
        - ssh, PuTTy, MobaXter, etc  connect to text console/shell
    - Remote graphical desktop access
        - X11 forwarding, VNC, RDP, NoMachine, Chrome Remote Desktop, Teamvieer
- SSH-based remote login (text terminal)
    - ` ssh command `
    - PuTTy, MobaXterm, Termius
    - pro
        - simple, fast, secure, easily work through filewalls (port 22)
    - cons
        - no GUI
- Remote graphical Desktop
    - traditional: X11/VNC/RDP protocals
    - modern: Encapsulated or tunneled remote desktop
- Traditional Desktop Access
    - protocols
        - X11 forwarding&#9;SSH port 22
        - VNC&#9;&#9;port 5900+
        - RDP&#9;&#9;port 3389
    - behavior
        - starts a new session (GDM launches new X session)
    - Tunneling possible
        - forward these through SSH
            - ` ssh -L 5901:localhost:5901 user@server `
            - vncviewer localhost:5901
- Modern Tunneling Remote Desktop Clients
    - Tool
        - NoMachine
        - Chrome Remote Desktop
        - TeamViewer/AnyDesk
    - Session type (New vs. Existing)
        - New (virtual desktop)
        - Existing (shared desktop)
        - Headless session
- Firewalls and VPNs
- NoMachine
    - sessions
        - cf. loginctl
    - connecting existing session not new one
        - ` vi /usr/NX/etc/server.cfg `
            - PhysicalDesktopAuthorization 1
            - CreateDisplay 0
            - EnableLoginPhysicalDesktop 1
            - (old)
            - PhysicalDesktopSharing 1
            - EnableSessionCreate 0
            - EnableSessionShadow 1
    - through firewall
        - Console sharing
            - NoMachine
                - Server check
                    - Systemctl status nxserver
        - Session-based: new session
            - VNC
        - AnyDesk
        - RustDesk
- Teamviewers
    - https://www.teamviewer.com/en-us/download/linux/
        - both versions of standard and Host
        - guest version
        - host version - role down the page
            - during installation  accept EULA (user contract) & DAE (data agreement)
    - two version
        - general version
            - cons: whenever turns on
                - there is no passwd
                - (old) passwd is changed
        - Host version
            - pros: the permanent passwd
            - cons: can not be a guest to other host
    - install
        - (deb) sudo apt install ./teamviewer\_amd64.deb
        - Host version
            - 1<sup>st</sup> uninstall if a teamviewer is installed and/or running
            - sudo dpkg -i teamviewer-host\_15.15.5\_amd64.deb
                - or
            - ` sudo apt install ./team……deb `
        - setting
            - login w. teamviewer ID then can be accessed by guest
                - in guest (laptop), host is changed into online from offline
                - Options/General/Account assignment
                    - [로그인 정보 삭제]
                    - passwd for teamviewer
            - easy access from remote guest without asking passwd
                - Options/Security/Grant ID(Joonho Park) Easy Access
                    - check box
            - (old) Options \> Security \> Personal password \> Password \> Change password
                - uncheck the gracious connect to put in passwd
    - uninstall
        - stop daemon if running
            - systemctl status teamviewerd
            - sudo systemctl stop teamviewerd
        - remove data
            - sudo rm -rf /opt/teamviewer
            - sudo rm -rf /etc/teamviewer
            - sudo rm -rf ~/.config/teamviewer
            - sudo rm -rf /var/lib/teamviewer
            - sudo rm -rf /run/teamviewer\*
        - uninstall package
            - ` sudo apt remove --purge teamviewer -y `
    - miscellaneous
        - sudo teamviewer info
            - should show teamviewer ID
    - Errors
        - missing host device in guest teamviewer and in creating, it says it exists already.
            - find it under “offline”
        - sudo teamviewer info
            - does not show teamviewer ID
            - check it is proper package for guest or host version
        - in login (debian)
            - Wayland: incoming remote control will fail
            - Xorg sessions are only supported
                - When login, use Xorg session
        - is it network error?
            - in guest
                - can’t find partner
                - partner is not connected to router
            - solved
                - ` apt-get update `
                - ` apt-get upgrade `
                    - then, fixed up
    - etc
        - it is daemon
            - ps aux \| grep teamviewer
                - .. teamviewerd -d
            - task id is continuously changed so
                - cannot be removed by kill or pkill
            - dpkg -r is not working
        - dpkg -l \| grep teamviewer
            - confirm the package name
        - uninstall
            - ` apt-get remove teamv*	wild card way `
            - ` apt-get purge teamviewer	another way `
        - install again
    - setting for running in boot
        - systemctl status teamviewerd
            - active  does not guarantee the connection
        - setting for autostart
            - ` vi /etc/gdm3/daemon.conf `
                - AutomaticLoginEnable=true
                - AutomaticLogin=joonho
                - WaylandEnable=false
            - autostart setting
                - ` cp /usr/share/applications/teamviewer.desktop ~/.config/autostart/ `
        - structure
            - daemon: authorentification, stay for connection
            - But there should be active X session
                - GUI need to start completely
    - $teamviewer
        - teamviewer -h
    - (centos) install host version
        - rpm shows lack of dependency
        - ` sudo yum install teamviewer-host…rpm `
        - problem
            - small window does not show id and passwd
            - open
                - click or bar-icon-mouse right button \> status dialog
            - id
                - status dialog: using tab, copy and display somewhere

### Avogadro 1.0

- cf go to Avogadro 2.0
- download
- INSTALL
    - debian
        - ` sudo apt-get install Avogadro `
        - installed at
            - /usr/bin/avogadro
    - centos
        - install method
            - ` mkdir build `
            - ` cmake ../ `
                - version
                    - ` cmake 2.8.9 later 2.8.11 `
                    - Qt 4.6.0 later 4.8.5
                    - OpenBabel 2.3.x later devel version
                        - ` yum install openbabel `
                    - Eigen 2.0 later 3.x supported
            - ` make –j2 `
            - ` sudo make install `
        - experienced error
            - ` cmake 3.6 error `
            - ` cmake 3.11 warning but installed `
            - ` cmake 2.8 `
- manual
    - go to [visual\_program](<file:///C:\Users\jhPark\AppData\Roaming\Microsoft\Word\visual_program.docx>)
- Avogadro 2.0  openchemistry

### MS teams, slack

- MS teams
    - install
        - several different methods
        - download .deb
            - sudo dpkg -i \*\*teams-package-file-name\*\*
            - ` which teams `
                - /usr/bin/teams
            - also appears in App/Internet/Microsoft Teams - Preview
        - from repo
            - ` curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add - `
            - sudo sh -c 'echo "deb \[arch=amd64\] https://packages.microsoft.com/repos/ms-teams stable main" \> /etc/apt/sources.list.d/teams.list'
            - ` sudo apt update `
            - ` sudo apt install teams `
    - performance
        - 2021: error in headset recognition
            - system sluggishness appears
        - 2020:
            - no problem in headset: speaker and mic
            - system sluggishness?
                - still good
    - maintenance
        - setting
            - uncheck: teams running when it turns off
    - remove
        - ` sudo apt-get remove teams `
    - install (deprecated)
        - https://login.microsoftonline.com/common/oauth2/deviceauth
        - install powershell
        - pwsh
            - prompt\> PS /home/joonho\>
            - install-module microsoftteams
            - import-module microsoftteams
            - connect
                - Connect-MicrosoftTeams -AccountId USERUPN
                    - show code to authenticate
                    - open [https://login.microsoftonline.com/common/oauth2/deviceauth](<https://login.microsoftonline.com/common/oauth2/deviceauth>)
                        - input key for authorization
                - once authorized, we can manage MS teams and run cmdlets
                    - how?
    - takes memory
        - remove startup in tweaks
            - remove automatic startup
- slack
    - download
        - web page
            - [https://slack.com/intl/en-kr/downloads/linux](<https://slack.com/intl/en-kr/downloads/linux>)
            - download .rpm
    - install
        - ` sudo yum localinstall ./slack-*.rmp `
        - installed in
            - Application/Internet/Slack
    - how to activate slack pane
        - $slack or click Slack icon
        - login
            - go to webpage
            - login in webpage
            - click workspace
            - go back to Slack pane
    - ` make repo for update `
        - cat /etc/yum/repos.d/slack.repo
            - \[slack\]
            - name=slack
            - baseurl=https://packagecloud.io/slacktechnologies/slack/fedora/21/x86\_64
            - enabled=1
            - gpgcheck=0
            - gpgkey=https://packagecloud.io/gpg.key
            - sslverify=1
            - sslcacert=/etc/pki/tls/certs/ca-bundle.crt
    - usage
        - ` make work group `
        - invite person
        - talk to all
        - talk to a person

### html

- [moved to DB](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\DB_Java_Cpp_html.docx>)
- how to run open html
    - $google-chrome a.html
    - browser command
        - google-chrome, firefox, etc

### grace (xmgrace)

- Debian&#9;&#9;&#9;&#9;&#9;cf. [manual](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\visual_program.docx>)
    - ` aptitude install grace `
        - xmgrace is automatically installed
    - xmgrace – gui
- CentOS
    - ` sudo yum install grace `
        - xmgrace is automatically installed
- KISTI: install at home
    - tested by KISTI
        - 5.1.25
    - download
        - [https://plasma-gate.weizmann.ac.il/Grace/](<https://plasma-gate.weizmann.ac.il/Grace/>)
    - install
        - ` module purge `
        - ` module load gcc/7.2.0 craype-mic-knl netcdf/4.6.1 `
        - ` tar -xzvf grace-5.1.25.tar.gz `
        - ` cd grace-5.1.25 `
        - ` ./configure --prefix={설치 경로} --with-extra-incpath=/apps/common/motif/2.3.8/include:/apps/common/jpeg/9c/include:/apps/common/libpng/1.2.56/include:$KISTI_APPLIB1/$CRAY_CPU_TARGET/netcdf/4.6.1/include --with-extra-ldpath=/apps/common/motif/2.3.8/lib:/apps/common/jpeg/9c/lib:/apps/common/libpng/1.2.56/lib:$KISTI_APPLIB1/$CRAY_CPU_TARGET/netcdf/4.6.1/lib `
            - log
                - gcc -O2  -fno-common -Wall -Wpointer-arith -Wnested-externs -I/apps/common/motif/2.3.8/include -I/apps/common/jpeg/9c/include -I/apps/common/libpng/1.2.56/include -I/apps/compiler/gcc/7.2.0/applib1/mic-knl/netcdf/4.6.1/include -o convcal convcal.c -ldl -lm
        - ` make && make install `

### Latex

- latex to pdf converter
    - latexmk
        - ` sudo apt-get update `
        - ` sudo apt-get install latexmk `
    - error
        - cmap.sty not found
        - fix up
            - to install cmap, it requires xzdec
- latex to html
    - ` make html `
    - web browser
        - [file:///Storage/Shared/WCommon/Docs\_res/book/statistical\_mechanics/statmech/build/html/introduction.html](<file:///C:\Storage\Shared\WCommon\Docs_res\book\statistical_mechanics\statmech\build\html\introduction.html>)

### VSCode

- Visual Studio code
- install
    - deb
        - download …deb
        - ` sudo apt install ./…deb `
            - automatically install the apt repo and signing key to enable auto-updating
        - ` sudo apt install apt-transport-https `
        - ` sudo apt update `
        - ` sudo apt install code `
    - run
        - $code
- Usage
    - go to [python reference](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\python3_matlab.docx>)

## CP-conda

### (ana)conda & virtual env

- contents
    - virtual env
    - whatis conda?
    - ` conda installation `
    - ` conda submodule `
    - python packages: ASE, AMP, TF
    - jupyter notebook
    - jupyterlab
- virtual environment in python&#9;&#9;&#9;&#9;cf contents
    - purpose
        - using different python version
        - using different branch of the same package/module
            - tf1, tf2
            - amp, amp w. G2offset
    - modules
        - venv
        - virtualenv
        - conda\_intro
        - pyenv
    - venv
    - virtualenv
        - install virtualenv
            - v2.7
                - ` pip install virtualenv `
            - v3.5
                - ` pip3 install virtualenv `
        - virtualenv vname
            - base prefix ‘/home/joonho/anaconda3’
            - new python executable /home/joonho/venv/bin/python
            - installing setup tools, pip, wheel, …
        - ` source vname/bin/activate `
            - (vname) prompt
        - deactivate
            - exit virtualenv
    - conda

### whatis conda&#9;&#9;&#9;&#9;&#9;&#9;&#9;cf. contents

- general
    - anaconda: tuned car
    - independent and stand-alone python virtual env
        - depending on python version: anaconda2 or anaconda3
    - don’t need to install
    - initialization
        - eval $(‘/$USER/anaconda3/bin/conda’ ‘shell.bash’ ‘hook’ 2\> /dev/null)

### Installation

- is it working without installation if copied in the same Xwindow, Gnome?
    - copy directory &#9;&#9;&#9;&#9;&#9;# conda copy
        - modify starting from .bashrc
            - modify all ID’s in setting
            - find and modify all the initial files in the setting
        - check
            - ` conda info --envs for correct path `
        - As for installed package and execution file  modify path also
            - ` $ which ase `
            - ` vi $path_to_ase/ase	 modify path `
    - use environmental module
- install&#9;&#9;&#9;&#9;&#9;cf. [windows](<file:///C:\Users\hopef\AppData\Roaming\Microsoft\Word\Windows_software.docx>)
    - download
        - ` wget https://repo.continuum.io/archive/Anaconda2-4.2.0-Linux-x86_64.sh `
            - change version (linux-x86-64)
                - [https://repo.continuum.io/archive/](<https://repo.continuum.io/archive/>)
        - bash Anaconda2-4.2.0-Linux-x86\_64.sh -b \[-p ~/anaconda\]
            - “~/anaconda” is prefix for installation
    - setting or initialization in .bashrc
        - ` echo 'export PATH="~/anaconda/bin:$PATH"' >> ~/.bashrc `
        - or use module load
            - in case using anaconda.sh for initialization
                - ` source ~/anaconda.sh `
    - ` conda update conda `
- uninstall
    - ` conda install anaconda-clean `
    - anaconda-clean –yes
    - comment .bashrc
    - rm –rf anaconda
- python version check
    - ` which python `
        - python –version
    - ` conda search python `
        - \* is for current version: 3.6.3
- how to start
    - ` conda activate `
        - (base)
        - packages are installed at $ANA\_HOME/lib/python\_ver/site-packages
    - subcommands
        - clean, config, create, info, install, list, package, remove, search, update, upgrade
- install (from Debian)
    - download
        - ` wget https://repo.continuum.io/archive/Anaconda2-4.2.0-Linux-x86_64.sh `
            - change version (linux-x86-64)
                - [https://repo.continuum.io/archive/](<https://repo.continuum.io/archive/>)
        - bash Anaconda2-4.2.0-Linux-x86\_64.sh -b \[-p ~/anaconda\]
            - “~/anaconda” is prefix for installation
    - setting
        - ` echo 'export PATH="~/anaconda/bin:$PATH"' >> ~/.bashrc `
        - or use module load
    - ` conda update conda `
- uninstall
    - ` conda install anaconda-clean `
    - anaconda-clean –yes
    - comment .bashrc
    - rm –rf anaconda
- python version check
    - ` which python `
        - python –version
    - ` conda search python `
        - \* is for current version: 3.6.3

### using conda

- activation conda
    - if not want to activate in .bashrc
        - ` conda config --set auto_activate_base false `
    - run anaconda
        - ` source anaconda.sh `
            - or scripts listed in .bashrc
        - ` conda activate [env_name] `
            - activate (base)
            - set PATH to $HOME/anaconda3/bin
- create a new env
    - create env
        - ` conda create -n (--name) vname `
            - ` conda init bash `
    - create error
        - Condaverification error
            - ` conda clean --all  try again `
    - create env with the specified packages
        - ` conda create -n vname python=3.5 numpy scipy matplotlib `
            - installed at $ANA\_HOME/envs/vname/lib/python\_ver/site-packages
            - install separately using pip3 such as ase, amp-atomistics
                - these cannot be installed at the creating level
    - install a new python version in a new env
        - ` make new version of 2.7.13 with a new name of py27 `
            - check whether 2.7.13 is in the list (after ‘python’)
            - ` conda create –n py27 python=2.7.13 anaconda `
                - anaconda/envs/py27
        - to use new version
            - ` source activate py27 `
            - ` which python `
            - python -V
        - escape from py27
            - ` source deactivate py27 `
        - install in a new version, does not affect the original python environment
            - so each module need to be install at each different env
    - change python version completely
        - in case you need only one version
        - ` conda install python=3.5.3 `

### conda submodule						cf contents

- envs
    - envs check
        - ` conda info --envs `
        - installed at $ANA\_HOME/envs
    - create env
    - activate env
        - ` conda activate vname `
            - (vname) at prompt
    - deactivate
        - ` conda activate `
            - goes to (base)
        - ` conda deactivate `
            - escape from the present virtualenv
- info
    - ` conda info --envs `
- create
    - ` conda create -n envname -c channel `
        - -n envname to be created
            - locates at $anaconda/envs/envname
        - -c channel
            - additional channel to search for packages: url
                - defaults: channel\_alias = [http://conda.anaconda.org](<http://conda.anaconda.org>)
    - (rename)
        - ` conda create --name newname --clone oldname `
        - ` conda remove -n oldname --all `
    - clone
        - ` conda create --clone `
- remove
    - ` conda remove -n envname --all `
        - directory does not remove, so, manually remove to create again in the same name
- list
    - ` conda list `
        - shows installed package check
    - ` conda list -n myenv `
        - list all packages installed into the env of ‘myenv’
    - ` conda install packagename `
- miscellaneous
    - version check
        - ` conda --version `
    - manage different version
        - ` conda create -n vname python=3.5    # using different python version `
        - ` conda activate vname `
        - ` pip install --ignore-installed --upgrade tensorflow-gpu==2.0.0-beta1 `
            - installed ~anaconda/envs/vname/lib/python3.5/site-packages
    - remove cache
        - ` conda clean --all (-a) `
    - python downgrade
        - ` conda search python `
        - ` conda install python=3.6.5 `

### conda version control

- How to use newer python version
    - base with v 3.8, how to use v 3.10
    - ` make env with python v 3.10 `
        - py310                    /home/joonho/anaconda3/envs/py310
    - no need to activate py310 everytime
    - method 1
        - change shebang
            - ` #!/home/joonho/anaconda3/envs/py310/bin/python `
    - method 2 portable
        - shebang
            - ` #!/usr/bin/env python `
        - alias vasp\_py=”conda run -n py310 python”
    - qsub/sbatch in job submission
        - ` source ~/anaconda3/etc/profile.d/conda.sh `
        - ` conda activate py310 `

### conda error							cf. contents

- Solving environment: failed with initial frozen solve. Retrying with flexible solve
    - error when conda is not updated  conda update
    - solution
        - ` pip install --upgrade pip `
        - ` conda update -n base conda `
        - ` conda update --all `
- job in cgcnn
    - commands
        - ` conda upgrade conda `
        - ` conda create -n cgcnn python=3 scikit-learn pytorch torchvision pymatgen -c pytorch -c conda-forge `
    - fails in: conda upgrade conda
        - message: The environment is inconsistent, please check the package plan carefully. The following package are causing the inconsistency
        - fix up
            - ` conda install anaconda 	 may succeed `
            - ` conda update --all		 may succeed `
                - updates all the packages, and then conda solves the inconsistency on its own.
            - may skip conda upgrade conda
    - fails in: conda create -n cgcnn …
        - CondaHTTPError: HTTP 000 CONNECTION FAILED for url [https://conda.anaconda.org/conda-forge/linux-64/cudatoolkit-11.1.1-h6406543\_9.tar.bz2](<https://conda.anaconda.org/conda-forge/linux-64/cudatoolkit-11.1.1-h6406543_9.tar.bz2>)
        - fix up
            - ` conda config --set ssl_verify no `

### anaconda-navigator

- $anaconda-navigator
    - shows jupyterlab, jupyter notebook, spyter, etc

### jupyter

- [jupyter install without anaconda](<file:///C:\Users\root\AppData\Roaming\Microsoft\Word\perl_python_c++.docx>)
    - /home/joonho/anaconda/bin/jupyter
    - run jupyter
        - at console
            - jupyter notebook
                - open browser automatically
                    - browser:: localhost:8888/tree
        - as server
            - (nohup) jupyter notebook --port=8891 --no-browser 2\>&1 &
                - double dash for –port and –no-browser
                - no blank in between 2\>&1
                - blank with & for background
    - guest access to server
        - run
            - ` ssh -X -N -f -L 8891:localhost:8891 id@server 	cf. ssh `
        - open browser
            - [http://localhost:8891](<http://localhost:8891>)

### Python Package

- where to install
    - install package without conda
        - as root vs user
            - root: /usr/….
            - user: /home/user\_id/.local
    - with conda
        - as envs
            - (base) $ana\_home/lib/python3.x/site-packages
            - (vname) $ana\_home/envs/vname/lib/python3.6/site-packages
- how to install
    - without conda
        - install as root
            - using yum install
                - $yum (apt-get) install python-matplotlib python-numpy python-scipy
                    - location
                        - /usr/lib/python2.7/dist-package
        - install as user (e.g. ase)
            - ` pip install –-upgrade –-user ase `
                - installed in ~/.local/bin
            - ` pip install --upgrade --user numpy scipy matplotlib `
            - PYTHONPATH to ~/.local/lib/python2.7/site-packages
            - PATH to ~/.local/bin
    - with conda
        - install
            - ` pip install packagename==version `
                - -I: overwrite
        - uninstall
            - ` pip uninstall packagename `
- error in sys.path
    - in build such as
        - python setup.py install
        - add path to sys.path
    - if local path is involved in sys.path together with build path
        - can’t remove local path by sys.path.remove(‘local\_path’)
    - modify condahome/bin/activate
        - ` export PYTHONNOUSERSITE=site `
            - this removes path to local site
- AMP
    - install inside anaconda
        - v0.6
            - ` pip3 install amp-atomistics `
        - v0.7
            - ` pip3 install git+https://bitbucket.org/andrewpeterson/amp `
- other packages
    - ASE
        - as user
            - ` pip install –-upgrade –-user ase `
            - ` pip uninstall ase `
    - scikit
    - TensorFlow&#9;&#9;&#9;&#9;&#9;cf Anaconda [in Windows 10](<file:///C:\Users\hopef\AppData\Roaming\Microsoft\Word\Windows_software.docx>)
        - tf version
            - ≤ tf 1.5
                - if cup does not support AVX
            - ≥ tf 1.6
                - if cpu support AVX
                    - Core i3/i5/i7
        - python version
            - python 2.7
                - upto tf 2.1.0
                    - so, python 2.7 with tf 1.15
        - AVX: advanced vector expension
        - tf v
        - cpu version
            - ` pip install tensorflow `
            - on windows 10
                - ` pip install --user tensorflow==2.0 `
                - ` pip install --user tensorflow==1.15 `
        - gpu version
            - ` pip install tensorflow-gpu==2.0.0-beta1 `
        - The following NVIDIA® software must be installed on your system:
            - NVIDIA® GPU drivers —CUDA 10.0 requires 410.x or higher.
            - CUDA® Toolkit —TensorFlow supports CUDA 10.0 (TensorFlow \>= 1.13.0)
            - CUPTI ships with the CUDA Toolkit.
            - cuDNN SDK (\>= 7.4.1)
            - (Optional) TensorRT 5.0 to improve latency and throughput for inference on some models.

### jupyter

- install
    - [jupyter install without anaconda](<file:///C:\Users\root\AppData\Roaming\Microsoft\Word\perl_python_c++.docx>)
        - anaconda (base)
            - /home/joonho/anaconda/bin/jupyter
        - ` conda env `
            - ` conda activate env_name `
            - ` pip install jupyter `
    - run jupyter
        - at console
            - jupyter notebook
                - open browser automatically
                    - browser:: localhost:8888/tree
        - as server
            - (nohup) jupyter notebook --port=8891 --no-browser 2\>&1 &
                - double dash for –port and –no-browser
                - no blank in between 2\>&1
                - blank with & for background
    - guest access to server
        - run
            - ` ssh –X –N –f –L 8891:localhost:8891 id@server 	cf. ssh `
                - single dash
        - open browser
            - [http://localhost:8891](<http://localhost:8891>)
- jupyterlab
    - whatitis
        - installed by default ?
        - evolution from Jupyter Notebook to Lab
    - web
        - to install
            - ` conda install -c conda-forge jupyterlab `
        - ` conda update `
            - ` conda update -n base -c defaults conda `
    - run
        - open at console
            - jupyter lab&#9;&#9;! similar to jupyter notebook
        - open through IP
            - at host
                - jupyter lab --no-browser --ip=0.0.0.0
            - at guest
                - open web-browser
                    - [http://i.p.a.d.:8888/](<http://i.p.a.d.:8888/>)
    - manual
        - change between lab and tree
            - address://…./lab &#9;→ address://…/tree
        - creating file
            - +\|File
        - opening file
            - double click
        - flexible layouts
            - text and terminal
            - Notebooks
            - Console
            - Text Editor
            - Terminal
        - enhanced function
            - expand and collapse cells
            - drag and drop cells within the Notebook
            - Tab autocompletion in the Editor
            - Themes
- error
    - 500 internal server error
        - pip
            - ` pip install --upgrade nbconvert `
        - conda
            - ` conda install nbconvert=5.4.1 `

### Spyder

- terminal
    - $spyder
        - if error
            - ` conda update spyder `
            - ` conda install pyopengl `
- python IDE
    - integrated development environment

## Q-Chem (LCS)

### summary (succeed)

- version match (new)
    - Q-Chem vs intel
        - Q-Chem 5.1: intel classic compiler 17.x/18.x (2017-2018)
            - 2025: still intel ships the classic compiler
            - try XE2011
            - recommend classic ifort 17/18 from oneAPI
- v5.1 succeed in compilation
    - chi
        - intel by choi
        - try intel2019 gnu
            - check scripts qchem, parallel.csh
    - mlet
        - compiled by Intel in server
        - check qchem (set random QCSCRATCH), parallel.csh (set QCMPIRUN)
    - KISTI
        - find script
- install procedure
    - ` cd $QC `
        - ` ./configure -h `
        - mlet
            - ` ./configure intel mkl openmpi `
                - openmpi was compiled by intel in server
    - ` cd $QC/build `
        - ` make -j4 `
        - ` make install `
    - installs at
        - $QC/exe
            - qcprog.exe
        - $QC/lib
        - $QC/bin
            - qchem
            - parallel.csh
            - ` vi machines `
    - save the above installed directory
        - even though remove all the other dir’s for hard space
        - save config.log
- (e.g.) mlet using intel in server
    - Intel
        - ` INTEL=/gpfs/opt/intel/compilers_and_libraries/linux `
        - ` source $INTEL/bin/compilervars.sh intel64 `
    - env
        - ` setenv QCMPI=OPENMPI			used in parallel.csh `
            - proper mpirun should be evoked by qchem
        - ` OPENMPI=/gpfs/opt/openmpi `
        - ` QCMPIRUN=$OPENMPI/bin/mpirun `
        - ` MPICH_HOME=/gpfs/opt/openmpi `
        - ` LD_LIBRARY_PATH=../lib:../include:LD… `
        - ` PATH=$.../bin:$PATH `
    - error after changing directory name
        - ldd qcprog.exe shows link
            - but linkage is broken so cannot conceive the file
        - updatedb
        - locate filename
            - locate libboost\_filesystem.so.1.54.0
- setting
    - machinefile
        - $QC/bin/mpi/machines
            - localhost\\nlocalhost\\n…
            - or chi\\nchi\\n..
    - qchem wrapper in $QC/bin
        - select parallel or serial
            - \`qcprog.exe -p\` == “mpi” sets $WITH\_MPI=1
            - for usage
                - qchem -np np file.in file.out
                    - with random scratch folder
        - runs “parallel.csh” $WITH\_MPI==1
            - $QC/bin/parallel.csh $infile $prcs $numinp $QCFILEPREF $$ $pbs
            - cf. serial $WITH\_MPI==0
                - $QC/bin/serial.csh $infile $numinp $QCFILEPREF $$
        - random scratch in server
            - set QCSCRATCH = \`/gpfs/opt/qchem/bin/get\_scratch --auto\`
            - before
            - set QCSCRATCH = \`echo $QCSCRATCH/$user \| sed 's/\\/\*$//'\`
    - parallel.csh in $QC/bin
        - modify parallel.csh to set proper mpirun
            - if QCMPI
                - ` setenv QCMPIRUN $OPENMPI/bin/mpirun `
                    - ` OPENMPI ==? MPICH_HOME `
                    - ` mpirun is properly run in this setting `
                    - should not run $QC/bin/mpi/mpirun which will run 1 proc
        - echoes
            - “MPIRUN in parallel.csh is $QCMPIRUN”
                - use openmpi in server (mlet v5.1)
        - run
            - qchem -np np a.in a.out
            - $QCPLATFORM == else (LINUX\_Ix86\_64)
            - ` QCMACHINEFILE=$PBS_NODEFILE `
        - no need to run by mpirun if the above scripts are set properly
            - else, else, else
                - set QCCMD=”$QCMPIRUN -machinefile $QCMACINEFILE -np $2 $QCPROG $infileBase.$count $4 \</devnull”
                - will be
                - /gpfs/opt/openmpi/bin/mpirun -machinefile $QC/bin/machinefiles -np 16 $QC/exe/qcprog a.$count $4 \</dev/null”
                    - cannot be used at the moment
    - serial
        - qchem a.in a.out
        - qchem -save a.in a.out scratch\_name
            - chi: -save does not work for $QCLOCALSCR
                - just use $QCSCRATCH
                    - if QCLOCALSCR is not defined
                        - QCSCRATCH is used instead
                - then it works
    - parallel
        - qchem -np np a.in a.out
        - or mpirun: in case qchem is not working
            - ` mpirun -np 4 $QC/exe/qcprog.exe a.in $QCSCRATCH/savename > a.out `
                - makes 4 (-np 4) scratch folder in $QCSCRATCH
                    - savename.0 savename.1 savename.2 savename.3

### Installation general

- check before build
    - compiler
        - intel: icc, icpc, ifort, mpirun, mpicc
            - changed into: icx, icpx, ifx
        - gcc: gcc, g++, gfortran
    - env for installation
        - for QC
            - ` QC_EXT_LIBS=	for openmpi, fftw, openblas(mkl), etc `
                - mlet
                    - /gpfs/opt
                        - openmpi, fftw
        - for mpi
            - ` MPICH_HOME= `
                - mlet
                    - /pgfs/opt/openmpi
            - ` LD_LYBRARY_PATH= `
            - ` PATH= `
            - ` MANPATH= `
        - for intel
            - MKLROOT
                - this can be set in source $INTEL/bin/compilervars.sh intel64
- env for running
    - env
        - QCMPI&#9;openmpi
            - to use default mpirun
        - QCHOME&#9;&#9;&#9;for version control
            - for convenience
        - ` QC=$QCHOME/qchem or any version `
            - you can change the directory name and $QC for several version
        - ` QCAUX=			for basis `
        - ` QCSCRATCH=/scratch/$USER	for running and writing scratch to dir `
        - for parallel
            - ` QCPARALLEL=TRUE/FALSE `
            - ` QCRSH=ssh `
        - etc
            - set in mlet, but not sure these are necessary
            - OPENMPI
            - QCMPIRUN
        - INTEL
    - activate qchem
        - ` source $QC/bin/qchem.setup.sh `
            - in bash

### error

- parallel qchem runs only 1 process
    - $QCMPI should be properly set to run the expected mpirun

### openmpi vs openmp

- openmpi
    - distribute job into each cpu in parallel
    - ? blas and fftw run on each cpu so don’t need to parallelize
    - run qchem
        - qchem -np n inf outf
- openmp
    - distribute job into each cpu in parallel
    - each cpu calculate in parallel
        - blas, fftw needs to be compile in parallel
    - run qchem
        - qchem -nt nthreads inf ouf

### install

- env
    - after installation of openmpi (any mpi)
        - ` MPICH_HOME= `
        - ` PATH=”$MPICH_HOME/bin:$PATH” `
        - ` MANPATH=”$MPICH_HOME/man:$MANPATH” `
        - ` LD_LIBRARY_PATH=”$MPICH_HOME/lib:$MPICH_HOME/include:/usr/lib64[:$LD_LIBRARY_PATH]” `
            - last LD\_LIBRARY\_PATH depends on the location of env setting
        - check
            - then we can approach mpicc, mpiCC, mpifort
            - then we can compile OpenBLAS(mkl), fftw3
    - 2<sup>nd</sup> env for Qchem installation
        - ` QCHOME=/home/joonho/softwares/qchem `
        - ` QC_EXT_LIBS=$QCHOME/trunk `
            - trunk is source
                - it might be any version or compile date or something else
        - ` QCAUX=$QCHOME/qcaux `
            - it contains basis, ….
    - 3<sup>rd</sup> env for running Qchem
        - ` QC=$QCHOME/trunk `
        - ` QCSCRATCH=/scratch/joonho/QCSCR `
        - ` QCLOCALSCR=/scratch/joonho/QCLOC `
        - ` QCPLATFORM=LINUX_Ix86_64 `
        - ` QCSCR=ssh `
        - ` QCPARALLEL=TRUE `
        - if \[ -e $QC/bin \]; then
            - ` source $QC/bin/qchem.setup.sh	! extension might be different according to shell `
            - fi
    - ` ssh without passwd in cluster `
        - cf. ssh-keygen
- configure
    - ` ./configure -h `
    - it makes $QCHOME/build and configure.log
    - ` cd build and make, make install `
- gnu
    - prerequisite
        - install fftw in $QC\_EXT\_LIBS
        - install openblas in $QC\_EXT\_LIBS
        - use link
            - ` ln –s gnu-compiled-fftw fftw `
            - ` ln –s gnu-compiled-openblas OpenBLAS `
    - configure using gcc
        - serial
            - ` ./configure gcc 			! working for 5.1 `
                - w
                    - fftw2.1.5-serial
                    - openblas.0.2.20.cmake.se
                - use /usr/local/lib64/libopenblas.so.0
                    - if installed in root, openblas locates in /usr/local/
                        - /usr/local/lib64
                        - /usr/local/include
                - fftw is included by $LD\_LIBRARY\_PATH
            - ` ./configure gcc openblas 		! working for 4.3 but 5.1, 5.0b `
                - openblas\_serial v=0.2.20 in $QC\_EXT\_LIBS/OpenBLAS
                    - error of undefined reference: pthread\_atfork, pthread\_create
                        - why does it call thread in serial compilation
                        - \[99%\] built target libintok – make error 2
        - parallel
            - ` ./configure gcc openmpi `
                - serial openblas in root
                    - /usr/local/lib64/libopenblas.a&#9;
                        - used for serial compilation so do not overwrite root with parallel openblas
                - openmpi
                    - openmpi.2.0.2.gcc
                    - v 1.10 make error of C library
                - fftw in $QC\_EXT\_LIBS
                    - fftw2.1.5-mpi
                        - compiled by openmpi
                    - serial fftw is not recognized
            - ` ./configure gcc openblas openmpi		! not working `
                - configure succeed with the below
                - openblas in $QC\_EXT\_LIBS
                    - openblas.0.2.20.cmake.pa
                        - compiled by openmpi
                    - openblas by mpicc make error in compiling QChem
                        - error around 40%
    - build qchem
        - /build/make
            - makes qcprog.exe
            - ` make –j 4 for parallel compilation (-j4 or -j 4) `
        - /build/make install
            - install in $QC
                - $QC/exe
                    - qcprog.exe
                - $QC/lib
                    - all kinds of \*.a
        - hard usage
            - $QC
                - total 37G
                - /build 25G
                - /exe 2.9G
            - check ldd qcprog.exe
    - after installation
        - check size
            - ` source directory increases from 5G to 11G except /build `
            - /build has 25 G
            - keep to save storage
                - configure.log
                - /exe
                - /util
                - /lib
                - /bin
        - set env
            - QC
    - run
        - serial
            - qchem file.in file.out
            - serial calculation
                - EDA
        - parallel
            - ` mpirun –np 4 qchem a.in a.out `
                - ` mpirun –np 4 qcprog a.in $QCSCRATCH > a.out  ! by Dr. Choi `
                - qchem –np 2 file.in file.out&#9;&#9;! will not working
            - machine file if necessary
                - $QC/bin/mpi/machines
                - machines
                    - localhost
                    - localhost
                    - up to number of process
- error(OpenBLAS) in installation – gcc
    - 5.1 serial
        - succeed only by ./configure gcc which uses /usr/local/lib64/libopenblas.a by default
        - fail using $QC\_EXT\_LIBS/OpenBLAS-version
            - openblas error: 50% built target libintok: Error 2
    - 5.1 parallel
        - succeed by ./configure gcc openmpi which uses openmpi.2.0.2, fftw and
            - /usr/local/lib64/libopenblas.a by default
        - fails
            - openmpi-1.10
                - not define C\_MPI library
            - fftw-serial
                - cannot find fftw
            - ` ./configure gcc openblas openmpi `
                - undefined reference to \`pthread\_atfork'
    - try to use
        - ` ./configure gcc openblas openmpi nomgc nolibdftn nolibintok noccman2 debug `
- w. intel CHI
    - serial
        - ` ./configure intel mkl `
            - build in $QCHOME/build without FFTW (though fftw in $QC\_EXT\_LIBS)
        - ` cd build `
        - ` make -j 4 `
    - parallel
        - try by choi
            - ` ./configure intel mkl mpich2 nointracule nomgc noopt2 nolibdftn nonewpath2 `
    - Intel 2011 Choi version
        - license from choi
            - license
                - free license before v. 13
                    - copied by Dr. Choi
                    - do not change directory
                        - it should locate $HOME/suite/
                        - full path to
                        - $HOME/suite/intel/impi, Compiler
            - env (do not change directory)
                - ` export I_ROOT=”$HOME/suite/intel” `
                - ` source $I_ROOT/Compiler/XE2011.13.367/bin/compilervars.sh intel64 `
                - ` source $I_ROOT/impi/5.1.3.223/linux/intel64/bin/mpivars.sh `
                - ` source /opt/intel/composer_xe_2011_sp1.13.367/mkl/bin/mklvars.csh intel64 `
            - directory structure
                - mkl library install
                    - /opt/intel/
                    - ` make source `
                        - ` tar cvzf mkl.tar /opt/intel/composer_xe_2011_sp1.13.367/mkl `
                    - ` tar xvzf `
                        - ./opt/intel…
                    - ` cd opt `
                    - ` mv intel /opt/ `
                    - full path
                        - /opt/intel/composer\_xe\_2011\_sp1.13.367/mkl
            - compilation and run
                - compiled by Choi in outside machine
                - serial
                    - qchem a.in a.out
                - parallel
                    - ` mpirun –np 4 $QC/exe/qcprog.exe a.in $QCSCRATCH/scrname > a.out & `
                        - this generates QCSCR.0 QCSCR.1, ….
            - proper output
                - Process 0 of 4 is on chi - thread support 0
                - Process 1 of 4 is on chi - thread support 0
                - Process 2 of 4 is on chi - thread support 0
                - Process 3 of 4 is on chi - thread support 0
                - initial socket setup ...start
                - initial socket setup ...done
        - license from Intel – 2017 old
            - source
                - ~/sciwares/aux\_archive/intel/kisti\_suiteintel\_20171111.tar.gz
                - ./intel/impi, ./intel/Compiler

### w. intel MLET (succeed)

- general
    - using INTEL in server mlet
    - openmpi was compiled by INTEL in server
    - fftw v.2 was compiled by INTEL in server
- INTEL
    - ` INTEL = /gpfs/opt/intel `
    - ` source $INTEL/compilers_and_libraries/linux/bin/compilervars.sh intel64 `
- MPI env
- QC env
    - ` QCMPI=openmpi `
        - qchem wrapper in $QC/bin/qchem
- error w. intel
    - old version of Choi is not working for Qchem compile
        - MPI\_CXX\_COMPILES – failed
            - need to check openmpi again
            - unable to compile a simple MPI C++ program
            - set 1
                - openmpi – icc
                - openblas – icc
                - fftw – icc
        - not working with compilation
            - openmpi
                - ` ./configure CC=icc CXX=icpc F77=ifort FC=ifort --prefix=$QC_EXT_LIBS/openmpi –enable-static `
                - make
                - ` make install `
            - OpenBLAS
                - ` make on source `
                    - parallel, using openmpi (disregard cmake)
                        - ` make CC=mpicc CXX=mpiCC FC=mpifort F77=mpifort `
                        - ` make PREFIX=/path/to/your/installation install `
                    - serial
                        - ` make CC=icc CXX=icpc FC=ifort F77=ifort `
                        - ` make PREFIX=/path/to/your/installation install `
                - cmake
                    - ` cmake ../–DCMAKE_C_COMPILER=icc -DCMAKE_CXX_COMPILER=icpc –DCMAKE_Fortran_COMPILER=ifort –DCMAKE_INSTALL_PREFIX=/… `

### openmpi

- version matching
    - openmpi: v.1.10.1
    - it should locate at $QC\_EXT\_LIBS/openmpi
- install
    - CentOS, gcc 4.8, 2018
        - ` ./configure CC=gcc CXX=g++ F77=gfortran FC=gfortran --prefix=$QC_EXT_LIBS/openmpi –enable-static `
            - previously set env QC\_EXT\_LIBS
        - N.B.
            - prefix
    - two steps
        - make
        - ` make install `
    - equal to one step
        - ` make all install `
- install error
    - version 2.0 error
        - there is no libmpi\_f90.so.1
    - ` ./configure CC=gcc CXX=g++ F77=gfortran FC=gfortran --prefix=/home/joonho/qcextlibs/openmpi –enable-static –enable-mpi-cxx `
    - mvapich2
        - error: ‘infiniband/mad.h not found, retry with –disable-mcast
- env
    - common env
        - CC C compiler
        - CXX C++ compiler
        - F77 Fortran 77 compiler
        - FC Fortran 90 compiler
        - ` CFLAGS = args to icc (intel C compiler) `
        - ` CXXFLAGS = args to icpc (intel C++ compiler) `
        - ` FCFLAGS = args to ifort (Intel F90 compiler) `
    - to use QC\_EXT\_LIBS
        - ` export QC_EXT_LIBS=/path/to/dir/ `
- compile options
    - setting install directory
        - -- prefix=/path/to/installation/directory
        - (do not user root) superuser
            - /usr/local/openmpi\_version
    - library
        - –enable-static
    - binding
        - --enable-mpi-cxx
            - enable building the C++ MPI bindings (default: disabled)
            - this makes error when running qchem configure
                - error such as : MPI CXX binding is missing
        - --enable-mpi-fortran(=value)
- After installation
    - Set mpi variables
        - ` export MPICH_HOME=/path/to/install/ `
        - ` export PATH=$MPICH_HOME/bin:$PATH `
        - ` export MANPATH $MPICH_HOME/man:$MANPATH `
        - ` export LD_LIBRARY_PATH $MPICH_HOME/lib:/usr/lib64:$MPICH_HOME/include:$ LD_LIBRARY_PATH `
    - mpi commander
        - mpicc (oshcc) C wrapper for C
        - mpiCC (oshCC) (mpic++ if filesystem is case-insensitive) for C++
        - mpifort (oshfort) for Fortran
    - mpi test
        - openmpi-2.1…./example/hello.c
        - mpicc hello.c –o hello
        - ` mpirun –n 4 hello `
    - version check
        - ` mpirun –V `
        - ompi\_info

### OpenBLAS (gcc)

- general
    - This includes LAPACK so don’t need to install blas, lapack separately
    - ` git clone https://github.com/xianyi/OpenBLAS.git `
    - OS Linux
        - Architecture x86\_64
        - Binary 64bit
        - C compiler&#9;gcc
        - Fortran compiler gfortran
        - Library name&#9;&#9;libopenblas\_sandybridgep-r0.2.20.dev.a
            - Multi threaded Max = 12
    - version check
        - ` grep OPENBLAS_VERSION /usr/local/include/openblas_config.h `
- installation in gcc&#9;&#9;cf. Q-Chem instllation
    - cmake
        - serial
            - ` mkdir build `
            - ` cd build `
            - ` cmake –DCMAKE_INSTALL_PREFIX=$QC_EXT_LIBS/OpenBLAS .. `
            - make
                - takes time
            - ` make install `
        - parallel
            - ` cmake ../–DCMAKE_C_COMPILER=mpicc -DCMAKE_CXX_COMPILER=mpiCC –DCMAKE_Fortran_COMPILER=mpifort –DCMAKE_INSTALL_PREFIX=/… `
    - two step installation
        - direct Makefile would invoke an error
        - serial
            - ` make FC=gfortan `
        - parallel, using openmpi
            - ` make CC=mpicc CXX=mpiCC FC=mpifort F77=mpifort `
            - ` make PREFIX=/path/to/your/installation install `
        - structure
            - openblas\_HOME/lib64/
                - libopenblas.a
                - libopenblas.so -\> libopenblas.so.0
                - libopenblas.so.0 -\> libopenblas.so.0.2
                - libopenblas.0.2
- how to link to use library (needless in Q-Chem)
    - link shared library
        - gcc –o test test.c –I /opt/OpenBLAS/include/ -L/opt/OpenBLAS/lib –lopenblas
            - -o for compile to object file
            - -I for include directory
            - -l for library file of lib…a
            - for multithreaded add –lpthread
            - for LAPACK functions, add –lgfortran or other Fortan libs
    - link static library
        - gcc –o test test.c /opt/OpenBLAS/libopenblas.a

### fftw-qchem

- basic
    - use fftw2
    - separate for OpenBLAS
    - qchem automatically looks for /path/to/qcextlibs/fftw
- env
    - ` FFTW_HOME=$QC_EXT_LIBS/fftw `
    - ` LD_LIBRARY_PATH=”$FFTW_HOME/fftw/lib:$FFTW_HOME/fftw/include:$LD_LIBRARY_PATH” `

### Q-Chem (gnu) &#9;

- tips
    - cmake
        - latest version is required to install Qchem
    - what is happening for the compiled executables in system change?
        - it is working in system change from Debian to CentOS
            - gnu version would be same
    - cf. install-succeed in gnu,  [intel](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\MO_DFT_MM_MD.docx>)
    - w/wo license
        - web installing with license
            - [http://www.q-chem.com/qchem-website/doc\_for\_web/qchem-linux-install.shtml](<http://www.q-chem.com/qchem-website/doc_for_web/qchem-linux-install.shtml>)
            - go to Q-Chem install document
        - if got source, doesn’t need license
- env setting following installation
    - 1<sup>st</sup> env for mpi
        - after installation of openmpi (any mpi)
            - before installation, gcc(icc), g++(icpc), gfortran(ifort) are accessible
        - then we can approach mpicc, mpiCC, mpifort
        - then we can compile OpenBLAS, fftw3
    - 2<sup>nd</sup> env for Qchem installation
        - ` QCHOME=/home/joonho/softwares/qchem `
            - for convenience
        - ` QC_EXT_LIBS=$QCHOME/trunk `
            - trunk is source
                - it might be any version or compile date or something else
        - ` QCAUX=$QCHOME/qcaux `
            - it contains basis, ….
    - 3<sup>rd</sup> env for running Qchem
        - ` QC=$QCHOME/trunk `
        - ` QCSCRATCH=/scratch/joonho/QCSCR `
        - ` QCLOCALSCR=/scratch/joonho/QCLOC `
        - ` QCPLATFORM=LINUX_Ix86_64 `
        - ` QCSCR=ssh `
            - for shared directory for network communication
        - ` QCPARALLEL=TRUE `
        - if \[ -e $QC/bin \]; then
            - ` source $QC/bin/qchem.setup.sh	! extension might be different according to shell `
            - fi
    - ` ssh without passwd in cluster `
        - cf. ssh-keygen
- Gnu in linux (debian): only succeed mpi in root– original: how to ?
    - install openmpi
        - version check
            - ` mpirun –V `
                - open MPI 1.6.5
        - fail in 1.10
            - cannot find /openmpi/lib/libmpi\_usempi.so.1
    - set env using export variable=value
        - MPICH\_HOME
        - ` PATH=”$MPICH_HOME/bin:$PATH” `
        - ` MANPATH=”$MPICH_HOME/man:$MANPATH” `
        - ` LD_LIBRARY_PATH=”$MPICH_HOME/lib:/usr/lib64:$MPICH_HOME/include” `
    - install OpenBLAS, fftw
    - set env (not necessary in qchem running)
        - QC\_EXT\_LIBS – the location of openmpi, OpenBLAS, fftw
            - $QC\_EXT\_LIBS/openmpi
            - $QC\_EXT\_LIBS/OpenBLAS
            - $QC\_EXT\_LIBS/fftw&#9;-- searched automatically
    - install qchem
    - set env for qchem running
        - QC
        - QCAUX&#9;- basis, etc
        - QCSCRATCH
        - QCLOCALSCR
        - QCPLATFORM
        - QCRSH
        - QCPARALLEL
        - ` source $QC/bin/qchem.setup.sh	- for bash `
            - this install $PATH for $QC/bin for qchem executable
    - run
        - path for qchem in $QC/bin/qchem
            - set by $QC/bin/qchem.setup.sh
        - qchem –np 1 a.in a.out
            - if it succeeds, the bellows are perfect.
        - $QC/exe/qcprog.exe
            - ldd qcprog.exe shows all the shared libraries if not failed.
                - failure: libmpi.so.12 not found -\> qcextlibs/openmpi/lib/libmpi.so.12
            - mpi lib in $MPICH\_HOME under $QC
            - /lib, /lib64, /usr/lib are linked
        - $QC/bin/parallel.csh runs mpi/mpirun\_qchem and writes to $QCLOCSCR
            - mpirun\_qchem was compiled using openmpi in ldd qcprog.exe
            - P4\_RSHCOMMAND was set in parallel.csh using env
        - machine files are $QC/bin/mpi/machines
            - it lists chi, chi, chi, … up to 8 processes
- GNU install try again
    - just change the QCHOME in .bashrc
        - .bashrc
            - original
                - ` export QCHOME=$HOME/softwares/QChem `
                - ` export QC=$QCHOME/qchem `
            - for trial version
                - ` export QCHOME=$HOME/softwares/qchem-try `
    - based on openmpi
        - openmpi (cd openmpi-2.1.3)
            - ` ./configure CC=gcc CXX=g++ F77=gfortran FC=gfortran --prefix=$QC_EXT_LIBS/openmpi –enable-static –enable-mpi-cxx `
            - ` make all install 			! this makes ../openmpi `
            - check env setting
                - MPICH\_HOME including PATH, LD\_LIBRARY\_PATH
                - QC\_EXT\_LIBS, QCAUX
        - OpenBLAS (cd OpenBLAS-0.2.18)
            - ` make CC=mpicc CXX=mpiCC FC=mpifort F77=mpifort `
            - ` make PREFIX=$QC_EXT_LIBS/OpenBLAS install `
        - fftw3 (cd fftw-3.3.4)
            - ` ./configure –prefix=$QC_EXT_LIBS/fftw –enable-mpi `
        - Qchem (cd trunk)
            - configure
                - ` ./configure gcc release openblas openmpi `
            - build (cd build)
                - make
                    - error
    - based on mvapich2
        - mvapich2 has default of gnu
            - ` ./configure –prefix=$QC_EXT_LIBS/mpich2 `
            - in case no infiniband/mad.h run with –disable-mcast
            - require yacc
                - ` apt-get install byacc `
        - compile OpenBLAS, fftw3
            - use mpicc, mpic++-\>mpicxx, mpifort
            - OpenBLAS
                - ` make CC=mpicc CXX=mpic++ FC=mpifort F77=mpifort `
                - ` make PREFIX=$QC_EXT_LIBS/OpenBLAS install `
            - fftw3
                - ` ./configure --prefix=$QC_EXT_LIBS/fftw –enable-mpi `
                - ` make all install `
        - ` ./configure gcc release openblas mpich2 `
            - ` cd build `
        - make
            - automatically looking for $QC\_EXT\_LIBS/fftw for linking
- intel
    - source
        - intel & mkl
    - prepare qcextlibs
        - mpi
            - mvapich2-1.9
                - install to mpich2
                - ` ./configure CC=icc CXX=icpc F77=ifort FC=ifort --prefix=/home/joonho/qcextlibs/mpich2 –enable-static `
        - how to link fftw?
    - configure in qchem
        - ` tar trunk; mv trunk qchem; cd qchem `
        - ` ./configure intel debug mkl mpich2 `
            - build files are in /build
            - ` cd build `
        - make
        - ` ./configure intel release mkl mpich2 `
- run
    - qchem –np 1 mol.in mol.out
- status of machine
    - chi (gnu)
        - openmpi installed
        - mvapich
            - Qchem building(make)
    - rho
        - use pre-compiled openmpi
            - /opt/mpi/intel-12/openmpi-1.8.1
            - compile using mpi, fftw
            - qchem configured,
        - jackjack
            - qcextlibs: intel-Qchem building: make error
                - mvapich2-1.9 – error
        - mvapich2-2.3rcl (fail)
            - intel
                - configured
                - Error in make: compilation aborted rdma\_iba\_priv.c
            - gnu
                - the same error
        - openmpi (fail)
            - intel
                - Error: aclocal-1.15 is missing,
                    - need to upgrade aclocal-1.11
    - psi
        - mvapich2-2.3rcl
            - intel
                - Error: libibverbs not fould
            - gnu
                - the same error

### other package

- can skip Blas, lapack using mkl or OpenBLAS
    - BLAS: basic linear algebra subroutine
        - maker: intel MKL, HP, IBM, SGI, free OpenBLAS, atlas
        - generic blas does not have makefile
        - get and compile
            - get [http://www.netlib.org/blas/blas.tgz](<http://www.netlib.org/blas/blas.tgz>)
            - gunzip blas.tgz
            - ` tar xf blas.tar `
            - ` cd BLAS `
                - f77 –c –O3 \*.f&#9;# compile all the .f files to .o
                - ar rv libblas.a \*.o&#9;# combine all the .o to library
            - optimization options
                - g77 –O3 –fomit-frame-pointer –funroll-loops –malign-double-mcpu=i686 on a pentium II
                - (--with-blas=lib for MPB’s configure)
            - MPB looks for the standard library blas with –lblas so library files should be libblas.a
        - copy to std directory
            - standard directory /usr/local/lib
            - su –c “cp libblas.a /usr/local/lib”&#9;# switch to root and install
    - LAPACK: Linear Algebra PACKage
        - software looks for LAPACK by linking with –llapack
            - we need liblapack.a be installed in /usr/local/lib
                - (LDFLAGS defines library directories, --with-lapack=lib)
        - ` wget http://www.netlib.org.lapack/lapack.tgz `
            - ` cp make.inc.example make.inc `
            - make
                - Makefile
                    - include make.inc
            - ` make blaslib			# each target makes different library `
            - ` make cblaslib `
            - ` make lapackelib etc `
        - su –c “cp liblapack.a /usr/local/lib

### QChem

- awake
    - compiler
        - intel compiler
            - ` source /opt/intel/composer_xe_2011_sp1.13.367/bin/compilervars.csh intel64 `
            - ` source /opt/intel/composer_xe_2011_sp1.13.367/mkl/bin/mklvars.csh intel64 `
            - qchem, vasp
        - gnu does not need any pre-setting
    - options in configure
        - intel
            - ` ./configure CC=icc CXX=icpc F77=ifort FC=ifort –prefix –enable-static `
                - check by $which icc icpc ifort
        - gnu
            - ` ./configure CC=gcc CXX=g++ F77=f77 FC=gfortran `
- can skip Blas, lapack using mkl or OpenBLAS
    - BLAS: basic linear algebra subroutine
        - maker: intel MKL, HP, IBM, SGI, free OpenBLAS, atlas
        - generic blas does not have makefile
        - get and compile
            - get [http://www.netlib.org/blas/blas.tgz](<http://www.netlib.org/blas/blas.tgz>)
            - gunzip blas.tgz
            - ` tar xf blas.tar `
            - ` cd BLAS `
                - f77 –c –O3 \*.f&#9;# compile all the .f files to .o
                - ar rv libblas.a \*.o&#9;# combine all the .o to library
            - optimization options
                - g77 –O3 –fomit-frame-pointer –funroll-loops –malign-double-mcpu=i686 on a pentium II
                - (--with-blas=lib for MPB’s configure)
            - MPB looks for the standard library blas with –lblas so library files should be libblas.a
        - copy to std directory
            - standard directory /usr/local/lib
            - su –c “cp libblas.a /usr/local/lib”&#9;# switch to root and install
    - LAPACK: Linear Algebra PACKage
        - software looks for LAPACK by linking with –llapack
            - we need liblapack.a be installed in /usr/local/lib
                - (LDFLAGS defines library directories, --with-lapack=lib)
        - ` wget http://www.netlib.org.lapack/lapack.tgz `
            - ` cp make.inc.example make.inc `
            - make
                - Makefile
                    - include make.inc
            - ` make blaslib			# each target makes different library `
            - ` make cblaslib `
            - ` make lapackelib etc `
        - su –c “cp liblapack.a /usr/local/lib

### openmpi \[then OpenBLAS, fftw\]

- download
    - https://www.open-mpi.org/software/ompi/v4.1/
- install&#9;(same as mpich, mvapich for qchem, vasp)
    - ` ./configure `
        - intel
            - ` ./configure CC=icc CXX=icpc F77=ifort FC=ifort --prefix=/home/joonho/qcextlibs/openmpi –enable-static `
        - gnu (qchem, vasp)
            - ` ./configure CC=gcc CXX=g++ F77=gfortran FC=gfortran --prefix=/home/joonho/qcextlibs/openmpi –enable-static –enable-mpi-cxx `
            - mvapich2
                - error: ‘infiniband/mad.h not found, retry with –disable-mcast
    - two step
        - make
        - ` make install `
    - one step
        - ` make all install `
- env
    - common env
        - CC C compiler
        - CXX C++ compiler
        - F77 Fortran 77 compiler
        - FC Fortran 90 compiler
        - ` CFLAGS = args to icc (intel C compiler) `
        - ` CXXFLAGS = args to icpc (intel C++ compiler) `
        - ` FCFLAGS = args to ifort (Intel F90 compiler) `
- options
    - setting install directory
        - -- prefix=/path/to/installation/directory
        - superuser
            - /usr/local/openmpi\_version
    - library
        - –enable-static
    - binding
        - --enable-mpi-cxx
            - enable building the C++ MPI bindings (default: disabled)
            - this makes error when running qchem configure
                - error such as : MPI CXX binding is missing
        - --enable-mpi-fortran(=value)
- set path and MPICH\_HOME
    - ` setenv MPICH_HOME /path/to/install/ `
    - ` setenv PATH $MPICH_HOME/bin:$PATH `
        - set path = (. openmpi\_install\_directory/bin $path)
    - ` setenv MANPATH $MPICH_HOME/man:$MANPATH `
    - ` setenv LD_LIBRARY_PATH $MPICH_HOME/lib:/usr/lib64:$MPICH_HOME/include:$ LD_LIBRARY_PATH `
- mpi commander
    - C:&#9;mpicc (oshcc) C wrapper
    - C++:&#9;mpiCC (oshCC) (mpic++ if filesystem is case-insensitive)
    - Fortran:&#9;mpifort (oshfort)
- mpi test
    - openmpi-2.1…./example/hello.c
    - mpicc hello.c –o hello
    - ` mpirun –n 4 hello `
- version check
    - ` mpirun –V `
    - ompi\_info

### fftw install

- use fftw2
- install in parallel
    - ` ./configure --prefix=/path/to/qcextlibs/fftw --enable-mpi `
        - not need to write to /path/to/qcextlibs/OpenBLAS
        - qchem automatically looks for /path/to/qcextlibs/fftw
            - LD\_LIB\_PATH will include fftw
    - make
    - ` make install `

### cmake

- latest version is required to install Qchem
- download & install
    - cmake.v…sh&#9;&#9;! binary file
        - ` chmod 755 `
            - ./cmake.v…sh
                - unpack

### Q-Chem (gnu) &#9;

- cf. install-succeed in gnu,  [intel](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\MO_DFT_MM_MD.docx>)
- w/wo license
    - web installing with license
        - [http://www.q-chem.com/qchem-website/doc\_for\_web/qchem-linux-install.shtml](<http://www.q-chem.com/qchem-website/doc_for_web/qchem-linux-install.shtml>)
        - go to Q-Chem install document
    - if got source, doesn’t need license
- Gnu in linux (debian): only succeed mpi in root– original: how to ?
    - install openmpi
        - version check
            - ` mpirun –V `
                - open MPI 1.6.5
        - fail in 1.10
            - cannot find /openmpi/lib/libmpi\_usempi.so.1
    - set env using export variable=value
        - MPICH\_HOME
        - ` PATH=”$MPICH_HOME/bin:$PATH” `
        - ` MANPATH=”$MPICH_HOME/man:$MANPATH” `
        - ` LD_LIBRARY_PATH=”$MPICH_HOME/lib:/usr/lib64:$MPICH_HOME/include” `
    - install OpenBLAS, fftw
    - set env (not necessary in qchem running)
        - QC\_EXT\_LIBS – the location of openmpi, OpenBLAS, fftw
            - $QC\_EXT\_LIBS/openmpi
            - $QC\_EXT\_LIBS/OpenBLAS
            - $QC\_EXT\_LIBS/fftw&#9;-- searched automatically
    - install qchem
    - set env for qchem running
        - QC
        - QCAUX&#9;- basis, etc
        - QCSCRATCH
        - QCLOCALSCR
        - QCPLATFORM
        - QCRSH
        - QCPARALLEL
        - ` source $QC/bin/qchem.setup.sh	- for bash `
            - this install $PATH for $QC/bin for qchem executable
    - run
        - path for qchem in $QC/bin/qchem
            - set by $QC/bin/qchem.setup.sh
        - qchem –np 1 a.in a.out
            - if it succeeds, the bellows are perfect.
        - $QC/exe/qcprog.exe
            - ldd qcprog.exe shows all the shared libraries if not failed.
                - failure: libmpi.so.12 not found -\> qcextlibs/openmpi/lib/libmpi.so.12
            - mpi lib in $MPICH\_HOME under $QC
            - /lib, /lib64, /usr/lib are linked
        - $QC/bin/parallel.csh runs mpi/mpirun\_qchem and writes to $QCLOCSCR
            - mpirun\_qchem was compiled using openmpi in ldd qcprog.exe
            - P4\_RSHCOMMAND was set in parallel.csh using env
        - machine files are $QC/bin/mpi/machines
            - it lists chi, chi, chi, … up to 8 processes
- GNU install try again
    - just change the QCHOME in .bashrc
        - .bashrc
            - original
                - ` export QCHOME=$HOME/softwares/QChem `
                - ` export QC=$QCHOME/qchem `
            - for trial version
                - ` export QCHOME=$HOME/softwares/qchem-try `
    - based on openmpi
        - openmpi (cd openmpi-2.1.3)
            - ` ./configure CC=gcc CXX=g++ F77=gfortran FC=gfortran --prefix=$QC_EXT_LIBS/openmpi –enable-static –enable-mpi-cxx `
            - ` make all install 			! this makes ../openmpi `
            - check env setting
                - MPICH\_HOME including PATH, LD\_LIBRARY\_PATH
                - QC\_EXT\_LIBS, QCAUX
        - OpenBLAS (cd OpenBLAS-0.2.18)
            - ` make CC=mpicc CXX=mpiCC FC=mpifort F77=mpifort `
            - ` make PREFIX=$QC_EXT_LIBS/OpenBLAS install `
        - fftw3 (cd fftw-3.3.4)
            - ` ./configure –prefix=$QC_EXT_LIBS/fftw –enable-mpi `
        - Qchem (cd trunk)
            - configure
                - ` ./configure gcc release openblas openmpi `
            - build (cd build)
                - make
                    - error
    - based on mvapich2
        - mvapich2 has default of gnu
            - ` ./configure –prefix=$QC_EXT_LIBS/mpich2 `
            - in case no infiniband/mad.h run with –disable-mcast
            - require yacc
                - ` apt-get install byacc `
        - compile OpenBLAS, fftw3
            - use mpicc, mpic++-\>mpicxx, mpifort
            - OpenBLAS
                - ` make CC=mpicc CXX=mpic++ FC=mpifort F77=mpifort `
                - ` make PREFIX=$QC_EXT_LIBS/OpenBLAS install `
            - fftw3
                - ` ./configure --prefix=$QC_EXT_LIBS/fftw –enable-mpi `
                - ` make all install `
        - ` ./configure gcc release openblas mpich2 `
            - ` cd build `
        - make
            - automatically looking for $QC\_EXT\_LIBS/fftw for linking
- intel
    - source
        - intel & mkl
    - prepare qcextlibs
        - mpi
            - mvapich2-1.9
                - install to mpich2
                - ` ./configure CC=icc CXX=icpc F77=ifort FC=ifort --prefix=/home/joonho/qcextlibs/mpich2 –enable-static `
        - how to link fftw?
    - configure in qchem
        - ` tar trunk; mv trunk qchem; cd qchem `
        - ` ./configure intel debug mkl mpich2 `
            - build files are in /build
            - ` cd build `
        - make
        - ` ./configure intel release mkl mpich2 `
- run
    - qchem –np 1 mol.in mol.out
- status of machine
    - chi (gnu)
        - openmpi installed
        - mvapich
            - Qchem building(make)
    - rho
        - use pre-compiled openmpi
            - /opt/mpi/intel-12/openmpi-1.8.1
            - compile using mpi, fftw
            - qchem configured,
        - jackjack
            - qcextlibs: intel-Qchem building: make error
                - mvapich2-1.9 – error
        - mvapich2-2.3rcl (fail)
            - intel
                - configured
                - Error in make: compilation aborted rdma\_iba\_priv.c
            - gnu
                - the same error
        - openmpi (fail)
            - intel
                - Error: aclocal-1.15 is missing,
                    - need to upgrade aclocal-1.11
    - psi
        - mvapich2-2.3rcl
            - intel
                - Error: libibverbs not fould
            - gnu
                - the same error

## Science Package

### p4vasp

- installation
    - (debian) from repository
    - (centos) follow the below recipe
- download (no use)
    - [https://github.com/orest-d/p4vasp](<https://github.com/orest-d/p4vasp>)
        - ` git clone https://github.com/orest-d/p4vasp `
- guides
    - gcc is working
        - KISTI: remove all the module
            - ` module purge `
    - version compatibility
        - p4vasp-0.3.30 is compatible with fltk-1.3.0
        - download p4vasp-0.3.30
        - download fltk-1.3.0 in $P4HOME/ext
    - collective version vs separate version
        - ls /ext
            - collective version
                - build-fltk.sh clean.sh fltk-1.3.0/
            - independent version (no source file of fltk-directory)
                - build-fltk.sh clean clean.sh
- install p4vasp with fltk inside
    - turn on gcc
        - turn off icc
    - ` make main directory `
        - ` mkdir p4vasp_build `
    - download p4vasp
        - ` cd p4vasp_build `
        - ` wget https://github.com/orest-d/p4vasp/archive/refs/heads/master.zip -O p4vasp.zip `
        - unzip p4vasp.zip
    - download fltk
        - ` cd p4vasp-master/ext `
        - ` wget http://repository.timesys.com/buildsources/f/fltk/fltk-1.3.0/fltk-1.3.0-source.tar.gz `
        - ` tar -xvzf fltk-1.3.0 `
            - makes fltk-1.3.0/
    - install p4vasp with fltk
        - ` cd .. `
        - sh install-local.sh
            - writes PATH .bashrc

### LAMMPS

- directories
    - LMP\_HOME/
        - src
        - build
        - cmake
        - example
    - ` make in /src `
- prerequisite
    - fftw
- include packages /src
    - check packages
        - ` make package-status `
    - install packages
        - ` make yes-opt `
        - ` make yes-class2 `
        - how KIM ?
- build
    - modify /src/MAKE/Makefile.xxx
    - in /src
        - ` make xxx `
            - lmp\_xxx is made as execution file
- modify Makefile
    - intel
        - system
            - /opt/intel/compilers\_and\_libraries\_2019.3.199/linux/mpi/intel64/bin
        - MPI\_XXX section
            - leave it alone
        - FFT\_XXX section
            - ` FFT_INC = -DFFT_FFTW2 -l/home…./fftw.version-intel-pa/include `
                - ` INC = -DFFT setting `
            - ` FFT_PATH = -L/home……/fftw.version-intel-pa/lib `
                - ` PATH = path for FFT library `
            - ` FFT_LIB = -lfftw `
                - ` LIB = name of FFT library `
    - gcc

### Gromacs

- install
    - fftw3
        - gnu compile for gromacs 4.5.4
            - ` ./configure CC=gcc CXX=g++ f77=gfortran FC=gfortran --prefix=$EXTLIB/fftw3 --enable-mpi CFLAGS=-fPIC (--enable-avx ?) `
            - make
            - ` make install `
        - intel compile for gromacs 5.1.5 using SIMD
            - version 5 && SIMD
            - ` ./configure CC=icc CXX=icpc F77=ifort FC=ifort CFLAGS=-fPIC --enable-avx --prefix=$EXTLIB/fftw3 `
                - --enable-mpi gets error
    - gromacs
        - include
            - --with-fft=fftw3
        - try to use cmake
    - ` ./configure –disable-float –program-suffix=_d –prefix=<dir> `
        - gromacs installed in root without --prefix
            - /usr/local/gromacs

### Packmol

- install
    - download
    - ` tar xvzf `
    - make
    - install packmol to $PATH
- run&#9;&#9;&#9;
    - packmol \< packmol.inp
- detail cf [MO\_DFT\_MM\_MD.doc](<file:///C:\Users\hopef\AppData\Roaming\Microsoft\Word\MO_DFT_MM_MD.docx>)

### Java - eclipse

- java
    - jdk is installed
        - /usr/lib/jvm/java-1.8.0-openjdk
- eclipse
    - in linux
        - download installer
            - eclipse-installer
        - run installer
            - sudo eclipse-installer/eclipse-inst
            - select java or any other package
            - install at root (OK)
                - ` ln -s /opt/eclipse/java-2019-026/eclipse/eclipse ~/.local/bin/eclipse_s `
                - alias eclipse=”sudo ~/.local/bin/eclipse\_s”
                    - can be run as superuser
            - install at home (useless)
                - /home/joonho/utilwares/eclipse/java-2019-026/eclipse/eclipse
                - ./eclipse
                    - cannot open shared object: permission denied

### Intelij

- install
    - unpack
    - ` cd Intelij_HOME/bin `
    - ./idea.sh

### babel

## install w. library

### configure

- ` ./configure –h `
    - installation directory
        - --prefix=PREFIX&#9;: default /usr/local
            - ‘make install’ will install all the files in
                - /usr/local/bin, /usr/local/lib
    - options
        - --enable-mpi&#9;&#9;! fftw for parallel
    - ENV
        - ` CC=gcc `
        - ` CFLAGS=-fPIC	! fftw3 & gromacs `
        - ` F77=gfortran `
- e.g.
    - ` ./configure CC=gcc F77=gfortran –enable-mpi `
- build directory
    - on source directory
    - or separate directory
- make
- ` make install `

### cmake

## Autotools

### Build system

- composed of
    - autoconf, automake, libtool
    - ` apt-get install autoconf `
- build using make
    - authority
        - normally ./configure, make is done by user
        - ` make install is done by root `
    - 3 steps
        - ` ./configure `
            - system library analysis
            - generate Makefile
        - make
            - compile&#9;(gmake is gnu make)
        - ` make install `
            - install the built library and binary to prefix folder

### how to make

- write
    - ‘Makefile.am’&#9;&#9;# input to automake
    - ‘configure.ac’&#9;&#9;# input to autoconf
- automake makes Makefile.in based on Makefile.am
    - Makefile.in is platform for Makefile
- autoconf makes configure based on configure.ac

### e.g. 1  &#9;&#9;

- /hello &#9;&#9;&#9;http://linuxspot.tistory.com/45
- how to make “configure”
    - Makefile.am
        - ` SUBDIRS = src	# recursively finds sub-directories `
    - /hello/src
        - hello.c
        - Makefile.am&#9;&#9;# define sources and target
            - bin\_PROGRAMS = hello&#9;&#9;# generate binary hello
            - hello\_SOURCES = hello.c&#9;&#9;# source
    - autoscan
        - makes configure.scan&#9;
    - ` cp configure.scan configure.ac `
    - configure.ac -\> modify
        - AC\_PREREQ…
        - AC\_INIT(package name, version, email\_address)
        - AM\_INIT\_AUTOMAKE(hello, 1.0)
    - aclocal
        - makes aclocal.m4, autom4te.cashe
    - autoheader
        - makes config.h.in
    - autoconf
        - makes configure&#9;&#9;&#9;
- how to make “Makefile.in”
    - automake –foreign –add-missing –copy
    - makes
        - Makefile.in src/Makefile.in
        - compile, depcomp, install-sh, missing
- ` ./configure `
    - obtain system info and write them into config.status
    - config.status receive input from Makefile.in then write Makefile
- make

### configure.ac

- autoconfig
    - reads configure.ac to write configure
- contents
    - #ini part
        - AC\_INIT(likeU, 0.1, [REDACTED_EMAIL](<mailto:REDACTED_EMAIL>))
        - AM\_INIT\_AUTOMAKE (\[likeU\], \[0.1\] )
    - # C compiler and option check
        - AC\_PROG\_CC
    - # libm.a library existence check
        - AC\_CHECK\_LIB(\[m\], \[sin\])
    - # libint1.h head file check
        - AC\_CHECK\_HEADERS(\[libint1.h\])
    - # setlocale function check
        - AC\_CHECK\_FUNCS(\[setlocale\])
    - # after run ./configure what to make
        - AC\_CONFIG\_FILES(\[Makefile\])
        - AC\_OUTPUT

### Makefile.am

## Makefile

### whatitis

- to maintain groups of programs
    - to manage large program which need to be recompiled
- when
    - input file is modified, the out file is needed to be modified
    - like batch, automatic program run is needed

### arch.make

- Makefile would be long structure
- it has dependency on system
- System parameter is set in a different file  no need to change main structure of Makefile
- Makefile includes arch.make
    - include arch.make

### Basic structure

- overall structure
    - Macro definition
    - commands to get targets
    - dependencies
- target rule
    - structure
        - \<target\>: dependent object list
        - \_\_tab\_\_ \<command\>
    - target
        - label or resultant file after run command
        - object file or execution file
    - if dependent object is newer than target, “make target” executes command

### general rules in Makefile

- empty line: disregarded
- # comment
    - do not use # after \\
- for longer line, \\ two commands
    - multiline for single command
        - appended by \\
- ; for separate command lines
    - two line&#9;
        - my\_target:
            - ` echo “first command” `
            - ` echo “second command” `
    - separated by ;
        - my\_target:
            - ` echo “first command”; echo “second command” `
    - && or \|\| are works for conditional execution
- var vs Macro
    - both are same
    - Macro
        - ` OBJECTS = main.o foo.o bar.o `
        - ` CXXFLAGS = -O2 -g `
    - variable
        - ` DIR = “../test” `
    - dereferenced by
        - $(MACRO)
        - $(VAR)
    - if tab is not working
        - error: missing separator. Stop.
        - use semicolon
            - clean : ; @rm –rf \*.o like
- @command
    - @ : do not print command line but print the result
- make
    - runs Makefile and if not, makefile
- input variable in command line
    - ` make FC=gfortran CC=gcc USE_THREAD=0 `
- ` BLASLIB = -L/home/joonho/softwares/vasp-test/OpenBLAS –lopenblas `
    - such as BLASLIB = -L/home/$USER/…&#9;not working

### make options

- –j#
    - # is integer
- –p
    - shows variables

### e.g.

- C compiler
    - -c : compile .c (.cpp, etc) makes .o object file
    - -o : makes execution binary file in the specified name
- program1
    - gcc -o helloworld helloworld.c
- program2
    - gcc -o a.out main.c input.c output.c
    - makefile 1: target and command
        - a.out :
            - gcc -o a.out main.c input.c output.c
    - makefile 2: many related files
        - a.out : main.o input.o output.o
            - gcc -o a.out main.o input.o output.o
        - main.o : main.c
            - gcc -c main.c
        - input.o : input.c
            - gcc -c input.c
        - …
    - makefile 3: use MACRO
        - ` OBJ = main.o input.o output.o `
        - a.out : $(OBJ)
            - gcc -o a.out $(OBJ)
        - main.o : main.c
            - gcc -c main.c
        - …
    - makefile4
        - ` OBJ = main.o input.o output.o `
        - ` SRC = main.c input.c output.c `
        - ` CFLAGS = -g `
        - ` TARGET = a.out `
        - $(TARGET) : $(OBJ)
            - $(CC) -o $(TARGET) $(OBJ)
        - clear :
            - rm -f $(OBJ) $(TARGET) core
        - main.o : main.c
        - input.o : input.c
        - …

### Macro

- whatitis
    - just symbol to define a specific code
    - contents
        - suffix rule,
- rule
    - \<macro name\> = \<macro sentence\>
        - ` CC = gcc `
            - for CC, capital is normally used
        - Makefile uses shell env variables so do not overwrite
    - dereference
        - $(macro name)
            - $\{..\}, $.. are possible but use $(…)
    - e.g.
        - ` OBJ = main.o read.o write.o `
        - test : $(OBJ)
            - gcc -o test $(OBJ)
    - predefined macro
        - ` AS = as `
        - ` CC = C compiler `
        - ` CXX = C++ compiler `
        - ` FC = Fortran compiler `
        - ` CFLAGS = C compile option `
        - ` CXXFLAGS = C++ compile option `
        - ` CPP = C preprocessor `
        - ` LDFLAGS = link flags `
            - why predefined?
                - these are used internally also
- macro for path
    - ` INC = include-path for head files `
        - –I&#9;(include)&#9;&#9;# capital I
            - header directory
            - link option
        - e.g.
            - XXX\_INC -D… -l…
                - -l…. include file
                - -D variable=defined\_value
    - LIBS
        - –L/path-to-library
        - -llib\_filename
        - e.g.
            - ` XXX_PATH = -L/library_path/lib `
            - ` XXX_LIB = -lfftw `
                - -llib\_name
    - cf.
        - fftw
- suffix rule
    - e.g.
        - ` OBJ = main.o read.o write.o `
        - ` SRCS = main.c read.c write.c	! not necessary `
        - ` CC = gcc `
        - ` CFLAGS = -g –c `
            - if -c is defined,
        - Target = test
        - $(TARGET): $(OBS)
            - $(CC) –o $(TARGET) $(OBJ)
        - clean:
            - rm ..
        - main.o : io.h main.c&#9;&#9;! there is no command line
    - .SUFFIXES : .c .o
        - .c .o files are treated by suffix rule
            - ` make will automatically compile .c source file to .o object file `
        - by the suffix rule the following is run automatically
            - .c.o: ; $(CC) $(CFLAGS) –c $\< -o $@
                - $\< filename w/o extension and first part target (.c.o)
                    - main.c
                - $@ filename with latter part of target (.c.o)
                    - main.o
        - the leftist (first) dependent or newer file than target
        - internal suffixes
            - .out .a .ln .c .cc .C .p .f .F…
            - but it would be better to use .c.o target definition
    - defined rule
        - .c.o:
            - $(CC) $(CFLAGS) –o $@ -c $\<
                - common extension rule which reads .c file to generate .o file
        - e.g.
            - test: test.o
                - $(LD) $(LDFLAGS) –o $@ $^
            - .c.o:
                - $(CC) $(CFLAGS) –o $@ $\<
                    - compile .c to .o
                    - $\< is changed into source file of .c, “test.c”
                    - $@ is target of “test.o”
- internal macro
    - e.g.
        - test: $(OBJS)
            - gcc –o $@ $^&#9;&#9;! or
            - gcc -o $@ $\<
    - $@ or $(@) is target
    - $\<&#9;earlier filename than time of target
    - $^&#9;all the dependent objects in the list
        - target: dep1.c dep2.c
            - gcc –o target dep1.c dep2.c
            - change into
                - gcc –o $@ $^
    - $?&#9;newer dependent object list than present target
        - normally for library
    - $\*&#9;target file without extension
        - main.o : main.c io.h
            - gcc -c $\*.c
    - e.g.
        - .PHONY: all clean
            - reserved target “.PHONY” lists fake targets
            - just shows what kinds of targets there are
        - all: test
            - list last target
            - “make all” is the same as “make test”
            - the first target except .target’s can be skipped in make command
                - “make” is the same as “make all”
        - clean:
            - $(RM) \*.o
        - test: $(OBJS) ; $(LD) –o $@ $^
            - command line is inline with target using ;
        - hello.o: $([$@:.o=.c](<mailto:$@:.o=.c>)) $([$@:.o=.h](<mailto:$@:.o=.h>)) Makefile
            - $@ is hello.o
            - hello.o will be changed to hello.c
            - note there is not command line then it will be done by the next common rule
            - if Makefile is modified, hello.o will be rebuilt
        - .c.o: ;&#9;$(CC) –o $@ $\<
- special macro
    - recursive macro
        - ` A = $(B) DD `
        - ` B = C `
        - …
        - @echo $(A)&#9;&#9;# prints C DD
    - simple extension macro
        - a := $(b) dd
        - b := c
        - …
        - @echo $(a)&#9;&#9;# prints dd
- internal extension rule
    - ` make –p `
        - %.o : %.c
            - $(COMPILE.c) $(OUTPUT\_OPTION) $\<
        - as for \*.c use COMPILE.c (gcc) for compile
        - $\< used for extension rule is for dependent files
    - redefine internal extension rule
        - .SUFFIXES: .o .c
        - %.o: %.c
            - $(CC) –DDEBUG –c –o $@ $\<
        - -- if finds \*.c, makes \*.o using the above rule
- Macro substitution
    - $(MACRO:OLD=NEW)
        - in variable $MACRO, OLD is changed into NEW
    - e.g.&#9;
        - ` MY_NAME = Joonho Park `
        - ` YOUR_NAME = ${NAME:Jack=Jook} `
    - e.g.2
        - ` OBJS = main.o read.o write.o `
        - ` SRCS = $(OBJS:.o=.c) `
            - ` SRCS =  main.c read.c write.c `
        - $(OBJS:%.o=%.c) would be same as $(OBJS:.o=.c)
- Automatic dependency: gccmakedep
    - whatitis
        - target: dependency; command
            - dependency is necessary but,
            - command is repeated so many times
- e.g.
    - ` CC		= gcc `
    - ` CFLAGS		= -W –Wall –O2 `
    - ` LDFLAGS	= -lm `
    - like : like.c love.c
        - $(CC) $(CFLAGS) –o $@ $^ $(LDFLAGS)
    - clean :
        - @rm –rf \*.o like
- e.g. 2
    - ` CC	= gcc `
    - ` CFLAGS	= -W –Wall `
    - ` TARGET	= diary `
    - all: $(TARGET)
    - $(TARGET): memo.o calender.o main.o
        - $(CC) $(CFLAGS) –o $@ $^
    - memo.o: memo.c
        - $(CC) $(CFLAGS) –o $@ $^
    - calendar.o: calendar.c
        - $(CC) $(CFLAGS) –o $@ $^
    - main.o: main.c
        - $(CC) $(CFLAGS) –o $@ $^
- e.g. 3
    - ` OBJ = memo.o calendar.o main.o `
    - all: diary
    - diary: $(OBJ)
        - $(CC) –o $@ $^
    - -- as for each dependencies, it uses extension rule for file.c

### variable

- = vs :=
    - =
    - :=
- ( ) vs \{ \}
    - basically same
    - \{ \} denotes variable from shell
    - ( ) denotes Makefile-defined variable

### Command

- Makefile
    - $(info …… $(VAR))&#9;# write this sentence
- MAKEFILE\_LIST&#9;names of Makefiles
    - ` FILE_NAME := $(MAKEFILE_LIST) `
    - $(info MAKEFILE\_LIST: $(FILE\_NAME))&#9; Makefile
    - \_THIS\_FILE := $(lastword $(MAKEFILE\_LIST))  Makefile
- abspath
    - ` ABSPATH := $(abspath $(_THIS_FILE)) 	 /home/joonho/exe/makefile/Makefile `
- dir
    - \_ATOM\_DIR  := $(dir $(abspath $(\_THIS\_FILE)))
        - $(info ATOM\_DIR is : $(\_ATOM\_DIR))  /home/joonho/exe/makefile/
- abspath ..
    - to get .. directory
    - ` WDIR       := $(abspath $(_ATOM_DIR)..) `

## Library

### general

- rule for naming
    - soname
    - realname

### summary in Debian part

- extension
    - .o: &#9;object file
        - gcc –c filename.c&#9;&#9;! –c : compile
            - filename.o
        - .out: executive file from gcc a.c –o (outfile) a.out
    - .a: an archive library containing many .o files
        - ls \*.o
            - a.o, b.o, c.o
        - ar q libmy.a \*.o
            - makes libmy.a
        - ar t libmy.a
            - a.o b.o c.o
    - .lo: library object when compiled with –fPIC
        - position independent object files
            - libtool compile command
            - -fPIC option
        - libtool compile gcc –c a.c
            - libtool: compile: gcc –c a.c –fPIC –DPIC –o ./libs/a.o &#9;! PIC code
            - libtool: compile: gcc –c a.c –o a.o \>/dev/null 2\>&1&#9;! non-PIC code
            - ls
                - a.lo, a.o
    - .so: shared object which contains PIC objects
- static executable
    - use .o and .a
- dynamic executable
    - bind with libraries at run time
    - use .lo and .so

### shared vs static&#9;cf. ld

- static library
    - library is included in executable
    - e.g. liblammps.a
- shared library = dynamic library (windows DLL(dynamic link library))
    - file executable
    - when executable is called, dynamic loader occurs
        - load linked dynamic library on memory
        - call entry function (cf. main() in C)
        - execute program
    - e.g. liblammps.so
- naming rule
    - name w. version
        - libname.so.version
    - called name has link to version
        - ` ln –s libname.so.version libname.so `

### path for finding

- the linker uses the following search paths to locate required shared library:
    - -rpath-link
    - -rpath
    - -L
    - LD\_LIBRARY\_PATH&#9;&#9;# path used for linux command “ld”
    - /lib and /usr/lib
- LD\_LIBRARY\_PATH&#9;! setting variable
    - /lib64, /usr/lib64 are default path (doesn’t need to be included)
- rpath
    - pre-referred path before LD\_LIBRARY\_PATH
        - -Wl, -rpath
        - gcc –Wl, -rpath, /usr/local/lib hello.c
    - check whether executable has rpath
        - readelf –d a.out \| grep RPATH

### compile options

- library
    - -L&#9;: path for looking for a library
        - -L/opt/intel/…
    - -l (lower case L): link library
- head file
    - -I (upper case i): include header file
        - -I/$HOME/sciwares/p4vasp/src/include&#9;&#9;! dir not file
    - -include
- -static : if static library exists, compile that
- -shared : if shared library exists, compile that
- -D: set value of a variable

### ld - Linux command

- e.g.
    - ld -o a.out /lib/crt0.o hello.o -lc
        - output a.out
        - link with /lib/crt0.o, hello.o and library libc.a
- option
    - -larchive == --library=archive
        - add archive file “archive” to the list of files to link
        - ld search its path list
        - first search .so and then .a
    - -Lsearchdir == --library-path=search\_dir
        - add path searchdir to the list of paths that ld will search for archive library
        - all -L options apply to all -l option
        - “=” is replaced by the sysroot prefix
    - -rpath-link DIR
- usage
    - linker is invoked indirectly via a compiler driver such as gcc
    - gcc -@l, --stargroup foo.o bar.o -Wl, --endgroup
- the linker uses the following search paths to locate required shared library:
    - -rpath-link
    - -rpath
    - -L
    - LD\_LIBRARY\_PATH
    - /lib and /usr/lib

### ldconfig

- whatitis
    - setting dynamic linker which connect dynamic/shared library at runtime
        - runtime dynamic linker == /lib/ld.so
    - ldconfig -v
        - ` module update `
    - ` vi /etc/ld.so.conf `
        - add path
        - ldconfig configure\_file
        - is not used when compile
- e.g.
    - ldd /bin/ls
        - shows so list and path
        - /etc/ld.so.conf sets this path
    - install apache or mysql
        - after installation
        - add library fold in /etc/ld.so.conf
        - ldconfig

### ldd

- what’tis
    - list dynamic dependencies
        - ask a program or a library to check the shared library dependency
    - /usr/bin/ldd
- usage
    - ldd option exe\_file
- option
    - --version: ldd version
    - -v, --verbose: info
    - -d, --data-relocs
        - object not located in the original location is relocated and print result
    - -r, --function-relocs
        - data object and function relocated and print not-located function
    - --help

### error

- finding library
    - how to confirm library dependence (error: can’t load library libevent.so)
        - ldd /usr/bin/vim
- ImportError
    - version ‘GLIBC\_2.20’ not found (required by $LIBS/openmpi-gcc/lib/libmpi.so.40
    - GLIBC
        - gcc library
        - gcc and glibc version is fixed when a system installed
    - confirm the LD\_LIBRARY\_PATH and locate the lib file
        - then open new terminal
            - “source .bashrc” is not enough

## <br>

## System Management

## Login

### last

## Network

### ip&#9;&#9;&#9;cf man, debian install, ip, iptable,

- Usage
    - ip \[options\] objects \{command\|help\}&#9;cf. what is \{ \}
        - objects = \{link \| address …\}
        - options = \{ -V \| -s\[tatistics\] \| …
    - objects should follow command “ip”
- ip a
    - a is a\[ddress\]
    - shows all the network&#9;&#9;cf. ifconfig
    - refer to enp2so
- ip link
    - ib for infiniband interface
    - eth for ethernet interface
- cf. inet, brd

### iptables

- open port 443&#9;&#9;&#9;cf open port
    - iptables -A INPUT -p tcp -m tcp -dport 443 -j ACCEPT

### netstat

- install
    - debian
        - ` sudo apt update `
        - ` sudo apt install net-tools `
            - /usr/bin/netstat
- usage
    - netstat -a&#9;&#9;&#9;cf. port number&#9;ss
        - shows all the ports
        - check open ports
    - -pln
    - netstat -tuplen \| grep LISTEN
        - only display open ports
- options
    - -t: all tcp, only show TCP ports
    - -u: all udp
    - -l: listening server sockets
    - -p: show PID/software
    - -n: don’t resolve names, port numbers instead of names
    - --version

### nmap

- Network Mapper
    - detect host
    - port scan
    - detect version
    - OS check
- options
    - -P0
        - port scan
        - PORT&#9;&#9;STATE &#9;&#9;SERVICE
        - 22/tcp&#9;&#9;open&#9;&#9;ssh
        - 5000/tcp&#9;&#9;open&#9;&#9;npnp
            - upnp (Universal Plug and Play)
    - sudo nmap -sT -0 localhost&#9;&#9;&#9;&#9;cf. open port
- UPNP
    - uses two ports, 5000 tcp, 1900 udp

### ping

- network checking
    - ping [www.google.com](<http://www.google.com>)
        - this should work
    - ping chi.kaist.ac.kr
        - if this is not working, try IP
        - ping 143.248.148.4
            - then, DNS might be broken
    - if network is not working, try nmtui

### avahi-daemon

- whatitis
    - using mDNS/DNS-SD protocol suite, search local network service
    - view a chat-available person in the network
    - find a shared printer
    - without DNS server, make an IP network user can use

### Security

- tls/ssl
    - tls: Transport Layer Security
        - ssl: pass naming, secure sockets layer

### proxy

- [https://www.joinc.co.kr/w/Site/System\_management/Proxy](<https://www.joinc.co.kr/w/Site/System_management/Proxy>)
- purpose
    - security:
    - speed: cache
    - ACL
    - Log/Audit:
- kinds
    - forward proxy
    - reverse proxy
- Construct proxy server
    - whatitis?
        - Kakao is blocked by firewall of KAIST
        - using other proxy, Kakao is transferred by bypass
- setting proxy in ubuntu
    - https://ko.linux-console.net/?p=2865
    - install
        - ` apt-get install squid -y `
        - systemctl status squid&#9; active
        - netstat -plunt \| grep 3128&#9;  show LISTEN
            - install netstat
    - Setting
        - based on IP
            - ` sudo vi /etc/squid/squid.conf `
                - at first line
                - acl client1 src 143.248.148.15 (eta)
                - acl client2 src 192.168.10.10
                - http\_access allow client1 client2
                    - client1, client2 is id’s for ip’s
            - systemctl restart squid
                - only allowed ip’s can access to proxy
        - based on user approval
            - using user/passwd
            - ` apt install apache2-utils -y `
            - htpasswd /etc/squid/passwd client1
                - New password:
                - Re-type …
                - Adding password for user client1
            - ` make a second user `
            - confirm
                - cat /etc/squid/passwd
                    - client1: …
                    - client2: …
            - ` sudo vi /etc/squid/squid.conf `
                - remove the above 3 lines and add
                - auth\_param basic program /usr/lib/squid3/basic\_ncsa\_auth /etc/squid/passwd
                - acl ncsa\_users proxy\_auth REQUIRED
                - http\_access allow ncsa\_users
            - systemctl restart squid
    - ` make traffic anonymous `
        - [https://ko.linux-console.net/?p=2865](<https://ko.linux-console.net/?p=2865>)

<br>

## Shell & Cluster

## Shell

### syntax of bash or tcsh

- common shell command used in Command Line Interface
    - ls, cp, mv, rm, mkdir, chmod, passwd, pwd, whoami, which, echo, and so on
    - advanced: df, du,  …
- variables
    - environment variables: global
        - HOME, SHELL, USER, HOST
        - PATH, PYTHONPATH
    - “common” variables: local
- alias
    - e.g.
        - alias gowork=”cd $HOME/research/gromacs/coumalin”
    - how to run
        - .bashrc &#9;! or
        - ~/scripts/alias.sh
            - ` vi .bashrc `
                - if \[ -f $HOME/scripts/alias.sh \]; then
                - ` source $HOME/scripts/alias.sh `
                - fi

### login shell

- set by superuser
    - different prompt depending on shell and user
        - ` $ for bash `
        - % for tcsh
        - # for superuser

### run script

- batch file
    - list of shell command
- run
    - bash batch.sh
        - python a.py
    - change file to the executable
        - shebang (#!)
            - ` which bash `
                - /usr/bin/bash
            - a.sh
                - ` #!/usr/bin/bash `
        - chmod
            - ls -a batch.sh
                - -rw-r--r-- blabla…&#9;&#9;(644)
                    - user group others
            - ` chmod 755 batch.sh `
                - ls -l batch.sh
                    - -rwx-r--r--
        - run
            - pwd
                - ./batch.sh
            - using PATH
                - ` mv batch.sh ~/bin `
                - ` PATH=$HOME/bin:$PATH		! in .bashrc `
                - in any directory
                    - bat + \[tab-key\]

## Bash

### link to

- if, matching, var, var\_default, list
- subcommand inside script
    - wrap command to get the output

### log in

- order of initial running script
    - .bash\_profile
        - if exist, it does not read
            - .bash\_login
            - .profile
    - .bashrc
        - put the command here rather than .bash\_profile

### variable

- variable-related command
    - set
        - display all the variables
    - unset var
        - remove variable
- set variable
    - ` VAR=VALUE `
        - with no space around “=”
        - any type
            - a=999
            - ` LIST=”/var/oopt/bin/” `
        - cf. default value
    - local var
        - temporary variable assignment
            - ` VAR=VALUE `
            - scope is under the current shell
        - declare option VAR
            - option: -riafx
            - e.g.
                - declare –I intvar
                - intvar=123
        - dereference
            - $VAR
        - local variable in function
            - local lvar=”local contents”
- ` export global (env) variable `
    - global variable is also env variable
        - ` export EVAR=VALUE `
            - e.g. export a=999
        - show env variables
            - $env
            - $printenv
    - PATH
        - path to all the Linux command
        - initial setting for PATH
            - /etc/profile
        - add more paths to PATH
            - ` PATH=”$PATH:/home/joonho/bin” `
            - ` export PATH `
        - permanent initialization
            - superuser can set for all users
                - /etc/profile
            - user defined path
                - ~/.bash\_profile
    - important env variables
        - HOST
        - PATH
        - PYTHONPATH
        - LD\_LIBRARY\_PATH
- in script
    - var is not inherited while env\_var is inherited
    - e.g.
        - var.txt
            - vv=”variable”
            - ` export VV=”ENV” `
        - ` source var.txt `
        - var.sh
            - ` #!/usr/bin/bash `
            - ` echo “vv = $vv” `
                - vv =
            - ` echo “VV = $VV” `
                - ` VV = ENV `
- parameter expansion
    - $\{var\}&#9;simple dereference
    - $\{var:-default\}&#9;use default if var is unset or empty
    - $\{var:=default\}&#9;set var=default if unset or empty, then use it
    - $\{var+alt\}&#9;
        - alt only if var is set
            - even if it’s empty
        - “” if var is unset
    - $\{var:?error\}&#9;exit with error if var is unset and empty
    - $\{var#pattern\}&#9;remove shortest match from beginning of value
    - $\{var##pattern\}&#9;remove longest match from beginning
    - $\{var%pattern\}&#9;shortest … from end
    - $\{var%%pattern\} longest … from end

### special characters: ;, \\

- ;
    - command separator
    - usage
        - clear; ls
            - execute clear then ls&#9;&#9;cf. -exec
- \\
    - escape character
    - \\; remove the meaning of ; in shell

### parameter expansion: $

- parameter expansion
    - $\{parameter\} for parsing
        - separate variable and the appended string
    - node=$\{host\}01
        - separation of host and 01
- command substitution
    - execution of shell command in script
        - \`hostname\`
        - $(pwd)
        - output=$( ./my\_scriopt.sh )
            - store the output of command
- arithmetic expansion
    - host=$(hostname) &#9;# execution rule for $( )
        - i=1
            - node=singlet01
- dereference of variable
    - a=”she”
    - ` echo $a `
- default value for positional argument
    - $\{var\}
        - same as $var but sometimes $\{var\} only works
    - $\{var:-word\} &#9;# use ‘word’ if var is unset or null
        - Word can be string another variable
            - var=$\{1:-sp\}
            - var=$\{1:-$job\}&#9;&#9;# with job=sp before
        - var2=$\{1:-$var1\}
            - if $1, var2=$1
            - else var2=$var1
    - $\{var:=word\}&#9;# assign ‘word’ to var if unset or null
    - $\{var:+word\}&#9;# Use ‘word’ if var is set (non-empty)
    - $\{var:?msg\}&#9;# Error with ‘msg’ if var is unset/null
- string length
    - $\{#var\}
    - $\{#parameter\}
        - length of $parameter when it is expanded to value
        - parameter==\*, @: number of positional parameters
- string manipulation
    - substring extraction
        - $\{var:offset\}&#9;&#9;# From offset to end
        - $\{var:offset:length\}&#9;# From offset with length
        - $\{var:index\}
            - extract from index&#9;
            - $\{var:i:j\}
                - start from i cut length of j
        - e.g.
            - stringZ=abcdef
            - At position
                - $\{stringZ:0\}&#9;# all the elements
                - $\{stringZ:1\}&#9;# after 1<sup>st</sup> element
                - $\{stringZ:1:3\}&#9;== “bcd” # three characters after 1<sup>st</sup> character
    - Substitution
        - $\{var/pat/repl\}&#9;# replace first match
        - $\{var//pat/repl\}&#9;# replace all matches
        - $\{var/#pat/repl\}&#9;# replace if match at start
        - $\{var/%pat/repl\}&#9;# replace if match at end
    - case modification
        - $\{var^^\}&#9;&#9;# uppercase entire string
        - $\{var,,\}&#9;&#9;# lowercase entire string
- Pattern removal (important for filenames/paths)
    - globbing (pattern matching) patterns: \*, ?, …&#9;different from Regex
    - Remove from front
        - $\{var#pattern\}&#9;# remove shortest match from front
        - $\{var##pattern\}&#9;# remove longest match from front
            - $\{parameter#word\}, $\{parameter##word\}
            - word is expanded to produce a pattern and then matches
            - when the beginning part is matched
            - # shortest cut left side
            - ## longest
        - e.g.
            - file=”geometris/H2p\_001.fdf”
            - ` echo ${file#*/}	# remove up to 1st / `
            - ` echo ${file##*/}	# remove up to last / `
        - e.g.2
            - test=[J.H.Park@chi.kaist.ac.kr](<mailto:J.H.Park@chi.kaist.ac.kr>)
            - ` echo ${test#*.} `
                - [H.Park@chi.kaist.ac.kr](<mailto:H.Park@chi.kaist.ac.kr>)
            - ` echo ${test##*.} `
                - kr
    - remove from back
        - $\{var%pattern\}&#9;# remove shortest match from bach
        - $\{var%%pattern\}&#9;# remove longest match from bach
            - when trailing part is matched
            - % shortest cut right side
            - %% longest
        - e.g.
            - file="geometris/H2p\_001.fdf"
            - ` echo ${file%.*}	# shortest back removal to ‘.’ `
            - ` echo ${file%%.*}	# longest back removal to ‘.’ `
        - e.g.2
            - ` echo ${test%.*} `
                - [J.H.Park@chi.kaist.ac](<mailto:J.H.Park@chi.kaist.ac>)
            - ` echo ${test%%.*} `
    - common file operation
        - file=’geometries/H2p\_001.fdf’
        - basename=$\{file##\*/\}&#9;# H2p\_001.fdf
        - root=$\{basename%.\*\}&#9;# H2p\_001
        - ext=$\{basename##\*.\}&#9;# fdf
        - dirname=$\{file%/\*\}&#9;&#9;# geometries
- etc
    - $\{var+x\}
        - if var is unset, it is nothing
        - if var is set, it is substituted
        - e.g.
            - if \[ ! -z $\{activate\_ana+x\} \]; then
    - Matching
        - expr match “$string” ‘$substring’
            - $substring is a regular expression

### arguments & getopts

- arguments&#9;&#9;&#9;&#9;&#9;&#9;
    - positional
    - optional
- reference to positional argument
    - $0: program name
    - $1 ~ $9: command line argument
    - $@ all the argument
    - $#: number of arguments
- getopts for optional arguments
    - [https://stackoverflow.com/questions/16483119/an-example-of-how-to-use-getopts-in-bash](<https://stackoverflow.com/questions/16483119/an-example-of-how-to-use-getopts-in-bash>)

### alias

- what is it?
    - shortcut or an abbreviation for a long command
- show
    - alias
        - show all aliases
    - alias abbr
        - show the alias of abbr
- format
    - alias ls=’ls --color=auto’
        - if wants to add an argument, use function
- setup
    - whole system
        - /etc/profile
        - /etc/rc.local
    - user
        - ~/.bashrc

### source vs sh

- source
    - aliased to “.”
    - run script in the present shell
- sh
    - normally redirected to bash
    - open new shell

### PS1 - color

- prompt in bash&#9;&#9;
    - ` PS1='\e[33;1m\u@\h:\e[31m\w\e[0m\$ ' `
        - \\e\[33;1m&#9;: yellow bold
        - \\u@\\h
            - display: joonho@chi
        - \\e\[31m&#9;: red
- bash escape sequence
    - \\u: username
    - \\h: hostname up to the first
    - \\w\\$
        - \\W: basename of the current working directory
        - \\w: the current working directory with $HOME abbreviated with a tilde
- when directory is too long
    - ` export PROMPT_DIRTRIM=num `
        - 2 or 3
- $infocmp
    - special escape sequences depending on terminal
    - ` echo $TERM `
        - xterm
    - infocmp
- color
    - \\e - asci escape character (033)
    - \\e\[x;ym - the beginning of color prompt
        - e.g.
            - \\e\[0;34m
    - \\e\[m – end of color prompt
    - x;y – color code
        - black 0;30 blue 0;34 green 0;32 cyan 0;36 red 0;31 purple 0;35 brown,yellow 0;33
        - replace 0 with 1 for dark color
        - \\e\[nn;na or \\e\[nna
    - e.g.
        - platinum
            - ` export PS1="\e[1;32m\u@\h:\e[m \e[0;34m\w\e[m$ " `

### string

- split
    - $\{string:position:length\}
- concatenate
    - var1=abc
    - var=”$var1”continue
    - ` echo $var  abccontinue `

### array & list

- ` make list `
    - list=( ele1 ele2 ele3 )
    - index = 0 1 2 3 …
    - seq start increasement end
        - list=\` seq 1 10\`
    - ` echo {1..10} `
        - ` echo {1..10..2} `
            - 1 3 5 7 9
    - $(ls -1 $dir)
- dereference && \{\}
    - element
        - use brace \{ \} to refer item
        - ` echo ${list[0]} `
            - list\[0\] elements
        - ` echo $list[0] `
            - \[, 0, \] are also string as a part of variable
    - element with variable
        - $\{list\[$i\]\}
        - iteration with all indices
            - for t in $\{ list\[@\] \}
            - similar to $\{list\[\*\]\}
    - whole list
        - use @, \*
        - $@: expand each element as a separate argument
        - $\*: expand to the arguments merged into one argument
        - $\{list\[\*\]\}
    - to get whole list as default
        - kpoints=( 2 3 4 )
        - kp=$\{@:-$\{kpoints\[\*\]\}\}
- slice
    - $\{A\[@\]:1:2\}
- add element to a list
    - list+=( “newone” “newtwo” )
    - for a in “$\{list\[@\]\}”
        - do
        - ` echo $a `
        - done
- deleting
    - unset list\[1\]
    - delete list all
        - unset list
- check exist in array
- to get a list in script
    - out=( $( python m.py) )
        - will get list from return of m.py
        - ` echo ${out[@]} `
            - ` echo $out will give ${out[0]} only `
        - ` echo ${out[0]} `
        - ` echo ${out[1]} `
    - out=$( python m.py )
        - will fail

### echo, printf, etc

- echo
- exit
- printf
    - printf “%2d %10s\\n” 3 Joonho
    - format
        - %.3f
        - %02d
    - string
        - %20s
        - %-20s&#9;&#9;! left align

### arithmetic

- expr, let, bc
- scope
    - arithmetic
    - logic
    - relation
    - string
- general rule
    - space between operator and
        - otherwise 5+1 is string
    - special character for expr
        - \* for all
        - & for bg
        - \| for pipe
        - \>, \< for redirection
        - (, ) for grouping
        - escape for special character: \\
- e.g. sum
    - expr 1 + 1
    - var = $(expr 1 + 1)
- operator
    - +, -, /, \\\*
- let
    - ` echo $var		# 6 `
    - let var\_=1&#9;&#9;# 7
- two other types for evaluation
    - $((     )) or $\[     \]
        - $((var+2))
        - $\[var+2\]
    - back quotation: \`      \`
        - c=\`$a + $b\`
        - c=$(( $a + $b ))
    - e.g.
        - expr 138 / (3 \\\* 2) cannot use ( )
        - ` echo $((138 / (3 * 2)) `
- bc
    - ` echo “2/3” | bc `
    - ` echo “scale=2; 2/3” | bc 	# for float `
    - npar=$(echo “sqrt(16)” \| bc)

### return and output

- output
    - true is 1
    - false is 0
- return
    - true is 0
    - false is 1

### if, &&, \|\|

- logical operator
    - three types
        - file&#9;&#9;&#9;! part of unary
        - numeric&#9;&#9;cf. relational op
        - non-numeric
    - returns as test command \[ \]
        - 0 if the condition is met
        - 1 if the condition is false
        - if \[ $a \]  tested as string
            - a=0&#9; true
            - a=1&#9; true
            - a=””&#9; false
- syntax
    - binary operator
        - if \[ arg1 op arg2 \]; then
            - command
        - else
            - command
        - fi
        - explanation
            - \[ \] is test command
            - 1 line expression
                - if \[ $i -eq 1\]; then echo “true”; else echo “false”; fi
            - e.g.
                - if \[ condition \]; then
                    - ` echo “We found $file” `
                - elif \[ condition \]; then
                    - pass
                - else
                    - ` echo “W can’t find $file” `
                - fi
    - in case logical operator
        - if \[\[ arg1 op arg2 \]\]; then list
    - command in condition&#9;&#9;if\_grep
        - do not use ‘\[  \]’
        - if grep -q “$tag” $file ; then
            - blabla
            - fi
- conditions
    - single value
        - \[ $? -eq 0 \]&#9;&#9;for succeed
        - if $? have value, it is always true
            - if \[ $? \] is true even though $?==0
            - $? = 0 or 1 is true always
            - $i = 0 or 1 is true always in if \[$i \]
        - i=&#9;&#9;no value
            - if \[$i \] is false
- file operator
    - -e
        - only FILE exists
        - -a: same but deprecated
    - -f
        - FILE exists and a regular file not directory
        - to use file size cf stat
            - if \[ (( $FILESIZE \> MAXSIZE )) \]; then
    - -d
        - FILE exists and is directory
    - -r –w -x
        - file has read, write, execution permission
    - e.g. 1
        - if \[ $# -eq 0 \]; then
            - ` echo “Missing options!” `
            - ` echo “(run $0 -h for help)” `
            - ` echo “” `
            - exit 0
        - fi
- string comparison
    - Always use \[\[ … \]\] instead of \[ … \]
        - \[\[ “$a” == “$b” \]\]
        - Always quoting variables
    - -z “string”
        - if length of the string is zero, it is true
            - this is effective only when string is defined
                - if not, error: unary operator requires operand
        - \[ -z “$\{var+x\}” \]
            - if var is unset, it is true
    - -n string
        - length of the string is non-zero, non-empty
        - If \[ -n “$1” \] &#9;&#9;: == if \[ ! –n “$1” \]
            - There should be quotation mark
        - this is default, then
            - if \[ $a \]
        - \[ -n “$v” \] for non-empty
        - \[ -n “$\{v+x\}” \]&#9;for defined
        - \[ $v \] is risky
    - e.g.
        - if \[ $ECHO == “true”\]; then
            - ` echo “Hello World” `
        - fi
- other unary op
    - !
        - reverse the evaluation of the expression
- relational
    - integer
        - -eq, -ne, -gt, -ge, -lt, -le, \<, \<=, \>, \>=
        - In the double parenthesis, all are as usual
            - ? $((“a” \<, \<=, \>, \>= “b”))
    - string
        - =, ==, !=, \<, \>, -z, -n
        - = (==), !=, \<, \> (askii order)
- logical operator
    - rule of thumb
        - -a, -o inside bracket - deprecated
        - &&, \|\| outside bracket
            - \[  \] && \[  \] : is ok
            - \[  \]  \|\|  \[  \]
    - shell operator: &&, \|\|
        - to combine the results of two commands
    - \[ \] (== test)
        - usage
            - if \[ expr \];
            - if test expr
        - regular command called test
        - uses -o, -a for and, or operators
        - it can’t use &&, \|\|
    - \[\[  \]\] (shell op not test)
        - fancier test shell syntax
            - should have space before and after ‘\[\[‘ and ‘\]\]’
        - can access to regex, wildcards, ( )
        - can use shell op. such as &&, \|\|, \<, \> inside the brackets
        - e.g.
            - \[\[ $foo == 5 && $bar == 6 \]\]  not working, sometimes working
                - if  \[\[ $(grep -ic NCORE INCAR) -eq 0  &&  $(grep -ic NPAR INCAR) -ne 0 \]\]  ; then
            - \[ \[ $h == ‘stable’ \]\] \|\| \[\[ $h == ‘int’ \]\]; then
            - In the double bracket \[\[ condition1 &&, \|\| condition2 \]\]
        - \[ expr1 -a expr2 \] → \[ expr1 \] && \[ expr2 \]
    - e.g.
        - \{ \} requires a complete command before them
        - if \{ \[ expr1 \] \|\| \[ expr2 \]; \} && \[ expr3 \]; then …
        - if \[\[ ( expr1 \|\| expr2 ) && expr 3 \]\]; then

### case

- usage
    - case expression in
        - case1)
            - sentences
            - ;;&#9;# act as break
        - case2)
            - …
        - \*)&#9;&#9;&#9;! for others
            - ;;
        - esac
- e.g.
    - case $job in
        - “vasp”)
            - ` ssh $node ps aux | grep $job `
            - ;;
        - “ls”)
            - ` ssh $node $job $dir `
            - ;;
        - esac

### shift & set

### matching

- match with RE&#9;&#9;cf. regular expression
    - \[\[ $data =~ re \]\]&#9;&#9;cf. \[  \] for test
    - if string contains numbers
        - if \[\[ $VAR =~ \[0-9\] \]\]; then
        - re=’^\[0-9\]+$’
        - if \[\[ $data =~ re \]\]
- match with substring
    - if \[\[ $string == \*”sub str”\* \]\]; then
        - negative: !=
    - if \[\[ $string =~ “sub str” \]\]; then
        - negative
            - if \[\[ ! “abc” =~ “d” \]\]; then
- whether a string in a list
    - e.g. 1
        - case $j in “A”) bla bla … \*)
            - ` echo “$j is not in ${job[@]} list” `
            - exit
    - e.g. 2
        - word\_list=”one two three”
        - match=”two”
        - if echo $word\_list \| grep -w $match \> /dev/null; then
            - command
            - exit 1
            - fi

### loop: for, while

- for   ;do …  ;done
    - several type for for-loop
        - one line expression
            - for x in \*.dat; do echo $x; done
            - for x in \*.dat
                - do
                    - ` echo $x `
                - done
        - for file in \*.txt
            - for file in file1 file2 file3
            - for file in /qcfs/joonho/vasp
            - ` FILES=”$@” `
                - For f in $FIELS
                - List of files
        - for x in 1 2 3 4 5 .. N
            - for I in \{ 1..5 \}
            - for I in \{0..10..2\}
            - for I in $(seq 1 $end)
                - to use variable in sequence
        - scan array
            - for x in “$\{array\[@\]\}”
        - for output in $( linux commander )
        - for (( exp1; exp2; exp3 ))
            - for (( c=1; c\<=5; c++ ))
            - infinite loop
                - for ((  ;  ;  ))
    - read directory
        - for f in $(pwd)/\*; do
            - fname=$(basename -- “$f”)&#9;# returns file name
            - ext=”$\{fname##\*.\}”&#9;&#9;# string cut with . of delimiter
    - Read line of file
        - $(  )
            - For line in $(cat filename)
    - break loop
        - break
- while
    - using condition
        - \[…\] do … done
        - while \[ condition \]
            - do
                - …
            - done
        - For ksh shell
            - While \[\[ condition \]\]; do … done
    - using commands
        - while getopts “he” OPTION; do
            - case $OPTION in
                - e)
                    - ` ECHO=”true” `
                    - ;;
                - h)
                    - ` echo “Usage:” `
                    - ` echo “$0 -h” `
                    - ` echo “$0 -e” `
                    - ` echo “    	-e	to execute echo \”hello world\”” `
                    - ` echo “	-h	help sentence” `
                    - ;;
            - esac
            - done
    - using commands 2
        - while read line
            - do
            - …
            - done
    - break
        - while :
            - do
                - if \[   \]; then
                    - break
                - fi
            - done

### Function

- General
    - Function should come before calling
- Function declaration format
    - function\_name ( ) \{  commands   \}&#9;# in several lines
        - function\_name ( ) \{  commands ;  \}&#9;# in one line
    - using reserved word function
        - function function\_name \{    \}&#9;# ( ) is optional
        - function f\_name \{ commands; \}
- Call function
    - Function\_name $arg1 $arg2
    - arguments
        - $0: filename
        - $1 $2 …: arguments ($args1 $arg2 etc) in function call
        - $#: number of args
        - $\*\|$@: list
        - “$@”: expand the list to separate strings such as “$1”, “$2”, etc
        - “$\*”: expand the list to a single string with separating space such as “$1 $2”
- to check a function defined
    - $bash --debugger
    - $declare -F \<function\_name\>&#9;# show sourcefile  not working
    - $declare -f \<function\_name\>&#9;# show contents
- other options
    - unset \<function\_name\>
        - free up a namespace in the current terminal
- advanced
    - ` export function `
        - to use function in bash script, export
            - ` export -f <function_name> `
    - ` make watch runs function and make watch function 	cf watch_function `
- E.g.
    - simple function 1
        - hello () \{ echo Hello world! \}
        - hello
    - command: ls -al dir \| wc -l
        - in alias.sh
            - function wl \{ ls -al $1 \| wc -l \}
        - wl dir/loose
            - runs the command
    - containsElement ( ) : check if the array contains element

### subcommand

- two methods for subcommand
    - back quote: \`    \`
    - $( … )
- e.g.
    - execution of shell command in script
        - \`hostname\`
        - $(pwd)
    - output=$( ./my\_script.sh )
        - store the output of command

### read from command line

- read var
    - get input from terminal
    - saved in $var
    - ` echo $var `
- read -p “print output here \[y/n\]?” x y
    - gets two values

### error

- syntax error: unexpected end of file
    - when use dos format
        - use dos2unix
            - dos2ux file1 \> file2
    - mismatched structure
        - if or for structure mistake
            - check couple for if-fi and for do-done

### Error

- “Unary operator expected” error
- Empty variables:   str=
- If \[ $str = “” \]; then
- Shell reads “ if \[  = “”\] “ so there is one item and it should be a unary op. rather than “=”, binary op.

### Basic

- #&#9; comment
- Exception: #!&#9;Sha-bang
- ;&#9;command separator
- If \[ -z $tmp \]; then&#9;&#9;# note space after ;
- ;;&#9;terminator in case option
- \`command\`&#9;&#9;back quotes is command substitution,
- assign output of command to variable
- :&#9;&#9;null command, NOP (no operation, do-nothing operation)
- Equal to true
- If \[condition\]; then : ; else some-actions; fi

### Arguments and list

- Arguments
    - $@&#9;: all the arguments – all the elements of the list of arguments
    - $0 &#9;: name of script
    - $1&#9;: first argument
    - $2&#9;: second argument
    - $#: the number of elements of a list
        - # gives number of elements by skipping the empty slot
    - $?var: is $var is defined?
- list
    - var\[XX\]=yy
    - area\[11\]=23
    - area\[13\]=UFOs
    - array members need not be consecutive or contiguous
    - some can be left uninitialized
- Array\_name=( a  bb  zz … )
    - If elements have a blank, then enclose using ‘  ‘
    - Dereference: $\{Array\_name\[0\]\}  “a”
    - Dereference all: $\{Array\_name\[@\]\} or $\{Array\_name\[\*\]\}
        - $\{array\[@\]\} returns the number of elements, not last index
    - Index starts from 0
    - $\{!array\} returns last index
- Dereference – curly brackets are needed
    - Dereference: $\{var\[XX\]\}
        - Use curly bracket, $\{   \}
        - $\{array\[n\]\}&#9;: n-th element
        - $\{#array\}&#9;: length of array\[0\]
        - $\{#array\[@\]\}&#9;: length of array elements
- array=( a b c … )&#9;&#9;&#9;# entire initialization
    - $\{array\[0\]\} == ‘a’; index starts from 0
    - Array=( \[1\]=one \[2\]=two \[30\]=thirty )
- Variable is also array with one component
    - String=abcABC
    - $\{string\[@\]\} == abcABC
    - $\{string\[0\]\} == abcABC
    - $\{string\[1\]\} == not defined
    - $\{#string\[@\]\} == 1&#9;# one element in array “string”
- “declare –a var=(‘   ‘ ‘     ‘ ‘     ‘)”&#9;: for entire array
- Addition
    - Copy
        - Array2=( “$\{Array\_name\[@\]\}” )&#9;
    - Array\_name=( “$\{Array\_name\[@\]\}” “new element” )&#9;! add new element
    - Array\_name\[$\{#array\[\*\]\}\]=”new element”&#9;! in the last index
- Extracting
    - Echo $\{array\[@\]:3:2\}
    - Extract 2 elements from array\[3\]
- Length of array
    - $\{#arrayname\[@\]\}
- Special treat
    - N\_list=$\{#array\_name\[@\]\}&#9;&#9;! @ makes word splitting
- Number (length) of array
    - N\_list=$\{#array\_name\[\*\]\}
- List in the “for” loop
    - For x in \`cat a.list\`
    - For x in $\{array\[@\]\}
    - For x in 1 2 3 4 5

### shift

- whattodo
    - Shift moves array to left
    - delete n arg’s from the left
        - shift n
- more
    - Shift position
        - Reference to position, the following elements shift to left

### set

- can remove n-th argument
- remove 2<sup>nd</sup> argument
    - set -- “$\{@:1:1\}” “\{$@:3\}”
        - $@ sets $1 then $3, …
- remove n-th argument
    - set -- “$\{@:1:n-1\}” “$\{@:n+1\}”
        - $@ becomes from $1 to $n-1, $n+1 to $#

### Tracing shell program

- ` #!/bin/bash –x	# tracing the route of program `
- Setting tracing on a block
- Set –x&#9;&#9;# turn on tracing
- Set +x&#9;&#9;# turn off tracing

### Variable ( \`backquote\`, $(…), $0, $1 … )

- Variable allocation and substitution: cf. scope of variable, export
- No space in both sides of “=”
- ` A=value `
- ` A =value	: “A” commander has argument of =value `
- ` A= value	: run value as commander with environmental variable A as “” `
- Space character preservation
- hello=”a b  c   d”
- ` echo $hello		: a b c d, there is word splitting `
- ` echo “$hello” 	: a b  c   d, there is not word splitting `
- Manipulating
- $\{parameter\} is same as $parameter
- Your\_id=$\{User\}-on-$\{HOSTNAME\}
- Default
- $\{parameter-default\}, $\{parameter:-default\}
- $\{parameter=default\}, $\{parameter:=default\}
- $\{parameter?err\_msg\}, $\{parameter:?err\_msg\}
- tmp=”default”
- Default=$\{1:-$tmp\}
- Dereference
- var=ten
- ten=10
- as function argument, func $\{!var\}
- var can be dereferenced by $\{!var\} -\> $ten
- array
- $\{#variable\}=length of $variable
- command substitution invokes subshell
- backquotes or backticks
- a=\`echo Hello!\`
- a=\`ls –l\`
- $(…) superseded backticks
- ` R=$(cat /etc/redhat-release) `
- Arch=$(uname –m)
- Nesting
- Word\_count=$( wc –w $(echo \* \| awk ‘\{print $8\}’) )
- Positional variable
- $0: script itself
- $1,…$n: arguments of the script
- Important variable
- SHELL
- PATH
- HOSTNAME

### Quoting

- All the special character are preserved except $, \`, \\
- “$a  “: changed to the value
- Escape word splitting
- $a=”a b c d”
- Command $a&#9;: four argument
- Command “$a” &#9;: one argument
- $a=””
- Command $a $a $a&#9;: no argument
- Command “$a” “$a” “$a”&#9;: three blank arguments
- Command “$a $a $a”&#9;&#9;: one blank argument
- Echo does not need quotation
- Use when word splitting makes problem
- If

### Operator

- =~: Matching operator
- $var =~ \[“yes”\| y\* \| \]
- Set string = yesterday
    - $string =~ yes&#9;: false
        - $string =~ yesterday : true

### Command line argument

- Special variable, $
- $# - total number of arguments
- $\* - all the contents in the argument line
- $$ - process ID after the shell program runs
- $0 – script name
- Shift
- Remove the first argument in $\*
- Shift
- $1  $2, $2  $3, etc
- $1 disappears
- $0 (script name) does not disappear

### If test-command

- Usage
    - If test-commands; then commands; fi
    - Test-commands
        - Test-commands are executed and if the return status is zero, it is true
    - Return status is the exit status of the last command executed or 0 if no condition tested
- Return status:
    - 0 : if it succeeds then ‘if’ is true
    - 1 : if it fails
    - Test-command can be any if it returns a status of zero when it succeed, or some other values when it fails
- E.g.
    - If \[ 3 –gt 2 \]; then echo “It is true”; fi
    - \[ test-command \] gives 0 of success then it is true
    - \[ STRING \], \[ 0 \], \[ 1 \] are true with return status of 0
    - If command&#9;&#9;&#9;&#9;&#9;cf. if grep, grep exec
        - if grep ‘ISIF = 3’ INCAR ; then echo “…”; fi
            - ` grep is executed and print out and it’s true with 0 `
        - If \`grep ‘ISIF = 3’ INCAR\` ; then echo “…”; fi
    - There is no command in if
        - If \[ grep ‘ISIF = 3’ INCAR \] ; then echo “…”; fi
            - Missing \]
    - If \[ \`grep ‘ISIF = 3’ INCAR\` \] ; then echo “…”; fi
        - Too many argument in if after \`   \` execution
    - If \[ \`grep ‘ISIF = 3’ INCAR\|wc -l\` \] ; then echo “…”; fi
        - \[  \] has only number and print only echo “…”

### Arithmetic operation

- $((expression))
- $((n1+n2))
- +, /, -, \*, %, (++, --: post or pre increment such as x++, ++x) \*\*,

### While loop

- From condition
- While \[ condition \]; do                  ;done
- From text file
    - While IFS= read –r line&#9;: IFS for field separator (default: white space) -r disables backslash escaping
        - Do
        - Commander
        - Done \< “/path/to/file”

### Read

- Read answer&#9;&#9;: from std input, read one line, save answer
- Read first second&#9;: save first word in “first” and the others in “second”
- Read –p prompt&#9;: output prompt and receive input
- Read –p “Enter two number: “ x y
- Read –r line&#9;&#9;: \\ is available in input

### Exit

- Returns value available to parent process
- Success returns 0 and fail returns non-zero error code: 1 ~ 225
- Exit number
- as for previous command
    - if \[ $? \] becomes true though $?==0

## shell variables

### IFS

- internal field separator
    - how to do word splitting
- e.g.
    - ` IFS=$’ \t\n’ `
        - ifs is white space, tab, new line
    - mystring=”foo:bar baz rab”
    - for word in $mystring; do
        - ` echo “Word: $word” `
        - done
    - output
        - Word: foo:bar
        - Word: baz
        - Word: rab

## special shell command

### sed – stream editor

- properties
    - read one line and treat it
        - so does not use buffer, just one line
        - If it makes a substitution, the new text is printed instead of the old one
    - delimiter
        - any delimiter can be used with triple if it is not included in the argument. Cf. szoldznewz
    - variables
        - ‘/’$\{dir\_n\}’/’
        - “/$dirn/”
    - Format
        - s/pattern/replacement/
        - /address/ s/pattern/replacement/
            - Where to apply a command – not just what to do
- sub-command prefix
    - s/
        - substitution
        - ` sed ‘s/address/address/’ list.txt `
        - ` sed ‘s/old/new/’ inputfile `
        - ` sed ‘s/old/new/’  inputfile > outputfile `
            - to save to another file
        - ` sed ‘s/  */ /’ list.txt `
            - change several blank into one blank
        - to change the whole line
            - ` sed ‘s/.*MAGMOM.*/magmom = 10*3/’ `
                - .\*: any character with infinite repetition
        - confine range
            - ` sed ‘3,7s/abc/def/g’ `
    - address + s/
        - '/^\[\[:space:\]\]\*NCORE/s/^/#/'
        - \[:space:\]
            - POSIX character, 0 or more whitespace character cf. RegEx
- sub-command suffix
    - /d, /!d
        - delete
        - ` sed ‘/TD/d’ 1.html	! line with ‘TD’ is deleted `
            - ` sed ‘/td/I d’	! case insensitive deletion of line `
        - ` sed ‘/TD/!d’ 1.html	! line with ‘TD’ survives `
        - ` sed ‘1,2d’ 1.html	! 1, 2nd lines are deleted `
            - ` sed ‘7d;12d;16d’ input	# delete multiple lines `
            - ` sed ‘5,8d’ input		# delete from 5 to 8 `
        - ` sed ‘/^$/d’ 1.html	! empty line is deleted `
            - RE: ^  start of line, $  end of line
        - ` sed ‘/1990/, /1990/d’ input	# delete start line with 1990 to that of 1990 `
        - ` sed ‘/^[[:digit:]]/d’	# line starts with digit `
        - ` sed ‘/[string]$/d’	# line ends with [string] `
    - /a
        - append
        - ` sed -e “/NPAR/a NCORE = 20” `
            - append “NCORE = 20” below NPAR line
    - /g for recursive
        - to delete a string, use ‘s/string//g’
    - /p for print
        - ` echo abc | sed ‘/a/p’ `
- symbols
    - $: last line
        - ` sed ‘$d’ input  deletes last line `
- option
    - -e
        - if multiple style, use several -e
        - qstat –f \| sed ‘/---/d’ \| sed ‘s\|0\\/\|\|’ \| sed ‘s\|resv\\/\|\|’&#9;cf. qstat\_sed
            - delete is line delete
            - s is substitution
            - equivalent to
                - qstat –f \| sed –e ‘/---/d’ –e ‘s\|0\\/\|\|’ -e ‘s\|resv\\/\|\|’
    - -n: do not print
        - ` sed –n ‘/abd/p’ list.txt `
            - ‘-n’ do not print but print with /p
            - just print /abd/ line
        - ` sed –n ‘1,10 p’ infile `
            - prints from 1 to 10 line numbers
            - ` sed -n -e ’41,540p’ H.ion > H_pot.txt `
    - -i, --in-place
        - for substitute in place of input file
        - ` sed -i ‘s/old/new/’ inputfile1 `
            - ` sed -i ‘s/old/new/’ *	# for all the files in the directory `
            - cf. find file and modify
- etc
    - ` sed -i -e ‘s/old/new/’ inputfile	# modifies inputfile `
        - -e for multiple arguments
- Other flags
    - /g&#9;for global exchange
        - ` sed change only the first matched word by default `

### awk

- whatitis
    - manipulate data
    - made by Alfred Aho, Peter Weinberger, Brian Kernighan
    - in the unit of field,
- contents
    - pattern
    - if-condition
    - BEGIN-END
    - awk-variable
- howtouse
    - CLI
        - basic syntax
            - ` awk ‘pattern’ filename `
            - ` awk ‘{action}’ filename `
            - ` awk ‘pattern {action}’ filename `
                - action such as print needs ‘\{  \}’
            - ` awk ‘pattern {action}’ filename > outputfile `
        - ` awk -f program -F separator /pattern/ ‘{action}’ input_file `
            - ` awk -F : “{print $1, $6}” ./text.txt `
            - read text.txt, separate record using :, print 1<sup>st</sup> and 6<sup>th</sup> field
            - -v for variable
                - ` awk –v file=$1 … `
                    - can use bash script input argument in the awk sentence
            - -f awk\_program\_file
                - ` awk command sentence can be written in a file `
                - ` awk -f awk-file infile `
            - -F field\_separator
        - BEGIN
            - execute action before read 1<sup>st</sup> record
        - END
            - execute action after read last record
            - e.g.
                - ` awk ‘ … ‘ infile `
                - ` awk ‘BEGIN{ …  } {  …  } END{ … }’ infile	# initial condition, loop, final sentence `
                - sentence is ended by semicolon
                    - ` awk ‘{sum+=$13; i++;} END{print I; print sum/i}’ infile `
            - ` grep file | read one column  average `
                - % bash function
                - function  mdave \{
                - thermo=$1
                - fin=$2
                - if \[ $thermo == 'T' \]; then
                - ` grep F= $fin | awk 'BEGIN{i=0; sum=0; ncount=0} { i++; if(i > 1000) { sum +=  $3; print $3; ncount++; } } END {print ncount, sum, sum/ncount}' `
                - fi
                - \}
            - cli
                - mdave T d201559j.log
    - in bash script
        - ` awk ‘ `
        - BEGIN \{            ;            \}
        - \{
        - #&#9;&#9;comment
            - if (   ) \{
                - print&#9;&#9;# print record (line)
                - next
                - \}
            - if ( ) \{   \} &#9;&#9;# many if-sentence
- pattern
    - execute pattern per each input record
    - /pattern/ uses RE
    - only /pattern/
        - print the line with the pattern
            - ` awk ‘/pattern/’ fname `
            - pattern is written by /   /
    - only action
        - all the records are object of action
            - ` awk ‘{action}’ fname `
            - to run calculation irrespective to record, use BEGIN
    - ` awk ‘/pattern/ {action}’ fname `
    - ` awk ‘/pattern/ {action}’ fname > outf `
        - to rewrite inputf in script
            - ` awk ‘      ‘ inputf > outf && mv outf inputf `
    - ` awk ‘condition’ input `
        - df \| awk ‘$4 \< 1000000’
            - if $4 \< 1000000, the line is printed
- ` awk variable `
    - $n is field variable
        - of the current input line, split by the field separator (default: white spaces)
        - E.g.
            - Fe 26 metal
            - $1 = ‘Fe’
            - $2 = ‘26’
            - $3 = ’metal’
            - $0 -whole line
            - $n - n-th field
        - length – number of letters
    - associative array: like dictionary
        - a\[$1\]: an array element
            - $1 is key in string or word in $1
        - Can assign value in a\[$1\]
            - a\[“Fe”\] = 1
            - a\[“Fe”\]++
- definition and ENV VARIABLE
    - FILENAME
        - present fine name
    - RS
        - record separator: default=”\\n”
            - So, every line is record
            - through file or pipe, input line is recorded in $0, separated by “\\n”
            - $0 line is devided by white space into fields, which counts from $1 to $100
    - NR
        - present index of record, not total number of records
        - NR&#9;- number of records, starts from 1
            - FNR counts from 1 for each file in case several file input
    - FS
        - field separator: blank and tab
            - ` awk -F : ‘/Park/{print $1, $2}’ infile `
            - -F ’\[ :\\t\]’
                - FS is blank, : and \\t
    - NF
        - number of fields
            - field: each divided part
    - OFS, ORS
        - FS in output
        - RS in output
    - print
        - ` awk uses print-function to print output into screen `
        - , (comma) is mapped into OFS (output field separator) of blank
    - dereference for variable
        - I not $i
    - variable assignment
        - var=value
        - uname -a \| awk ‘\{hostname=$2; print hostname\}’
- action
    - print whole file
        - ` awk ‘{ print }’ datafile `
            - the same as awk ‘\{ print $0 \}’ datafile
    - find pattern then print the whole line
        - ` awk ‘/west/’ datafile `
        - ` awk ‘/^north/’ datafile `
            - pattern: ^ for the start of the line
            - pattern follows regular expression
    - print field
        - ` awk ‘{ print $3, $2 }’ datafile `
    - find pattern and action (print)
        - ` awk ‘/Park/{print “\tHello? “ $1, $2} infile `
    - print syntax
        - basic format
            - ‘\{ print \}’
        - comma:
            - $1 $2
                - without comma, output is connected
            - $1, $2, “hello”
                - each field is separated by blank
        - formatted print
            - using printf
                - printf “%8s %10d\\n”, $1, $2 ‘
                - modifier
                    - %.2f, %.6g
                    - c for character
                    - d for integer
                    - f for float
                    - - for left filled
                - no \\n so finish with \\n
            - e.g.
                - ` awk '{printf "%5d  %5s  %15.6f   %15.6f   %12.5f\n", $1, $3, $5, $9, $11 }' `
            - OFMT
                - ` awk ‘BEGIN{OFMT=”%.2f”;} `
- string manipulation functions
    - length(str)
    - index(str, search\_str)
        - index($1, “/”)
            - do not use ‘ when awk use ‘ as the master quotation
                - ` awk ‘{ `
    - split(str, array, delimiter)
    - substr(str, start\_ind, end-ind)
        - ` grep "optimization un" NN*/amp-log.txt -B 1 | awk '{ if(NF==11) { print $1, substr($1,1,index($1,"/")-1),$8} }' `
    - sub(regex, rep\_str, str)
    - gsub(regex, rep\_str, str)
        - like sub() but replaces all the position

### awk programming

- basic
    - comment: # following sentence
    - each sentence is finished by ;
    - group of sentences is blocked by \{ \}
        - several sentences
            - \{….;  ….; \}
    - first usage of variable, list, it is Null
        - by ++, it becomes 1
- variable&#9;&#9;&#9;&#9;&#9;&#9;cf. awk contents
    - How to use shell variable
        - xpart=”X1”
        - ` awk -v part=”$xpart” ‘{ print part }’ `
            - N.B.
                - use “ “
                - no “$” in dereference var
- If-else
    - format: awk ‘\{ if( )\{ \} else\{ \} \}’
        - if(condition) \{sentence1; sentence2’… \}
        - else if(condition) \{   \}
        - else \{   \}
    - if statement
        - pattern match: /regexp/
            - if($4 ~ /\\\*/)&#9;! 4<sup>th</sup> column matches with ‘\*’
        - ‘if’ can be omitted
            - ` awk ‘ $0 == ”[ atom ]” {print “yes”}’ bman.top `
                - condition\_sentence followed by \{action\}
            - ` awk ‘{ if($0==”[ atom ]”) {print “yes”}}’ bman.top	! the same `
        - omit \{ \} in if block
            - \{ if(i!=0) \{print $3 ; i++;\} else \{ bla \} \}’
            - \{ if(i!=0) print $3 ; i++; else \{ bla \} \}’&#9;&#9;! the same
    - operator
        - !: negative
    - e.g.
        - ` awk ‘BEGIN { if (!a[‘I’]++) {print a[‘I’]} } ‘ `
            - a\[‘I’\] is Null, !a\[‘I’\] is True
                - \{print \} runs
            - a\[‘I’\]++ =1
            - print 1
        - ` awk ‘BEGIN { if (!++a[‘I’]) {print a[‘I’]} } ‘ `
            - ++a\[‘I’\] =1 before test
            - if is True, !++a\[‘I’\] is False
            - No prints
- control keyword
    - next: control flow mechanism
        - stop processing the current input recorde and move on to the next one
        - skip the
- loop
    - for
        - for (initialization; condition; increment\|decrement) action
        - e.g.
            - ` awk ‘BEGIN { for (I = 0; I <= 5; ++i) print i}’ `
                - without BEGIN, it does not run, why?
                    - BEGIN can be run without record input
        - e.g. 2
            - for (i=1; i\<=NF; i++)
            - words\[$i\]++
                - list: words
        - treat list
            - for (ar in arr) \{ print ar\[1\], ar\[2\]\}
        - e.g. 3 to treat all the fields in a record
            - ‘\{ i=1; while(i\<=NF) \{
    - while
        - while (condition) action
- array
    - associative array
        - index
            - need not to be continuous
            - can be string, number
            - no need to declare size
    - definition
        - a\[var\]
            - a\[var\] becomes Null, then, is not be printed
        - a\[var\]++
            - becomes 1
    - e.g.
        - arr\_name\[index\]=value
        - ` awk ‘BEGIN{a[norm]; print a[norm]; a[norm]++; print a[norm]}’ `
            - ← blank
            - 1
- split in awk
    - split($0, arr, “/”)
        - split $0, input array of arr, using “/”
        - use “ “ for delimiter
        - arr start from arr\[1\], arr\[2\], …

### special technique

- Shell variable to awk
- get variable from awk
    - basic
        - use backticks and $() to put output into a variable
    - case 1
        - function init()\{
            - ` grep $1 `
            - \}
        - myvar=\`init sth\`
        - ` echo $myvar `
    - case 2
        - function init()\{
            - cat $1 \| awk ‘\{printf(“%5d : %s\\n”, NR, $0)\}’
            - \}
        - myvar=$(init sth)
        - ` echo $myvar `
    - eg. 3
        - function get\_total()\{
            - pestat \| grep $1 \| awk '\{ if($4 != $5) sum+=$5-$4\} END \{print sum\}'
            - \}
        - functioni pe()\{
            - for I in ‘seq 1 5\`; do
                - sum=$(get\_total X$i)
                - ` echo “partition X$i: … $sum free” `
    - the above is the same as
        - sum=$( pestat \| grep X$i \| awk '\{ if($4 != $5) sum+=$5-$4\} END \{print sum\}' )

### awk example

- skip first line
    - ` awk ‘ BEGIN { I = 0; } `
        - \{ I++; if (I == 1) \{ bla … \}
        - else \{ … \}
        - \}’
- block treatment
    - ` awk '{if($0=="[ atoms ]") {go=1} if(go){sum+=$7} if($0=="[ bonds ]") {go=0}} END{print sum}' bman.top `
    - ` awk '$0=="[ atoms ]"{go=1} go{print $7; sum+=$7} $0=="[ bonds ]"{go=0} END{print sum}' bman.top `
- treat qstat -f
    - qstat -f \| sed -e '/---/d' -e 's\*0/\*\*' -e 's\*resv/\*\*'
    - qstat -f \| sed -e '/---/d' -e 's\*0/\*\*' -e 's\*resv/\*\*' \| awk '\{if(NR==1)\{printf "%20-s\\t%5s\\t%7s\\t%20s\\t%20s\\t%10s\\n", $1, $2, $3, $4, $5, $6\}else\{split($3,num,"/"); nfree=num\[2\]-num\[1\]; printf "%20-s\\t%5s\\t%7s %3d\\t%20s\\t%20s\\t%10s\\n",$1,$2,$3,nfree,$4,$5,$6\}\}'
    - in bash script, add \\ for “ and $ …
        - alias qstatf="qstat -f \| sed -e '/---/d' -e 's\*0/\*\*' -e 's\*resv/\*\*' \| awk '\{if(NR==1)\{printf \\"%20-s\\t%5s\\t%7s\\t%20s\\t%20s\\t%10s\\n\\",\\$1,\\$2,\\$3,\\$4,\\$5,\\$6\} else \{split(\\$3,num,\\"/\\");nfree=num\[2\]-num\[1\];printf \\"%20-s\\t%5s\\t%7s %3d\\t%20s\\t%20s\\t%10s\\n\\",\\$1,\\$2,\\$3,nfree,\\$4,\\$5,\\$6\}\}'"
- treat consecutive lines in VASP
    - ` awk '$2 <= last {print f} {f=$0; last=$2}'	! basic and important `
        - rule
            - if True, \{print f\} runs
            - 2<sup>nd</sup> \{  \} always run
        - 1<sup>st</sup> NR
            - no value in ‘last’
                - if false, does not run \{print f\}
                - if yes, nothing to print in ‘f’
            - second \{ \}
                - f saves 1<sup>st</sup> NR
                - ‘last’ saves 2<sup>nd</sup> field of 1<sup>st</sup> NR
        - 2<sup>nd</sup> NR
            - $2 fields compared with ‘last’=$2 of the 1<sup>st</sup> NR
            - if True, print 1<sup>st</sup> NR
            - f and last are set in 2<sup>nd</sup> NR
                - then compared in the next 3<sup>rd</sup> NR
    - more complicate manner
        - ` grep F= *out | shows multi lines, then, select a certain line `
        - re0\_450s.out:   1 F= -.18272354E+02 E0= -.18272354E+02  d E =-.182724E+02
        - re0\_450s.out:   2 F= -.18262868E+02 E0= -.18262868E+02  d E =0.948644E-02
        - re0\_450s.out:   3 F= -.18278677E+02 E0= -.18278677E+02  d E =-.632217E-02
        - re0\_450s.out:   4 F= -.18278678E+02 E0= -.18278678E+02  d E =-.632321E-02
        - re0\_500s.out:   1 F= -.18271150E+02 E0= -.18271150E+02  d E =-.182711E+02
        - re0\_500s.out:   2 F= -.18262488E+02 E0= -.18262488E+02  d E =0.866183E-02
        - re0\_500s.out:   3 F= -.18276986E+02 E0= -.18276986E+02  d E =-.583615E-02
        - re0\_500s.out:   4 F= -.18276987E+02 E0= -.18276987E+02  d E =-.583719E-02
        - ` awk '!a[$1]++ {b[++count]=$1} {c[$1]=$0} END { for (i=1;i<=count;i++) { print c[b[i]]}}' `
            - \{b\[++count\]=$1\} runs if !a\[$1\]++ is true
            - \{c\[$1\]=$0\} runs always
            - END runs finish the program
        - ` awk '!a[$1]++ {b[++count]=$1} {c[$1]=$0} END{for(i=1;i<=count;i++) {print b[1]} }' `
            - b\[index=integer\] prints filename&#9;at 1<sup>st</sup> line of new file
            - c\[b\[ind\]\] print the last line of each file
        - thinking
            - whenever new file
                - b\[integer\] has new filename
            - if a\[filename\] is not new
                - c\[filename\] saves whole line at each NR if the same filename
                    - so saves the final line in a file
        - ` awk '!a[$1]++ {b[++count]=$1} {c[$1]=$0} END{print a[$1]}' `
            - ` NR=1 `
                - for no a\[‘file1’\], \{ \} is executed
                    - b\[1\] = ‘file1’
                    - a\[‘file1’\]=1
                - \{c…\} is always executed
                    - c\[file1\] saves whole line
            - ` NR=2 `
                - a\[file1\] exists, so condition is fault
                    - a\[‘file1’\] = 2
                    - \{b..\} does not run
                    - c\[file1\] is overwritten by the present record
            - ` NR=5 `
                - a\[‘file2’\]=1
            - NR…
                - a\[‘file2’\] increasing
            - END
                - a\[‘file2’\] will be final number
        - ` awk ‘a[$1]++ {b[++count]=$1; print a[$1]}’		! 1st try `
            - ` NR=1 `
                - a\[‘re0\_450s.out’\] = Null; at initialization
                - a\[‘re0\_450s.out’\] is condition test
                    - does not exist, so, \{ \} is not executed at NR=1
                - a\[‘re0\_450s.out’\] = 1; by ++ after conditional test
            - ` NR=2 `
                - a\[‘re0\_450s.out’\] (=1) exists, so \{ \} is executed
                - count=Null at definition
                    - but becomes 1 by ++count
                - b\[1\]=‘re0\_450s.out’
- treat two separated line
    - input from “$ more job.remdk”
        - remdk
        - start
        - Mon Nov 25 14:01:40 KST 2019
        - end
        - Mon Nov 25 16:25:04 KST 2019
    - get two lines
        - more job.remdk \| awk '\{ if($4) \{ print $4\} \}’
            - Mon Nov 25 14:01:40 KST 2019
            - Mon Nov 25 16:25:04 KST 2019
    - calculate time lap
        - more job.remdk \| awk '\{ if($4) \{ split($4,arr,":"); print arr\[1\]-hour, arr\[2\]-min;\}     \{ hour = arr\[1\]; min=arr\[2\];\}  \}'
            - if FALSE
                - hour=0, min = 0
            - if TRUE
                - split($4,arr,”:”)
                    - 14 01 40
                    - print 14 1
                - hour=14, min=01
            - if FALSE
                - still arr\[1\]=14, arr\[2\]=01
            - if TRUE
                - split into 16 25 04
                - print 16-14, 25-01

### gawk

- In linux, awk is symbolically linked to gawk

### xargs

- usage
    - pass results of the preivous command through pipe ‘\|’ to the next command as arguments
- default
    - args go to the end
    - ls \| grep “\\.bak$” \| xargs rm
        - ls, select files with ends of .bak then remove
- define the args’ location in cp/mv: -I or iI, i is working while l is not
    - ls \| grep “\\.bak$” \| xargs -i\{\} cp \{\} ./bak\_files
        - N.B.: no space between -i and \{\}
        - args is obtained by \{\} through -i
        - it is used at \{\} location
        - any string can be used instead of \{\}
            - xargs -IFILE cp FILE ./bak\_files
    - (deprecated) -i
        - xargs -i cp \{\} ./bak\_files
            - \{ \} is default
    - mv
        - ls ldos\*dat \| grep V -v \| xargs -l\{\} mv \{\} ./Dat
    - working?
        - ls \*.log \| xargs -i mv \{\} \{\}\_bkp
- E.G.
    - find file and head -1
        - find . -name “test\_force\_stat.dat” \| xargs head -1&#9;cf. for AMP
    - with diff and cp
        - diff . ../../Sol/Dout/Geo \| grep “Only in .” \| awk ‘\{print $4\}’ \| xargs cp –t ../../Sol
    - ` grep w/ and w/o xargs `
        - ls \*.tmp \| grep “echo”
            - find echo in the \*.tmp filenames
        - ls \*.tmp \| xargs grep “echo”
            - find echo in the contents of the \*.tmp file
    - multiple grep with find
        - find . -name INCAR \| xargs grep IMAGES \| grep -v “#IMAGES”
        - including sed to modify files with str
            - find/exec
            - grep/xargs
    - multi line to single line
        - ls -1 \| xargs
    - find a line and execute another command
        - qstat -u $USER \| awk '\{ if($4 ~ /\\\*/) \{print $1\} \}'
            - in case jobname is long, \* appears in jobname at 4<sup>th</sup>-column
        - qstat -u $USER \| awk '\{ if($4 ~ /\\\*/) \{print $1\} \}' \| xargs -i\{\} qstat -f \{\} \| grep Job\_Name
            - print Job\_ID and pass to xarg, then, qstat -f Job\_ID shows Job fullname
        - at shell script
            - alias qsj="qstat -u $USER \| awk '\{ if( \\$4 ~ /\\\*/) \{print \\$1\} \}' \| xargs -i\{\} qstat -f \{\} \| grep Job\_Name"
- xargs vs -exec
    - exec: when args long, make a problem

## some techniques

### for loop in a line

- rename multiple files
    - bash
        - for File in \*.txt; do mv $File $(echo $File \| sed ‘s/txt/dat/’); done
        - for file in \*mol; do cp $file $(echo $file \| sed 's/.mol/-eda.mol/'); done
    - tcsh
        - there is no tcsh correspondent
        - foreach-end cannot be written in one line

### see the multiple lines in a file

- see grep

## tcsh (tc shell)

### variable set vs setenv

- ` setenv variable value `
    - Usage
        - set is used for current shell and setenv for current and any subshell
        - ` setenv is used for PATH, HOME, etc `
        - by convention, variable is capitalized
    - Environment variable assignment&#9;&#9;&#9;&#9;&#9;&#9;
        - ` setenv var value `
            - ` setenv QC /opt/applic/qcParAug18 `
            - ` setenv PATH $PATH:/dir/path `
            - ` setenv PATH $PATH:/usr/local/appl/bin `
                - the same as
                - set path = (. $path /home/joonho/bin)
            - use double quote for blank
        - preassigned env var
            - HOME, PATH, …
    - see all variables
        - setenv, env, printenv
    - see one variable
        - ` echo $tty 	: to see one variable `
        - printf “%s\\n” $tty&#9;: to see one variable
    - unsetenv environment variable
        - ` echo $var                 : empty `
- set var = val
    - by convention, the variable is not capitalized
    - set var = value
        - there are spaces around “ = “
        - value is character string
            - set aa = hello
            - set bb = ‘Hello world’
            - set outputfile = ~/csc319/out.txt
        - value is a list of text strings
            - set name = (val1 val2 val3)
    - dereferencing
        - $name
        - $\{name\}
        - set aa = “$aa my friend” &#9;# “ “ expand the variable into value
        - concatenation
            - set name=prepend\_value$\{name\}
            - set name=$\{name\}append\_value
        - preassigned shell variable
            - user, term, home, path
            - if these are changed, the corresponding env is also changed
    - display all the variables
        - set
    - see one variable
        - ` echo $var `
        - ` echo $name[n]		# when name = (  ) `
    - mistake
        - set var
            - var has empty value
    - unset bb
        - equivalent to
            - set bb
            - set bb = ‘’
- path vs PATH
    - set var = (  ) vs setenv VAR bla…
        - normally different
    - exceptions
        - path and PATH are same
- set var from command

### alias

- e.g.
    - Alias ls “ls –a”
        - Alias ls
    - ` source .tcshrc `
        - this adds $LD\_LIBRARY\_PATH, $path so, sometimes later, exit the terminal
            - “Word too long” error when $LD\_LIBRARY\_PATH is too long arguments
        - Error
            - If there is one error in initial files, it stops there.
    - Tcsh problem
        - Problem in source
        - Source .tcshrc.psi.env
            - /: No such file or directory
            - There is non-available file for source in “.tcshrc.psi.env”

### escape ‘ ‘

- use single quote for escape
    - ` echo ‘Usage:: qsub -N jobname -v np=np $SB/pypbs/sge_vasp.csh' `
        - if you use double quote, $SB will be tried to be replaced

### prompt

- set prompt = “…”
    - ` setenv PROMPT ‘%m%# ‘ `
- e.g.
    - set prompt = ”%\{\\033\[0;33m%\}%n@%m:%\{\\033\[0;31m%\}\[%/\]%\{\\033\[0;37m%\}% %\{\\033\[0m%\}”
    - joonho@kdft:\[/home/joonho\]%
    - In Kim
        - set prompt = "%B%\{\\033\[34m%\}%d %D.%w.%Y %P%\{\\033\[0;37m%\} \[%\{\\033\[1;33m%\}%n%\{\\033\[0;37m%\}\]\[%\{\\033\[1;33m%\}%m%\{\\033\[0;37m%\}\]\[%\{\\033\[1;33m%\}%~%\{\\033\[0;37m%\}\]%\{\\033\[30m%\}%b%\{\\033\[1;36m%\}%#%\{\\033\[0;37m%\} "
- analysis
    - color
        - ”%\{\\033\[0;33m%\}
    - formatting sequence
        - %m: expanded to hostname of server
        - %#: equal to ‘\>’
        - %n:&#9;name (id)
        - %/: pwd
        - %~: pwd with home with ~
        - %c: current path
            - \[%n@%m:%c\]%#
- color
    - %\{\\033\[31m%\}%m\{\\033\[0m%\}
        - %\{\\033\[0m%\}: latter part for back to the default color

| 30 | 31 | 32 | 33 | 34 | 35 | 36 | 37 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Black | Red | Green | Yellow | Blue | Magenta | Cyan | white |

- thickness
    - %\{\\033\[1;31m%\}%m\{\\033\[0m%\}

| 0 | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- |
| Normal | Bold | Normal again | Background color | Underline the text | blinking |

### list or array

- usage
    - there is no nested lists
- eg
    - set string = ( yesterday today )
        - $string\[1\] = “yesterday”
- set users = ($user1 bcde2345)
- set $user\[0\] = defg345
    - set numofusers = $#users
    - set users2to4 = “$users\[2-4\]”
    - set allusers = “$users\[\*\]”
    - set lastuser = $users\[$\]
- command line array
    - $0: filename
    - $1, … $9: nine arguments
    - $\*: list of line parameters except $0
    - $#argv: the number of command line arguments

### command

### if ( expr ) then … endif

- usage
    - if ( -f $file ) then
        - ` echo “We found $file” `
        - else if ( … \|\| …) then
        - ` echo “We can’t find $file” `
        - else
        - ` echo $1 `
        - endif
- variable is defined
    - set var = value
    - unset var2
    - ` echo $?var `
        - 1
    - ` echo $?var2 `
        - 0
    - if ( ! $?var2 ) then
        - ` echo “var2 is not defined” `
    - endif
- logic
    - \|\| and &&

### Operator

- Arithmetic calculation
    - Execution: @
        - @’ ‘c=$a’ ‘+’ ‘$b
            - @’ ‘    ‘ ‘+’ ‘
            - @ should have blank, operator should have blanks on both sides
- conditional operators
    - ==&#9;equal to (string)
    - If ( $list =~ y\* ) …&#9;: error,
        - List cannot appear in if-sentence
- set list = (ele1 ele2)

### while, foreach

- while
    - structure
        - while ( condition )
            - do something
            - end
- foreach
    - structure
        - foreach n ( 1 2 3 4 5 )&#9;&#9;! n.b. no “in”
            - commands ($n)
            - end
    - there is no one line expression
        - foreach and end should hold whole line
    - list expression
        - search directory
            - (\*.txt)&#9;
        - Sequence with command of backtick
            - (\`seq 1 1 40\`)

### string

- set string = ‘hello’
- string concatenation
    - set string = “$string $param”

## Shell Command Basic

### bash

- into sub shell
- option
    - -s or no argument
        - input from standard input
        - positional argument is possible
        - e.g.
            - bash –s My name is John
            - ` echo “$1” `
                - My
    - -c
        - read commands from the following string and assign any arguments to the positional parameters
        - e.g.
            - bash –c ‘set a b c d; IFS=”+-;”; echo “$\*”’
- bash in find –exec
    - find envt –type f –exec bash –c ‘ls’ \\;
        - command ls with the number of envt/files

### bzip2

- uncompress
    - bunzip2 bigfile.gz2

### compress file: tar, zip

- tar
- zip
- gzip
- bzip2

### cat

- cat –option filenames
    - display files consecutively
- -b
    - Each line with number
- –n
    - Number including blank line
- –s
    - The consecutive blank line becomes one line

### cd

- change directory
- options
    - ‘’ or ~
        - go to home
    - -
        - go back to the previous directory
    - –P
        - when going into a linked directory
        - -P makes pwd shows the physical path to the directory

### cmp

- compare the two files byte by byte to find out whether the two files are identical or not
- function
    - if different, returns the location of the first mismatch
- syntax
    - cmp file1 file2

### cp

- usage
    - ` cp options source destination `
    - dependence of file system
        - FAT
- ` cp conserving attribute `
    - ` cp –dpR	or -ap	would be similar to tar, rsync `
    - ` cp -urav `
- option
    - -a
        - same  as -dR
    - -r
        - recursive to include subdirectory
    - -p
        - copy the properties: owner, group, authority, time…
        - in case of link file made by “ln -s”
            - copy the linked file as it is
            - if not, copy the original file
    - -u, --update
        - if only source file is new file, copy
    - -av
        - preserve all the attributes
    - –preserve=links
        - preserve attribute
        - is included in -av
- hidden file
    - .\[a-z,A-Z,0\_9\]\*
        - .\* includes ./ and ../, that is present file and parent file
    - ` cp .[a-z,A-Z,0_9]* destination `

### df

### diff

- show difference of two files or directories &#9;&#9;cf. cmp
    - files
        - diff a.txt b.txt
    - directories
        - diff -q dir1 dir2
        - diff -qr dir1 dir2
            - recursive to include subdirectories
        - e.g.
            - diff –r dir1 dir2 \| grep dir1 \| awk ‘\{print $4 \}’ \> difference1.txt
- options
    - -b: disregard blank
    - -w: disregard white space in lines of two files
- output
    - files
        - \<: only for the left file
        - \>: only for the right file
    - directories

### du

- properties
    - disk usage with showing highest directory
    - ` grep G to show large usage directory `
- usage
    - –h –max-depth=1 \| grep G
        - h for human
- options
    - -x
        - skip mounted file, linked file

### echo

- write
    - $var is dereferenced
    - \\$ suppress dereference
    - use “    “ to give an effect on option
- option
    - -e
        - the followings are effective
            - \\\\, \\n, \\r, \\t
        - ` echo “hello\nworld” `
            - hello\\nworld
        - ` echo -e “hello\nworld” `
            - hello
            - workd

### exec, ok, print

- exec
    - find condition –exec command \{\} \\;
        - as for files found by ‘find’  execute command&#9;cf. xargs
        - execute (-exec) commnd up up to ‘;’&#9;&#9;# ; is special character
            - to remove shell meaning, use escape character \\;
        - \{\} means the found files in find
            - do not separate \{ and \}
    - cf.
        - find exec grep
        - find file using UID
- –ok command \\;
    - similar to –exec
    - confirm before execution
- –print
    - print filename

### find

- general
    - locating Files and directories
    - find path –option argument
        - if omit path, it’s the present directory
            - find -option argument
        - can use wild card for filename
            - find -name ‘\*.pl’
- Option
    - -name, -iname
        - -name ‘\*.out’
            - can use wild card
            - searches all the subdirectories also
        - -iname to ignore case
    - -type
        - -type pattern
            - d: directory, f: regular file
            - find / -name et\* –type d
    - -size
        - find . type f –size +10000
    - - times
        - -mtime: w.r.t. modified time
        - -atime: w.r.t. accessed time
        - -ctime: w.r.t. corrected time
        - -amin, -cmin, -mmin: w.r.t. minite
        - to remove a certain days passed file
            - find . –mtime +30 –type f –exec rm \{\} \\;
    - -perm&#9;&#9;# permission (cf. ls form)
    - -group
    - -user
    - -exec command
- to deprecate “permission denied”
    - add 2\>/dev/null
- e.g.
    - find path pattern
        - find . –name foo
            - only finds foo
        - “find –name eda” finds only eda
            - to include eda in filename, use
                - find –name “\*eda\*”
        - several options
            - find . –type f –name \*.jpg&#9;&#9;&#9;cf chmod
    - find –name “WAVCAR”
        - if path is not, find start in the current directory and look around all the subdirectories
        - Cf. locate is better for short typing
    - suppress “Permission denied”
        - find / -name pmix 2\>&1 \| grep -v “Permission denied”
- find-exec or find \| exec, find-sed, &#9;&#9;cf find-xargs
    - find string recursively
        - find all the files with a string&#9;&#9;cf. grep
    - -exec command \{\} \\;&#9;&#9;&#9;cf. exec
        - receive found file in \{\} and execution with command which ends with \\;
    - e.g.
        - find a file
            - find . -name “INCAR”
        - find a file and grep
            - find . -name “INCAR” -exec grep IMAGES ‘\{\}’ \\;
                - ` IMAGES = 8		 how to display filename? grep -H `
            - find . -name “INCAR -exec grep -H IMAGES ‘\{\}’ \\;
        - find a word and change in-place: &#9;cf. modify mutifiles by grep/xargs
            - find . -name “\*.py” -exec grep input \{\} \\;
            - find . -name “\*.py” -exec sed -i ‘s/inout/rw/g’ \{\} \\;
                - possibility to include other word including the keyword
            - find . -type f -exec sed -i 's/\\/home\\/dshin/\\$HOME/p' \{\} \\;
        - find . –size +5096k –exec ls –l \{\} \\;
        - find . –name “\*.jpg” –atime -1 –exec ls ?\| \{\} \\;
        - find . –type f –empty
        - find /etc –exec grep ’\[0-9\]\[0-9\]\*\[.\]\[0-9\]\[0-9\]\*\[.\]\[0-9\]\[0-9\]\*\[.\]\[0-9\]\[0-9\]\*’ \{\} \\;
        - find /etc -type f -exec cat '\{\}' \\; \| tr -c '.\[:digit:\]' '\\n' \| grep '^\[^.\]\[^.\]\*\\.\[^.\]\[^.\]\*\\.\[^.\]\[^.\]\*\\.\[^.\]\[^.\]\*$'

### find analogue: locate which whereis

- locate, which, whereis
- locate
    - usage
        - locate \[options\] name(s)
    - locate v2
        - find all the directories and files which include “v2”
- which
    - finds binary, exe files
- whereis
    - binary of commander, location of source, location of man page

### gzip

- gzip bigfile&#9;&#9;&#9;&#9;&#9;&#9;cf. compress files
    - makes bigfile.gz
    - uncompress
        - gunzip bigfile.gz
- encrypt the files in place
    - the original files are replaced by the encrypt file

### grep

- ` grep vs pgrep `
    - ` grep searches text lines for a pattern `
    - pgrep searches running processes
- usage
    - ` grep “LVDW “ INCAR* `
    - ` grep -options ‘   ‘ file `
    - ` grep -ivABC `
    - ` grep -rl string dir `
        - all the files with string in dir, (r)ecurrsively
        - only file name display
    - ` grep -l string *py			cf change multiple lines `
        - output only fnames
    - to modification of multiple files
        - ` grep -l str *py | xargs sed -i ‘s/str/newstr/g’  	cf. find_exec `
- option
    - -E: extended RE (ERE)
        - basic regex: special characters of \|, +, ?, etc need escaping
        - -E can use them directory
            - basic: grep “Kinetic\\\|Hartree” siesta.out
            - ERE: grep “Kinetic\|Hartree” siesta.out
        - -E: \|, ?, +, \{n,m\}
    - –i:&#9;ignore case dependency
    - –v: &#9;invert match – select non-matching line
    - -c: &#9;number of lines
        - get grep returns 0 or number
            - if no line returns 0
            - if several line, returns !0
    - -r: &#9;recursive
    - -n: &#9;show number&#9;e.g. 24:\[ ….
    - -B num –A num
        - show how many lines before(-B) and after (-A) matched line
    - -C num
        - if –B and –A have the same number
    - -w: &#9;print if pattern matches with whole word in a line
    - -H: &#9;print filename&#9;&#9;&#9;&#9;&#9;cf find and grep
        - (E.g.) grep F= \*log
            - Output is different as for the number of .log file
                - When there exists only one .log file, it does not print filename
                - When there are more than one .log file. It prints filename in $1
            - -H makes the output regular
    - -R: &#9;recursive and search entirely
    - -n: &#9;line number
    - -l: &#9;list file names only for matching file
    - -e: pattern
    - --include:&#9;--include=\\\*.\{c,h\}
    - --exclude&#9;--exclude=\\\*.o
    - --excude-dir:&#9;--exclude-dir=\{dir1,dir2,\*.dst\}
- multiple matches
    - or
        - “str1\\\|str2”
        - if the line has str1 or str2  to not make space between str1 and \\\|
    - and
        - agrep ‘pattern1;pattern2’
        - ` grep -P ‘^(?=.*pattern1)(?=.*pattern2) `
        - ` grep -X ‘.*pattern1.*&.*pattern2.*’ `
        - ` grep -e ‘pattern1.*pattern2’ -e ‘pattern2.*pattern1’ `
        - ` awk ‘/pattern1/ && /pattern2/ {print;}’ `
    - a but not b
        - ` grep a | grep -v b `
        - to mix with find, use xarg rather than -exec
- string
    - ‘   ‘ or “   “
        - what is difference?
- regex in grep &#9;cf. regex
    - whole word
        - ‘\\b…\\b’ for boundary
        - ` grep –i “\bsp\b” a.out `
            - finds \\tsp\\t or blankspblank not inspiration
    - not working (?)
        - end word in a line
            - ‘\\ssp$’
        - ‘\\sword\\s’
- format of output
- Example
    - ` grep “Optimization” *out | awk‘{print $6}’ `
    - Print only one column
        - ` grep "RIMP2" ph_carboxylic_*/*out | grep "total" | awk '{print $6}' | perl –ne 'END {print "\n"} chomp($_); print "$_\t";'| awk '{print $1 - $2 + $3 - $4}' `
    - in perl, END \{ \} or BEGIN \{ \} is used for a sentence out of loop
    - to change the column output to line output, read output and use chomp($\_) in perl where the standard line input is saved in $\_
    - you can use arithmetic calculation in awk
    - use the next line to get the last line in series: amp-log.txt
        - ` grep “optimization “ dir/amp-log.txt -B 1 | awk ‘/T/ {print $8, $10}’ `
- find all the files with a string
    - ` grep -Rnw path -e ‘pattern’ `
- ` grep and change `
    - no rule for grep and change
    - ` grep to find out `
    - find-sed to change

### history

- env
    - HISTTIMEFORMAT
        - setting
            - su
                - /etc/profile
            - user
                - .bash\_profile
        - format
            - ` export HISTTIMEFORMAT=”[%F %T %Z]” `

### hostname

- psi, kdft, chi

### less / more

- PAGE UP or b: one page up
- PAGE DOWN or space bar: one page down
- Direction key: one line up and down
- G: end of text
- 1G or g: first of text
- /string: searching string forwardly
    - n: next string
- h: help
- q: quit

### ls

- options
    - -a: all the files
    - -l: long
    - -p: present directory
    - -d: list directory themselves not its contents
        - for all the directories
            - ls -d \*/
        - for RE directories
            - ls -d NN\*
    - -v: version
        - natural sort of (version) numbers within text
- e.g.
    - ls -alp
        - shows all the files with properties for the present directory
- show directory only
    - without matching RE
        - ls -d
            - shows only .
        - use matching with ‘/’
            - ls -d \*/
                - ‘\*/’ pattern matches all the subdirectories in the current directory
                - to include hidden directories
                    - ls -d .\*/ \*/
            - ls -d /any\_path/\*/
    - with RE
        - ls NN\*
            - shows all the NN\*/ and their contents
        - ls NN\* -d
            - for Only directories
    - -p
        - Append “/” after directory name
    - Copy directory list
        - ls -l \| grep ^d \| awk '\{print $9\}' \> dos.dir
- One file in a line
    - ls -1
        - it work also in the dir
        - ls dir\_name -1
    - ls \*inp \| more  \> dir.txt &#9;! this is better ls \*inp -1 \> dir.txt
- color setting
    - color is set by $LS\_COLORS
    - alias ls=’ls –F --color=tty’
    - alias ls=’ls --color=auto’
        - alias ls ‘ls –color=tty’&#9;# csh
- indicator style
    - -p&#9;append slash for indicator to directories
    - --indicator-style=’non’&#9;, ’slash’,…
- ls /etc/g\* not recursively
    - echo
        - ` echo /etc/g* `
    - grep
        - ls /etc/g\* \| grep “\\bg”
- recursively
    - ls –R
- sort
    - ls -d NN\* \| sort -n -t N -k 3
    - ls -lv NN\*

### ln

- soft link
    - ` ln –s target link_name `

### locate

- locate finds file in a database&#9;&#9;&#9;cf. use find
    - need to update database after a new file is created

### mkdir

- options
    - -p: autogenerate the bridge directories if they don’t exist

### more

- similar to less

### mv

- ` mv *.out Freq `
    - move all matched files to Freq directory
- xargs for more sophisticate function

### ftp, sftp, scp

- ftp: same as sftp
- sftp (scp)&#9;&#9;&#9;cf KISTI sftp
    - scp and rsync
        - scp source target
    - properties
        - uses ssh port
            - if ssh port is changed, use -oPort for port
        - for security, realize ftp through ssh protocol
        - only binary mode
        - slower than ftp
    - connection
        - sftp [joonho@kdft.kaist.ac.kr](<mailto:joonho@kdft.kaist.ac.kr>)
        - using port number of ssh
            - sftp -oPort=40316 [jhpark@143.248.37.246](<mailto:jhpark@143.248.37.246>)
        - sftp\>open id@hostname
    - disconnect
        - sftp\>quit&#9;# or exit, bye
    - commander
        - help/?
        - bye
        - remote&#9;local
            - ls(dir)&#9;lls(ldir)
            - pwd&#9;lpwd
            - cd&#9;lcd
            - mkdir
            - rmdir
            - delete
        - get/mget&#9;# from server to guest, m for multiple
        - put/mput&#9;# from guest to server
        - open: connect
        - close: disconnect
    - .netrc
        - save passwd
- scp
    - scp file id@server:/path
    - normal
        - scp file [joonho@chi.kaist.ac.kr:~/](<mailto:joonho@chi.kaist.ac.kr:~/>)
        - scp [joonho@chi.kaist.ac.kr:~/test](<mailto:joonho@chi.kaist.ac.kr:~/test>) .
    - in the same network
        - scp –r node12:/scratch/joonho/
        - scp cmcc3:~/.ssh/id\_rsa.pub .
    - large file
        - scp fails as it try to grab as much bandwidth as possible: stalled
        - scp –l 8192 a.tar joonho@...
            - it takes long time
    - option
        - -P &#9;port
            - scp –P port server\_file obj\_file
        - -r&#9;recursive
        - -l&#9;limitless
            - if not work, use rsync
- sftp in script
    - using EOF
        - sftp -oPort=23 [kalenpw@184.155.136.254:/home/kalenpw](<mailto:kalenpw@184.155.136.254:/home/kalenpw>) \<\<EOF
        - put /home/joonho/a.x
        - exit
        - EOF&#9; this should be in the first column though inside block
    - \<\<
        - marker \<\< followed by name(EOF) tells the script to pass the following lines until the name is found at the beginning of the line (by itself)
- error
    - scp, sftp fails when ssh prints out
        - scp
            - not working
        - message from sftp
            - Received message too long 1231975525
        - turn off message from .bashrc file

### rename

- not linux standard command
- install
    - ` sudo apt-get install rename `
- options
    - -s: change target of symbolic link
    - -o: do not overwrite
    - -n: show results not performing
- usage
    - rename TO4 tO4 \*
    - rename TO8 tO8 HfSe2L1O36WO4TO4Q\*

### tail - head

- head
    - option
        - -n for number of line
- tail
    - option
        - -n
            - -n#
        - -f for following the added line during job is running
    - too many logs to be added
        - tail –f \| grep “404”

### tar

- ` tar c(x)vzf a.tar filename				cf. compress files `
- options
    - alternative for generation
        - -c&#9;create
        - -x&#9;extraction
        - -t&#9;test - check inside tar file
        - -I, --use-compress-program=COMMAND&#9;# include compressor
    - compression
        - -z &#9;gzip
            - ` tar cvzf backup.tar.gz dirs/ `
        - basic tar and gzip
            - ` tar cvf backup.tar dirs/ `
            - gzip backup.tar&#9; backup.tar.gz
                - backup.tar is removed
                - to leave backup.tar
                    - gzip -k backup.tar
        - j using bzip2
    - add or append
        - --append/-r&#9;recursive?
            - ` tar --append -f a.tar files `
            - p will preserve the original permission
        - -u&#9;update
            - new version is appended not overwrite
        - these options can’t be used in gzip file
- .txz file
    - ` tar Jxvf file.txz `
        - use -J or --xz

### whoami

- ` echo id `

### which

- find executable in the $PATH

### xz

- uncompress
    - xz -d bigfile.xz
    - unxz bigfile.xz
- more compress after tar
- xz
    - xz a.tar
        - makes a.tar.xz
- unxz
    - unxz a.tar.xz
        - makes a.tar &#9;&#9;# at the location
    - xz --decompress a.tar.xz
        - -d == --decompress

### zip

- uncompress
    - unzip

## Shell Command Middle

### basename & dirname

- basename
    - extract the last name, filename or dirname
        - bash
            - fulldir=\`pwd\`&#9;&#9;&#9;in bash
            - base=\`basename $fulldir\`
                - base has the present directory or filename
        - csh
            - basename \`pwd\`
                - cannot save to variable
            - set dir = “…/…/dr”
            - basename $dir
            - in queue script
                - set dirname = \`basename $SBE\_O\_WORKDIR\`
                - ` echo $dirname >> $logfile `
    - cut suffix
        - basename $full\_filename .msi
- dirname
    - extract the precedent dirname
        - dir=\`dirname $fulldir\`

### chmod

- change mode of files&#9;&#9;&#9;cf. chown, chgrp
    - r for read
    - w for write
    - x for execution
- options
    - -R: recursive
- usage
    - ` chmod 755 filename `
    - don’t use this
        - ` chmod -R 755 . `
            - N.B. this change all the files and dirs.
- special technique
    - change only directory
        - find . -type d -exec chmod 755 \{\} \\;
    - change only files
        - find . -type f -exec chmod 644 \{\} \\;
    - only group permission
        - ` chmod -R g+x . `
        - ` chmod -R g+r . `
- permissions
    - to get into a directory
        - g+r is required
    - to copy a file from source dir
        - g+r, g+x are required for dir
        - g+r is required for file
    - to write at home
        - u+x, u+w are required

### crontab

- setup
    - utility control file
        - /etc/cron.d/cron.allow: if exist, only the users can use crontab
        - /etc/cron.d/cron.deny: if exist, those cannot run crontab
        - if both doesnot exist, only root can run crontab
    - crontab stores user name in /var/spool/cron/crontabs/username
    - /etc/rec.d/init.d/crond: for start, stop, restart
- usage
    - crontab –option
        - -l: for list
        - -e: edit command file
        - -r: remove all the list
    - confirm
        - ps –ef \| grep crond
- start
    - /etc/init.d/crond start\{restart\|stop\}
- format
    - 1 command in a line
        - minute hour date month day command
    - e.g.
        - m       h  dom mon dow   command
        - 0  0 \* \* \* rsync -avz --delete /home/joonho/  &#9;/Data/Backhome/joonho
    - 3,5,7 for several hour
    - 4-6&#9;4, 5, 6 o’clock everyday

### cut

- whatitis
    - cutting out the sections from each line of files and writing the result to standard output
        - cut option filenames&#9;&#9;cf. cut string
            - option
                - delimiter
                - field
    - application with pipe
        - cat file \| cut -d ‘ ‘ -f 1 \| sort -r
    - cut string
        - str=a.pbs
        - pre=\`echo $str \| cut -d. -f1\`
        - ` echo $pre  ‘a’ `
- cut –d\[ \] –f# filename
    - -d defines delimiter
    - -f defines field where index starts from 1, 2, 3…
- to get a filename as string
    - ext=’cut –d. –f2 \<\<\< $1\`

### diff

- get the difference between dirs and files
- option
    - -r: including subdirectories and files
- notation
    - in “diff a b”
    - \< left file, \> right file
    - character
        - a: adding
            - Nan,m
                - at N, add updated lines of n~m
        - d: delete
            - n, mdN
                - m-n lines deleted, then sync at N
        - c: change
            - n, mcq,s
                - n~m lines deleted then added q~s in file b

### dircolors (LS\_COLORS)

- howtocheck
    - dircolors
    - dircolors \| tr : “\\n” \| head -10
    - ` echo $LS_COLORS `
- basic setting for color
    - ls --color=auto
        - alias ls=’ls --color=auto’
- change colors being set by LS\_COLORS
    - ` export LS_COLORS=’   :    :-separated `
    - ` export LS_COLORS=$LS_COLORS:”ex=00;32” `
        - omitting $LS\_COLORS will change the colors of other files
- formats
    - kisti
        - ex=38;5;34:
        - ln=38;5;51
    - pt
        - ex=38;5;34:
        - ln=38;5;51
- file types
    - di: directory; fi: file: symbolic link: ln, block device: bd, character device: cd, executable file w. “x” permission: ex
    - \*.extension: any file with extension
    - file\_kind
        - \*.ets works. in.\* does not work
        - fi – general file
        - di – path
        - ` ln – symbolic linker `
        - pi – FIFO
        - so – socket
        - ex – execution file
        - \*.png – file with extension of png
- LS\_COLORS
    - usage
        - ` LS_COLORS=“di=1;31” `
            - directory 1; (bold), 31 (red)
            - di is set and for all the other types, default is used
        - ` LS_COLORS=”no=00:fi=00:*.rpm=01;31:” `
            - no need to export
            - but in .bashrc
                - except 1<sup>st</sup> line, use LS\_COLORS=”$LS\_COLORS:…”
    - general
        - text style
        - text color (foreground color)
        - background color
    - text style
        - 0: normal text
        - 1: bold or light
        - 2: dim
        - 4: underlined
        - 5: blinking
        - 7: reverse back and fore ground color
    - background color code:
        - black 40
        - blue 44
        - Cyan 46
        - green 42
        - purple 45
        - red 41
        - white 47
        - yellow 43
    - color code:

Figure 3 dircolor

- Colors

|  |  |  |  |
| --- | --- | --- | --- |
| 30 | black | 90 | dark gray |
| 31 | red | 91 | light |
| 32 | green | 92 | light |
| 33 | yellow | 93 | light |
| 34 | blue | 94 | light |
| 35 | magenta | 95 | light |
| 36 | cyan | 96 | light |
| 37 | light gray | 97 | white |

- 39=default foreground color: 30=black: 31= bright red: 32= bright green: 33= yellow: 34= blue: 35= magenta: 36=cyan: 37=light gray: 90=dark gray: 91=light red: 92=light green: 93=light yellow: 94=light blue: 95=light magenta: 96=light cyan: 97=white
- etc
    - file color setting in Initial file
        - .dir\_colors
- find setting
    - ` setenv | grep COLOR `

### du –sh /dir

- disk usage
    - check disk usage of directories or files
    - default is Kbyte
- option
    - -s: for total usage of a directory
    - -h: human
        - du -h:
    - --max-depth=1: shows the 1<sup>st</sup> subdirectories

### free

- show memory and swap usage

### gcc

- C compile front-end
- treat order
    - C preprocessing
        - treat #include #define #ifdef …
        - done by cpp
        - e.g.
            - gcc –E –o hello.i hello.c
                - hello.i
    - C compile
        - change source code to assembly source code
        - done by cc1
    - Assemble
        - change it into object code
        - done by as
        - e.g.
            - gcc –c hello.c
                - hello.o
    - Linking
        - link to library and become execution file
        - done by ld
- option
    - -o out\_filename
        - gcc hello.c
            - a.out
        - gcc –o hello hello.c
            - hello
    - preprocessing
        - -E&#9;: treat only C preprocessing
    - compile
        - -W&#9;: warning message
        - -Wall : all the warning message
        - -O, -O2, -O3&#9;: optimization
            - increased number makes more optimized code but it takes longer time in compilation
        - -g : for gdb of debugging
    - assemble
        - -c : make object file by assembling the assembly code

### git

### jobs

- fg or fg %n
- bg or bg %n

### kill

- kill process
- option
    - -l:
        - list all the signals: integer is matching with signal
        - 9 SIGKILL
    - -9 pid is same as –SIGKILL pid

### module

- for what?
    - for the unified system which have diverse packages or versions of softwares
        - manipulate your environment such as PATH, LD\_LIBRARY\_PATH to gain access to new software or different versions of the same package
        - e.g.
            - ` module load python/3.4 `
        - for default version
            - ` module load python `
- switches
    - avail
        - list all the available modules
        - if there are multiple versions of a single package, one will be default which can be loaded when it is called without version
    - whatis
        - avail with short description
    - load MODULEname
    - unload MODULEname
    - list
        - show currently loaded modules
    - help \[MODULEname\]
    - show MODULEname

### passwd

- change password by user

### ps

- process
- options
    - aux
        - N.B.: a and -a are different
    - -a:
    - ef
- kill process
    - ps -ef \| grep id \| awk ‘\{print $2\}’ xargs kill -9

### realpath, pwd, cd

- realpath .
    - reveals the full path (absolute path)
- pwd –P
    - when going into a directory through symbolic link, pwd shows path through symbolic link
    - -P shows physical path
    - cf. cd –P linked\_dir
- ` cd –P .. `
    - to parent directory through physical path

### reboot –n

### rsync –avz –S -8

- what?
    - by default, only copies new and changed files from source to destination
    - remote sync using network
        - port TCP 873
        - based on ssh or rsh
        - error in protocol incompatibility
            - : protocol version mismatch -- is your shell clean?
            - turn off output of .bashrc in remote server
            - when be asked passwd while ssh logs in w/o passwd
                - ` rsync -avz -e ssh dir1 dir2 `
    - for usage refer to crontab
- install
    - ` apt-get install rsync `
        - apt-cache search rsync
        - apt-cache show rsync
            - for version
    - apt-cache show xinetd
- setup
    - setup file
        - ` apt-get install xinetd `
        - /etc/xinetd.d/rsync
        - /etc/rsyncd.conf
    - ` rsync env `
        - /etc/xinetd.d/rsync
            - disable = no
    - ` rsync server `
        - /etc/sryncd.conf
    - open 873 port in iptables
        - firewall
- usage
    - works for large size file
    - ` rsync -options source destination `
        - ` source or destination `
            - user@host:path
        - two directory
            - ` rsync –azvh /var/lib/mysql/ /home/backups/mysql `
    - Details for directory
        - directory itself or its contents
            - ` source notation `
                - /home/joonho&#9;: copy folder itself
                - /home/joonho/&#9;: copy files inside directory
            - destination
                - no difference?
        - it generates target directory if there is not
    - ` ssh comes into play for network sync `
        - remote to local
            - remote machine
                - ` rsync env `
                    - hosts allow=my\_ip
                - open firewall
            - copy
                - ` rsync –avz leif@example.com:/home/lif/data /home/leif/backup/ `
        - local to remote
            - copy
                - ` rsync –avz /home/leif/data/ leif@example.com:/home/lif/backup `
                - ` rsync –avzP –delete –e ssh source_dir user@server:/destination_dir `
            - ` rsync –avz –e ssh dir dir `
    - what method?
        - use rsync daemon ( :: )
            - inetd (port 873), no encryption
        - use remote shell ( : )
            - ` ssh (port 22) `
    - what does it do?
        - synchronize
            - --delete
                - delete if the file in destination is not in source
        - just copy with comparing size and time
            - --checksum
                - slow but better in comparison (of checksum)
                - divide the file into a chunk with fixed size and compare
    - for automatic sync: crontab
- option
    - e.g.
        - -zvh
        - -avz, -avuz
    - -a: archive mode
        - -r(recursive), -t(type stamp), -l(symbolic link), -p(permission), -g(group), -o(owner) -D
        - include hidden files
        - ` cp makes a new timestamp `
            - while rsync reserve the original timestamp
    - -v: verbose
    - -z: compress
        - fast transfer for remote but can be slower in the same machine
    - -h: human
    - -u: if destination file is modified, do not overwrite
        - compare two files using date
        - in case destination directories are modified
    - -d: only directory tree is copied
    - --progress, -P: see the progress
    - include, exclude
        - --exclude ‘data’
        - --exclude ‘\*.bak’
        - --exclude ‘Qchem’ --exclude ‘archives’ --exclude ‘a.txt’
    - --delete
        - complete synchronize
            - delete a directory in destination, if it is not in the source
    - --ignore-existing
        - only files that do not exist on remote are copied
    - --update
        - only local file with newer timestamp is copied
    - --dry-run
        - to test what will be transferred
    - -K
        - to preserve symbolic link
- auto synchronize
    - cron
    - crontab: five fields with command
        - m h dm m dw command
        - minute (0-59); hour (0-23); date (1-31); m (1-12); day (0:Sunday…)
        - if not used ‘\*’
- e.g. mysunc\_disk.sh
    - ` EXLST1="--exclude-from /aces/disk/env/bin/exfiles.txt" `
    - ` rsync -rltDv -S -8 -i ${EXLST1}  /aces/disk/archives/softwares/licenses/   . `
    - sync to Windows Character set (CP949)
    - ` rsync -rltDv -S -8 -i -e ssh --iconv=CP949,UTF-8 /aces/disk/syncpot/webhard/ `
- error
    - ` rsync error: failed to set times on destination_dir: operation not permitted `
        - permission error on destination
            - permit the destination directory
                - ` chown id:group dir `

### sg

- similar to git

### sleep

- usage
    - sleep time
- time
    - default: s
    - 1s
    - 1m
    - 1h
    - 1d

### sort

- options
    - -n: sort numerically
    - -t: field separator
    - -k: field index
- e.g.
    - ls -d NN\*
        - NN10 NN15 NN20 NN25 NN30 NN40 NN5 NN50
    - ls -d NN\* \| sort -n -t N -k 3
        - NN5 NN10 NN15 NN20 NN25 NN30 NN40 NN50

### ssh/sshd

- usage
    - source
        - [https://www.linuxcapable.com/how-to-install-and-enable-ssh-on-debian-linux/](<https://www.linuxcapable.com/how-to-install-and-enable-ssh-on-debian-linux/>)
    - install
        - ` sudo apt update && sudo apt upgrade `
        - ` sudo apt install openssh-server `
        - sudo systemctl status ssh
    - ` ssh user@ip -pportnum `
        - default portnum = 22
        - ` ssh jhpark@143.248.37.246 -p40316 `
- customize
    - /etc/ssh/sshd\_config
        - SSH setting overall server
        - root authority
        - login
            - Bash
                - PermitRootLogin no
                - PasswordAuthentication yes
        - port change
            - Port 22
            - e.g.
                - Port 2222
        - restrict connection
            - AllowUsers&#9;joonho
        - key authentication
            - PubkeyAuthentication&#9;yes
        - idle timeout
            - ClientAliveInterval&#9;300
            - ClientAliveCountMax&#9;2
    - $HOME/.ssh/ssh\_config
- restriction
- Error in ssh
    - No route to host
        - wrong ip
        - server down
        - netfilter(iptables, firewall) blocks
        - sshd inactive in host
    - fix ‘no route to host’
        - sshd active
        - firewall
- use different port
    - designate several ports
        - /etc/ssh/sshd\_config
            - Port 10022
            - Port 20022
        - open port with a specific ip
    - restart with iptables or firewalld
        - using systemd
            - systemctl restart sshd
                - If no sshd.service  install openssh
        - without using system
            - service sshd restart
- command on nodes
    - ` ssh psi01 mkdir /scratch/joonho `
        - You can make dir or copy file
    - cf. qnodes.sh
        - ` ssh $node ls /scratch/$id `
            - when it fails it sometimes returns 2 rather than 1, so
            - if \[ $? –ne 0 \] rather than if \[ $? –eq 1 \]
- X forwarding&#9;&#9;&#9;cf. skill ssh
    - ` ssh –[XY] ipaddress `
        - localhost error
- port forwarding
    - background
        - in many server, ssh and a few service ports are open
        - need to open port for managing service
    - kinds
        - local port forwarding
        - remote port forwarding
        - dynamic port forwarding
- local port forwarding
    - usge
        - use ssh server like gateway or proxy server and connect to external: tunneling
    - server: 192.168.96.6
        - running Tomcat server
        - web port: 8180
        - open port: 22
        - closed port for Web and JMX, Tomcat
        - in web of guest, server name is always ‘localhost’
    - to use Tomcat
        - ` ssh –L <local port>:<remote server>:<remote port> [ssh server] `
            - -L: local port forwarding
            - local port: will be used in client
            - remote server: 192.168.96.6 will be used as gateway
        - local port forwarding to external of yahoo.com:80
            - ` ssh –L 10030:yahoo.com:80 root@192.168.96.6 `
            - in web of clinent
                - [http://localhost:10030](<http://localhost:10030>)
        - local port forwarding to internal service
            - ` ssh –L 10030:localhost:8180 root@192.168.96.6 `
                - 8180 is port for Tomcat
            - in web
                - [http://localhost:10030](<http://localhost:10030>)
- ` ssh –l id –Y servername [hulk.kaist.ac.kr] `
- option
    - -L: port:host:hostport&#9;&#9;e.g. 8891:localhost:8891 cf.
    - -N: do not execute a remote command
        - useful for just forwarding ports
    - -f: request ssh to go to background just before command execution
    - e.g. in jupyter
        - ` ssh –XNf –L … `

### ssh-keygen

### stat

- file status
    - stat a.txt
- e.g.&#9;
    - ` FILESIZE=$(stat -c%s filename) `
- options
    - -c, --format=FORMAT: use input format
        - -c%s
- format
    - %s: total size in bytes

### (g)zip/(g)unzip, tar

- zip
    - zip a.zip files
    - unzip a.zip
- gzip –d
    - uncompress the executable
    - gunzip
- bz2
    - gzip2 –d ….tar.gz2
    - ` tar xf ….tar.gz2 `
        - ` tar can extract gz2 `
- tar
    - ` tar xvzf a.tar `
    - ` tar cvzf a.tar files `

### tee

- whatitis
    - output to stdout and file at the same time
- usage
    - ls -l \| tee file.txt \| less
        - write file.txt by reading ‘ls -l’
        - less also reads ‘ls -l’
    - ` echo test | tee tee.txt `
        - stdout: test
        - cat tee.txt
            - test
- options
    - -a : append
    - -I : ignore interrupt

### time

- time commander
    - output

### tmux

- terminal multiplex
    - a SSH/manage several virtual sessions in a terminal
- function
    - sustain session (continue even ssh connection is lost)
    - several windows / pane
    - background job is going on
- e.g.
    - upgrade OS in ubuntu

### top&#9;&#9;

### tput

- improve terminal representation
    - [https://wikidocs.net/215602](<https://wikidocs.net/215602>)
    - tput: Terminal PUT
        - input to the terminal
    - rmcup
- cup
    - Cursor User Position
    - smcup = start memory cup (alternative screen enter)
        - less, vim, man, tmux copy-mode, htop, etc runs smcup
            - when finish it should run rmcup
    - rmcup = alternative screen leave
- usage
    - $tput rmcup&#9;e.g. mouse wheel scroll terminal scroll
        - mouse scroll work for scroll terminal rather than history
    - one of ncurses package in linux distribution
- terminal
    - ` echo $XTERM `
        - xterm-256color&#9;in kisti

### tr

- translate or deleting characters
- syntax
    - tr \[option\] set1 \[set2\]
- usage
    - tr “:” “\\n”
        - from string, change : into \\n
- options

### trap

- if a signal occurs, trap gets the signal and do a preassigned job
- syntax
    - trap arg signal
        - or trap command signal
    - if signal occurs, action (arg, command) is excecuted

### xargs

## User Friendly command

### compgen -A function

- displays only function name

### declare

- list functions defined by myself
- options
    - -F
        - list function names
    - -f \[function\_name\]
        - shows all the functions
        - \[function\_name\]
            - shows the function

### set

- set \| grep “ ()”&#9; shows functions

### type

- type function name
    - shows function
- type fname
    - == declare -f fname

### typeset (obsolete)

- list functions defined by myself
- options
    - -f
        - list all the functions
    - -F
        - list only function names

## System Management Command

### Standard in, out, & error

- 0: standard input
- 1: standard output
- 2: standard error
- n\>&m (bash commander)
    - change of standard input and output
    - 2\>&1
        - standard error is redirected to standard output
- \<&0&#9;: standard input
- Te.out 2\>/dev/null
    - discard the standard err

### adduser

- usage
    - adduser \[options\] userid&#9;&#9;&#9;cf useradd, userdel
    - slurm
        - adduser -gusers -d/home/id id
        - passwd id
- No options
    - adduser userid&#9;&#9;&#9;&#9;cf id to check uid, gid
    - ` make home directory and copy files from /etc/skel (ls /etc/skel –a) `
        - if not, make a home directory
    - ask passwd, personal information such as telephone, address, etc
        - makes /home/username
    - if not asking passwd
        - sudo passwd userid
            - New password
        - sudo passwd -d userid&#9;&#9;! for deletion
- options
    - groupname
        - adduser userid sudo
        - add sudo (group name) to id
    - -uid ID
        - adduser joonho -uid 1000
        - GID will be 1000 also
    - -gid ID
    - -g group
    - -m create home directory
    - -d&#9;directory location
        - adduser -g users -m -d /home/userid&#9;userid
- permission
    - /etc/login.defs
    - HOME directory permission
        - (fedora)
            - HOME\_MODE&#9;0700  0750&#9;&#9;cf. Debian: DIR\_MODE
                - 0750: if the same user, can get in and read
    - new file and directory permission
        - UMASK&#9;022
        - calculation
            - basic permission
                - file: 666
                - directory: 777
            - umask permission
                - file: 666 - 022 = 644
                - dir: 777 - 022 = 755
- cf. useradd
    - not automatically generate home directory
    - passwd username
        - firstly set passwd
    - for further information of useradd

### addgroup

- sudo addgroup -aG group username
    - -a for append
    - -G for group name

### apachectl

- to start and stop httpd after installing httpd package
- subcommand
    - start
    - stop
    - restart
        - equal to /sbin/service httpd restart
    - status

### /bin, /sbin

- /bin: binary directory
- /sbin: binary directory for superuser

### badblocks

- check bad blocks in a partition
- badblocks –v /dev/sda2

### #biosdecode

- parses the BIOS memory and prints info:
    - SMBIOS
    - DMI
    - etc
- cf. dmidecode

### blkid

- check uuid of partition
- sudo blkid

### chgrp

- chgrp –option group FSO&#9;&#9;&#9;cf. chown
    - -R: recursive
    - FSO stands for file system object

### chown

- ` chown [–R] user[:group] file			cf. application, chgrp, usermod `
    - -R: recursive, that works for subdirectory

### cups-config

- install
- options
    - --version
    - --api-version
    - --help

### dkms

- dynamic kernel module supports
    - to make a kernel which is not in linux kernel tree

### dmesg

- usage
    - check system booting message
    - will show kernel error
        - cf. /proc/kmsg
- location
    - /var/log/dmesg
- option
    - dmesg –C
        - clean and renew message
    - dmesg “ grep -I segfault

### #dmidecode

- command line utility to parse the BIOS memory and prints info:
    - IPMI Device
    - memory type and speed
    - serial number
    - BIOS version
    - PCI/PCIe slots and speed
    - etc
- usage
    - IPMI device
        - #dmidecode --type 38
    - PCI/PCIe slots
        - #dmidecode --type 9
- number / device
    - 0 BIOS
    - 1 System
    - 2 Base Board
    - 4 Processor
    - 17 Memory Device
- cf. biosdecode, lspci

### dracut

- whatitis
    - recover/rebuild/re-generate initramfs
        - initramfs: initial ram file system
    - corruption of initramfs can occurs by many ways
        - by install a buggy device driver
        - then it becomes unbootable
    - unbootable or kernel panic
        - screen stops during booting
- whenever new kernel is installed, new initramfs is built in /boot
- in case no initramfs image
    - ls -ltrh /boot/initramfs-\*
        - size 0
    - #dracut -f /boot/initramfs-kernel…img $(uname -r)
    - reboot
- for update kernel
    - dracut -f --kver kernel\_version

### firewall-cmd

### fsck

- file system check and recover

### fuser

- shows process which a file or a socket uses
    - in umout or remove a hidden file such as .nfs…..
        - “device is busy”
    - cf. lsof
- Usage
    - fuser file
        - shows process ID which uses the file
- option
    - -v: detail
    - -n: namespace
        - sudo fuser -n tcp 80 443
        - sudo fuser -n tcp -v 80 443
    - -k:
        - kill signal
        - sudo fuser -v -k /var/
            - send kill signal to all the processes which use /var

### df

- df : disk free
    - usage of file system
    - storage of total, usage, available, use %, mount info
    - prevent file system full
    - cf. du
- confers
    - /etc/fstab&#9;file system
    - /etc/mtab&#9;mount info
- options
    - -k, -m for display scale
    - -h: for human
    - .: partition where pwd is included
        - df .
    - -a for all
    - -t for special type
        - df –t ext3
- display
    - device name, …. 6<sup>th</sup>-mount point of device

### fdisk, /sbin/

- do: partition program
    - works on 1 disk
- e.g.
    - su –
    - fdisk /dev/sda
        - m for help
        - p for print the present partition table
        - n for new partition
            - p for primary partition up to 4
            - e for extended partition, the 4<sup>th </sup>one will be e and e can have 4 partitions also
            - p: 1, 2, 3
            - e: 4, 5, 6, 7
        - a for boot partition
            - 1 for taking 1<sup>st</sup> primary partition as boot partition
        - d for deleting
        - t for changing system id
            - e.g. linux swap
            - l for list of system id for t
        - w for quit with saving
        - q for quit without saving
- partition recover is possible – high tech
- fdisk –l
    - shows disk

### file

- file executable&#9;&#9;&#9;cf. library
    - dynamic or static link to library

### free

- free -h
    - to check free memory

### gcc wrapper

- wrapper
    - means a batch which includes several jobs which can be done at a time
- gcc hello.c
    - cpp hello.c \> hello.i&#9;! C Pre Processor(cpp) to deal with #define, #include
    - gcc –s hello.i &#9;&#9;! C compile (cc1) to assembly making hello.s
    - as –o hello.o hello.s&#9;! assemble hello.s to object file
    - ld hello.o other\_libs&#9;! link(cllect2) to libraries to make executable, a.out
- gcc options
    - -W: warning
    - O: optimize
        - O2 – level 2, almost optimize
        - O3 – level 3,
    - -S: to assembly \*.s
    - -c: compile using as, \*.o
- cpp0 option
    - -I : include header file
    - -include
    - -D: define macro outside
- collect 2/ ld option
    - -L: define library directory
    - -l: library to link
    - -shared
    - -static

### gdisk

- ` make partition in new harddisk driver `
    - gdisk /etc/sdd
        - confirm the number of partition and each size before start
        - partition removes all the data
    - after making partition, go to making filesystem
- subcommand (sequential)
    - use ? or help on subcommand anytime
    - p
        - shows present partition
    - o
        - remove all data and make a protective MBR
    - n
        - ` make new partition `
        - L shows filesystem
            - 8300 default for linux filesystem
        - start&#9;1
        - last&#9;&#9;+500G&#9;&#9;#G, T, etc can be used
    - for several partition
        - continue n of above stage
    - w
        - write and exit
- confirm
    - ls /dev
        - Now sdd has sdd1, sdd2, etc
    - format each partition: mkfs

### getent

- get entry from
    - ahosts, aliases, ethers, group, gshadow, hosts, netgroup, networks, passwd, protocols, rps, services, shadow
    - cf. passwd

### groups

- options
    - no option: shows all the groups
    - username: group membership of a user

### group-related

- ` make groups `
    - #groupadd gname
    - #groupadd gname2
- create user and add to group
    - #useradd -G new\_group newuser
        - change primary group  usermod
    - #passwd newuser
- give id authority
    - add user sudo authority
        - adduser joonho sudo
- groups shows groups where the user belongs
    - #groups
        - USER : group1 group2 …&#9;&#9;&#9;&#9;cf. usermod
- show id
    - #id
- group change
    - usermod -g king userid
- /etc/group
    - animal:x:1001:tom,jerry
        - groupname:group passwd(x not use):group id:user
- primary group
    - /etc/passwd
        - tom:x:1000:1003::/home/tom
        - user:user passwd:user ID:primary group ID::/home directory

### groupmod

- assign group id to user
    - groupmod -g 1002 joonho
- cange an old existing groupname to a new
    - groupmod -n newgroup oldgroup
- e.g. application
    - to change a user’s group name to existing groupname
        - use usermod

### hostname

- show domain name
    - hostname
        - chi or psi etc
- options
    - -f: fully qualified domain name
        - chi.kaist.ac.kr
    - -d: domain name
        - kaist.ac.kr
    - -I: ip address
        - cf. ifconfig for more detail
    - -i: internal ip address
        - 127.0.1.1
- change hostname
    - temporal change
        - hostname newname
        - hostname
            - newname
    - permanent change without rebooting
        - sudo hostnamectl set-hostname iron
            - if you log out and log in, you will see the hostname has changed
    - permanent change: use one of two options
        - ` vi /etc/hostname `
            - newname
            - save and close the file
        - hostname -F /etc/hostname
        - ` vi /etc/sysconfig/network `
- etc files
    - /etc/resolv.conf
        - ip of domain server
    - /etc/hosts
        - 127.0.0.1&#9;localhost
        - 127.0.1.1&#9;chi.kaist.ac.kr

### #hostnamectl

- #hostnamectl set-hostname chi

### ibus-setup

- setting Korean-Hangul cf. ibus

### id

- find UID and GID of the current user&#9;e.g. application
- options
    - -u&#9;effective UID
    - -n&#9;name instead of number
    - -g&#9;effective GID&#9;cf. groups to check all groups where user belong
    - -G&#9;all GID’s
- chi
    - id -u → joonho
    - id -g → joonho
- kisti
    - id -u → 6040169
    - id -g → 6040169
    - id -un → x1813a01

### ifconfig

- whatitis
    - do prefer ip a
    - in case ….
- install
    - ` apt install net-tools `
- /sbin/ifconfig
    - superuser: ifconfig
    - user: /sbin/ifconfig
- display ip address
    - eth0
        - inet addr:192.168.0.189
- manual setting
    - sudo ifconfig eth0 143.248.247.232 netmask 255.255.255.0
- cf. network problem

### ifup\|ifdown

- ifdown
    - breaking network connection
- ifup
    - activate network connection as the present setting

### ld, ldd, ldconfig

### ln –s real_file link_file

- soft link
    - ` ln –s f_target link_name `
    - ‘ls -al’ shows ‘l’
- e.g.
    - want to link /usr/local/etc/nginx to /etc/nginx
        - ` cd /usr/local/etc `
        - ` ln -s nginx /etc/nginx `
            - in fact make link /etc/nginx -\> /etc/nginx
                - because the source path is relative to the link’s path
- remove
    - rm link\_file
        - if linked file is directory
            - it can’t remove
            - do unlink
    - unlink link\_file
        - it is removed
- copy symbolic link
    - copy original file
        - ` cp link newfile `
            - same as
                - ` cp -L link newfile `
        - target file’s contents are copied
        - the newfile becomes regular file, not a link
    - preserve link
        - ` cp -P link.txt copy.txt `
        - copy.txt points to the same target

### loginctl

- doing&#9;&#9;&#9;&#9;&#9;&#9;cf. application to NoMachine
    - introspect and control the state of system login manager, system-login.service
    - provides a unified interface for managing user logins, sessions, seats, and users
- subcommand
    - list-sessions
        - show all the login sessions
    - session-status session-id (from list-sessions)
    - activate id
        - activate
    - lock/unlocking
        - lock-session id, unlock-session id
    - terminate-session
    - kill-session
    - list-users
    - user-status username
- list-sessions in eta
    - first login
        - 3 1000 joonho seat0 tty2
            - GDM is overridden by tty2
        - GDM runs
            - Debian-gdm&#9;seat0&#9;tty1&#9;! separately runs to manage the graphical login screen
    - MobaXterm connect
        - 10 1000 joonho       pts/8&#9;&#9;! this is mobaxterm
        - 11 1000 joonho
        - 3 1000 joonho seat0 tty2&#9;! when disconnected, eta recovers
    - MobaX logged out & NoMachine connected
        - 3 1000 joonho seat0 tty2
        - c5 1000 joonho&#9;&#9;! this is NoMachine
    - New session on login
        - when you successfully log in, GDM launches your GNOME sesktopo session, but it starts a new session on tty2
        - GDM passes my view from tty1 to tty2
            - while tty1 is active and ready for switching
- relation with screen
    - screen lock
        - the present session remains active, running in background
        - lock screen hides the active session, requiring a password
    - suspend
        - if login crushes, it make a new login session with name of c3 or another ID

### lscpu

- find architecture of cpu&#9;&#9;&#9;&#9;&#9;cf. ls
- spec
    - Architecture: x86\_64
    - Op-mode: 32/64 bit
    - Number of total CPU cores: including all sockets
    - Model name
    - Cache memory: Lld, Lli, L2, L3
    - NUMA node:

### lsmod

- list all the modules used by Linux Kernel
    - vboxdrv, nvidia, drm(nvidia),
- modinfo
    - to see module information

### lsof

- whatitis
    - list open files
    - list open files and process, device info, file kinds, etc
- output
    - command PID USER FD TYPE DEVICE SIZE/OFF NODE NAME
        - FD: file descriptor
            - cwd: current working directory
            - rtd: root directory
            - mem: memory-mapped file
            - txt: program text (code and data)
        - TYPE: file kinds
            - DIR: directory
            - CHR: character special file
            - REG: regular file
            - unix: unix domain socket
- Usage
    - filename
        - show process which the file uses&#9;cf. fuser
    - +D /tmp
        - show open files in the path
    - -i TCP:22
        - protocal:port
    - -i TCP:22-80
        - define port range
- sudo lsof -iTCP -sTCP:LISTEN -P&#9;&#9;cf. iptables
    - list the services that are running
- sudo lsof -i -P -n \| grep LISTEN
    - options
        - -i: listing ports
        - -P: inhibit the conversion of port number to port name
        - -n: do not use DNS name

### lspci

- show pci bus and devices
    - pci: graphic card, vga card

### mkdir –p

### mkfs

- whatitis
    - after making partition through gdisk
    - making file system with format
- usage
    - mkfs –t ext4 /dev/sdd1
        - ext4 for linux data file system
- further work for automatic mounting of harddisk driver
    - present
        - not displayed in “ls /”
    - include device of /dev/sdd1, /dev/sdd2 in /etc/fstab using uuid

### modinfo

- sudo modinfo module\_name
    - module\_name from lsmod

### mount/umount

- pre
    - check partition
        - fdisk -l
- ` make dir to mount a device at `
    - e.g. mkdir /mnt/win
- mount
    - mount /dev/sdc1 /mnt&#9;# mount device of window at /dev/sdc1 at /mnt
        - if there is no error message, it succeeded
    - mount –a
        - validate the modified fstab
    - bash script for mount
        - bach AFTER\_BOOT.sh
- umount to disconnect between system and device such as disk, directorys
    - umount /mnt or umount /dev/sdc1

### nm

- name (?): list symbols from object files
- for each symbol
    - general
        - lower case: local symbol
            - some are global symbols (u, v, w)
        - upper case: global
    - U: the symbol is undefined
    - T: defined

### passwd

- options
    - -u id:&#9;
    - if not asking passwd
        - sudo passwd userid
            - New password
        - sudo passwd -d userid&#9;&#9;! for deletion

### pgrep

- pgrep searches running processes &#9;&#9;cf grep
    - directly queries the process table
- w. top
    - top -H -p $(pgrep VirtualBoxVM)

### ps

- show all the processes
- options
    - -ef:

### scp/rcp

- option
    - port
        - scp -P 1234 files destination&#9;&#9;! N.B. P is capital
            - destination: [joonho@chi.kaist.ac.kr:~](<mailto:joonho@chi.kaist.ac.kr:~>)
                - there should be “:”
- usage for kisti
    - from eta
        - rcp x2232a02@nurion.ksc.re.kr:/scratch/x2232a02/SnO2/s002.tar .
    - from pt
        - scp x2232a02@nurion.ksc.re.kr:/scratch/x2232a02/SnO2/s002.tar .

### ssh

- option
    - port
        - ` ssh -p 1234 server `

### sensors

- whatitis
    - check cpu temperature
- After installing lm-sensors
    - Sudo apt-get install lm-sensors

### service

- usage
    - service service\_name subcommand
        - e.g.
            - service httpd start
        - the same as
            - systemctl subcommand service\_name.service
            - e.g.
                - systemctl start httpd.service
    - subcommand
        - save, start, restart, etc
- when iptables is modified
    - service iptables save
    - service iptables restart

### shopt

- cannot find it with “which”
    - builtin command to set and unset Bash shell options
- shopt
    - shows current setting
- options
    - -s direxpand
        - when dir or fname expansion, do not add \\ in front of $
        - bash tab autocompletion back slash
            - do not add back slash

### smartctl

- Whatitis
    - Self-Monitoring Analysis and Reporting Technology
    - harddisk driver check
    - If SMART support is available
    - Cf.
        - sudo badblocks –v /dev/sda
        - gsmartcontrol
            - graphical interface
- usage
    - sudo smartctl –a /dev/sda \| less&#9;
        - w/o sudo shows different output
- output
    - overall-health …: PASSED
        - readable but does not guarantee the safety
    - ATTRIBUTE
        - 1 Raw\_Read\_Error\_Rate
        - 3
        - 7
        - 197 Current\_Pending\_Sector
            - RAW\_VALUE indicates how many of the hard disks sectors can no longer be read and waiting for re-mapping
- SMART Test
    - test
        - smartctl -t short /dev/sdb
    - display test results
        - smartctl -l selftest /dev/sd

### split

- to split large file into pieces
- usage
    - split options file “prefix”
        - split -b 10M a.tar.bz2 “a.tar.bz2.part”
    - recover again
        - cat a.tar.gz2.part\* \> a.tar.gz.joined
- options
    - -b
        - e.g.
            - 10M

### ss

- sudo ss -tulpn&#9;&#9;&#9;cf. open port
- similar to netstat

### startx

- in shell, if X is installed, you can run X

### systemd

- whatitis
    - service is referred to as a unit
    - unit is a resource
- upto centos 6, run level of SysV init
    - in boot
        - kernel is loaded on memory
        - init process
            - init script
            - init setting
                - RunLevel
                - execution script following each init script
- cento 7: Systemd
    - system booting process
    - Service Management
    - cgroup manages process resources
    - manage service process
        - so called, Daemon
- Systemd command
    - systemctl
    - systemd-analyze
    - systemd-cgls
    - systemd-cgtop
    - systemd-loginctl
- e.g.
    - present service list
        - #systemctl

### systemctl

- whatitis
    - examining and controlling the system systemd and service manager
    - system control
        - cf. systemd
    - form
        - systemctl subcommand servicename.service
        - the same as
            - service servicename subcommand
- systemctl
    - subcommand
        - start &#9;&#9;&#9;! start
        - restart &#9;&#9;&#9;! restart
            - when you modify configuration file such as httpd.conf
        - stop &#9;&#9;&#9;! stop
        - enable&#9;&#9;&#9;! active after booting
        - disable&#9;&#9;&#9;! inactive after booting
        - mask&#9;&#9;&#9;! dismiss
        - unmask&#9;&#9;&#9;! register
        - try-restart &#9;&#9;&#9;! when service is running, restart
        - reload &#9;&#9;&#9;! setting and restart
        - status&#9;&#9;&#9;! confirm whether it is running or not
        - is-active&#9;&#9;&#9;! confirm
        - list-units --type service --all&#9;! status of all the services
        - , unmask, enable, get-default, set-default
    - servicename
        - httpd
        - firewalld&#9; fwupd
- check service status
    - systemctl status servicename.service
    - systemctl status servicename
        - systemctl always looks for \*.service
    - status
        - could not be found
            - means it is not installed
        - Active: inactive (dead)
            - means not installed
            - first install the-list
- order in command
    - when cannot start
        - unmask → start → enable
    - from install
        - install → unmask
- start and stop
- restart or reload
    - restart
        - starting it manually
    - reload
        - already running but if any configuration is changed, reload
    - reload-or-restart
        - if you are not sure
    - error
        - failed to restart … Unit is masked
- enable or disable
    - such as cloud server, there are lots of service automatically started
        - httpd, MySQL, MariaDB etc
- unmask
    - systemctl unmask firewalld
    - error
        - if not installed, first install
        - ` yum install firewalld `
- isolate
- get-default
    - differs from the value of /usr/lib/system/system/default.target
        - graph: graphical.target
        - text: multi-user.target
- set-default
    - systemctl set-default graphical.target
        - change to graphical login window

### unit states

- systemctl list-units --all
    - systemctl list-units --all --state=failed
    - systemctl list-units --all --type=mount
    - systemctl list-unit-files
        - STATE
            - enabled
            - disabled
            - static
                - donot have install section, cannot be enabled
            - masked
                - will not be able to start it
        - e.g.
            - systemctl start servicename
                - failed to start servicename: unit is masked
            - systemctl unmask servicename
- manipulate unit file
    - creating
        - touch /etc/system/system/servicename.service
    - view
        - systemctl cat servicename
    - view dependency
        - systemctl list-dependencies servicename
    - view properties
        - systemctl show servicename
    - edit
        - systemctl edit httpd.service
            - creates a directory in /etc/system/system/httpd.service.d
                - edits is stored here
            - this override the main unit file
    - remove
        - rm /etc/systemd/system/httpd.service
        - rm -r /etc/system/system/httpd.serivce.d
        - to apply the change
            - systemctl daemon-reload
- list targets
    - systemctl list-unit-files --type=target
    - systemctl list-units --type=target

### su

- substitute user/switch user
- su \[-\] \[user\]
- \[-\] option
    - login with reading initial files
    - w/o -: do not read /root/.bashrc /root/.bash\_profile
- \[user\] option
    - substitute user with \[user\]
    - w/o \[user\]: su to root
- option –c
    - single command option
        - su –c command
        - su –c “command”
        - sudo command
    - require root passwd
    - similarity to sudo

### sudo

- need to install
    - ` apt-get install sudo `
    - if it doesn’t work, check sources.list
- usage
    - ` make user have root permission to correct system `
        - Ubuntu doesn’t have root
            - if you did not make root passwd at installing, make it
                - sudo passwd root&#9;cf. passwd
    - login with user passwd
- option
    - -i
        - sudo –i
        - same as su
        - require user passwd
- find sudoers
    - getent group sudo&#9;! not sure whether this is working
    - use id or groups
        - id: to check my current id’s group
        - groups: find the present user’s groups
- add user sudo authority
    - not working
        - adduser joonho sudo
            - try at the moment when making id
        - use usermod for wheel
    - edit sudoers file
        - open
            - #visudo
            - # vi -f /etc/sudoers
        - edit
            - find “root ALL=(ALL) ALL”
            - add “id ALL=(ALL) ALL”&#9;&#9;! id==joonho

### uname

- sys\_name hostname kernel\_version … date
- option
    - -a: all
    - -m: hardware type
    - -n: hostname
    - -r: OS release
        - kernel version
    - -s: OS
    - -v: OS version

### useradd

- ` make username					cf adduser `
    - not make password automatically
    - not automatically generate home directory
    - passwd username
        - firstly set passwd
- add secondary group to user
    - useradd –G Groupname Username
- Making ID (sudo)
    - /usr/sbin/useradd joonho
        - Useradd –d /home –u uid –g group –s tcsh
    - /etc/passwd : confirm that the ID:Joonho was generated in /etc/passwd
        - How to define group(e.g. 500) ?
    - ` chown –R Joonho:ysj filename (/home에서 owner:group, filename would be ID(owner) `
        - -R: change all the sub directory and files
            - Joonho Joonho will change just owner
    - Chgrp clients filename
- Chsh –s /bin/tcsh Joonho
- Putty login failure

### userdel

- userdel -r id
    - remove home directory
- option
    - -r, --r : remove home directory which means complete deleting

### usermod

- what it is
    - change or modify user attribute
        - do not modify /etc/passwd using vi
    - format
        - #usermod \[options\] USER
            - only root or sudoer
- options
    - -u : assign UID
    - -g : assign first GID&#9;&#9;&#9;cf groupmod
        - if usergroup already exists and want to a user’s primary group to be usergroup
            - usermod -g users saheb&#9;&#9;cf
        - assign a primary group to user  change group name cf. create user
        - #usermod -g pgroupname username
            - -G refers to a secondary group
            - need to change group of the old files&#9;cf. chgrp
    - -l : change login name, so the home directory should be changed manually
        - usermod -l login-name old-name
    - -d: assign home directory
        - usermod -d Absolute\_path USER
        - to move contents in the old home
            - usermod -d Absolute\_path -m USER
    - -s: to change default shell
        - usermod -s /usr/bin/bash USER
        - check available shell
            - cat /etc/shells
- usage
    - assign secondary groups to user
        - -a keeps already existing secondary groups intact
            - otherwise they will removed
        - #usermod -aG group user
        - #usermod -aG wheel joonho
        - makes joonho as sudoer  cf centos
- ID
    - check UID & GID
        - $id
        - ` grep ‘^joonho’ /etc/passwd `
        - ` grep ‘joonho’ /etc/group `
        - groups joonho
            - USER : GROUPS
        - home directory
            - ls -ld /home/joonho
- change UID
    - usermod -u 1002 joonho
        - id of joonho becomes 1002
        - home directory will change automatically
    - in case running process
        - pkill -u joonho pid
        - pkill -9 -u joonho
- change GID

### vipw & vigr

- password, group, shadow-password, shadow-group
- vipw
    - edits /etc/passwd
    - vipw –s
        - edits the shadow secure version of /etc/passwd
- vigr
    - edits /etc/group
    - vigr –s
        - edits the shadow secure version of /etc/group

### virtualenv

### w

- whatitis
    - to show who is logged on and what they are doing
- usage
    - w \[option\] user \[…\]
- option
    - -h: don’t print header
    - -u: ignore username
    - -s: short format
    - --help
    - -i: ip address instead of hostname
    - w user: about the specified user only
- cf
    - ‘who’ shows only connection users with ip

### watch

- refresh a command in every set time
    - monitoring a command result
    - input command repeatedly default 2 seconds
- options
    - -d, --differences\[=cumulative\]
        - highlight the changes between successive updates
        - cumulative make the highlights sticky
    - -h: for help
    - -n, --interval=\<seconds\>
        - default = 2
    - -t, --no-title: turn off showing the header
- basic usage
    - watch \[-d\] \[-n seconds\] ‘command’
        - command is combined with ‘ ‘ when blank is included
        - watch -d=cumulative -n 600 “df . -h”
    - ^c: for finish
- advanced
    - watch runs function
        - watch -d ‘kpy qst.py’&#9;&#9;&#9;
            - kpy is user-made function&#9;&#9;&#9;cf bash function
            - qst.py is constant  if you want to get argument for kpy function
    - watch runs function (watch function) with argument
        - define function with argument
            - function gt \{ grep F= $1 \| tail -20; \}&#9;&#9;# gt: grep and tail
            - ` export -f gt		# to be used in bash script cf. bash function `
        - watch function with function argument
            - function wgt \{ watch -d -n 60 “gt $1”; \}
                - for variable expansion, use double quote
- e.g.
    - watch -d ls -lrt
    - watch -d -n 5 ls -alrt
    - watch uptime
    - watch -d -n 5 ‘cat /proc/uptime’
    - watch -n 10 iostat
    - watch -n 5 vmstat
    - watch -d -n 1 ‘ps -ef\| grep httpd\| grep -v grep’&#9;# apache process monitoring
    - watch -d ‘w; echo ; df -h; echo; free -m’&#9;&#9;# several command

### wget

- ` wget –r –p http::/address `
    - require the address of the file, driver

### xset

- usage
    - xset -dpms s off
- whatitis
    - ` ssh was disconnected after night `
        - syntom
            - client\_loop: send disconnect: Broken pipe&#9;&#9;cf. ssh

## installed utility command

### curl

- Client URL
    - using protocols transfer data to server or download data from server
    - protocols
        - http/https/ftp/scp/telnet/smtp/pop3/ldap
- Install
    - ` sudo apt install curl `
    - ` yum install curl libcurl libcurl-dev `
- options
    - -L, --location
    - -o, --output FILE
        - save as FILE
    - -O, --remote-name
        - use remote name
    - -I domain\_name
        - get info or server
        - ` curl -I chi.kaist.ac.kr `
- e.g.
    - install pwsh
        - ` curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo `
    - upload file to [NOMAD](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\AMP_ASE_NanoCore.docx>)
        - ` curl -X POST 'http://nomad-lab.eu/prod/v1/api/v1/uploads?token=REDACTED' -T <local_file> `

### pwsh

- whatitis
    - power shell
- install
    - download
        - ` curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo `
    - update yum package repository cache
        - ` sudo yum makecache `
    - ` sudo yum install powershell `
    - check installation
        - pwsh --version

### vi

- mode
    - base
    - edit
    - : command
    - /search
- contents
    - mark (m), macro command (qa-q, @a), edit swap file
- encoding
    - present: UTF-8 unicode
- automatic linked to vim in Debian
    - ` which vi `
        - /usr/bin/vi
    - ls –al /usr/bin/vi
        - -\> /etc/alternatives/vi -\> /sur/bin/vim.tiny
- four modes
    - base mode
        - cursor movement
            - 1 step: h, j, k, l
            - Word: w, W, b, B, e, ge, gg, G, ^, 0, $
                - ^, $ (?) &#9;line or sentence
            - line
                - :line\_number
                - nG
            - 1<sup>st</sup> line
                - 1G, gg,
                - \[\[: 1<sup>st</sup> line inside function
            - end line
                - G, :$
                - \]\]: last line inside function
            - ^e: roll up
            - ^y: roll down
        - delete
            - dd&#9;delete one line
            - Nd&#9;delete N line
            - dw&#9;from the cursor to the beginning of the next word
            - d$ or D:&#9;from the cursor to the end of line
            - dG:&#9;from the cursor to the end of file
        - yank
            - yy&#9;1 line yank
            - Nyy&#9;N line yank
        - paste
            - p&#9;paste data in the last buffer
        - undo
            - undo from the last change
                - Nu
                    - undo N step
                - :u
                - :undo
                - U: undo all latest changes on one line
            - for redo
                - :redo
        - select block
            - ^v + move-cursor&#9;select square box
            - to cancel: esc X more than 3
        - two windows
            - ^w + v\|h&#9;&#9;vertical/horizental
            - ^w + direction-key&#9;hop to other window
    - editing mode
        - i&#9;! insert
            - \<F9\> changes paste toggle
                - toggle w/w.o tab key at front
        - a&#9;! append
        - “Esc” to exit editing mode
    - : command mode
        - :w, :wq, :q!, :q,
            - write, write and quit, forced quit without save, quit
            - :w a.txt
                - save to new file
        - add line number
            - :set nu
                - == :set number
            - :set nonu
                - == :set nonumber
        - :e, :edit, :e!, :edit!
            - when file is encoded, the buffer is presented
            - :edit!
                - ignore the correction done by other source and let the present file to editing mode  this file becomes swap file, and another swap file if exists, removed.
            - remove swap file (or hidden file)
                - r for recover when open file
                - :e!
                    - asking whether delete  delete
                - you can get out and reload without asking
        - show filename
            - :f
                - show just the filename
            - 1 + ^g
                - file name with full path
        - color change
            - blue is not clear in black background
            - :colorschem
        - case insensitive search
            - :set ignorecase
            - :set smartcase
                - /copyright&#9;&#9;# case insensitive
                - /Copyright&#9;&#9;# Case sensitive
                - /copyright\\C&#9;# case sensitive
                - /Copyright\\c&#9;# case insensitive
            - :help /\\c
            - :help /\\C
            - :help ‘smartcase’
        - substitution
            - %s/pattern/new/&#9;&#9;!all the line
            - 1,5s/…&#9;&#9;&#9;! for the lines
            - ,$s/…&#9;&#9;&#9;! from line to the end
        - redo
            - ^R \| :redo
            - N^R
    - / search mode
        - #&#9;find the present word backward
        - \*                 “               forward
        - continuous search
            - n/N in cursor mode
        - case insensitive&#9;&#9;&#9;cf also setting with :
            - \\c
                - as for /copyright
                - /\\ccopyright, /copyright\\c, /copyri\\cght
            - \\C for sensitive
        - search whole word
            - e.g. search atom not atoms
            - \\\<pattern\\\>
            - /\\\<atom\\\>
- block setting
    - select block
        - in a certain position, ^v then move cursor to select rectangle
        - possible actions
            - d (delete) y (yank)
    - block shift left or right
        - set 1 column ( 1 row if not move cursor )
            - shift + \>\|\<
            - N\>, N\< are possible
    - block editing just by one line
        - set column block
        - shift I
        - edit the 1<sup>st</sup> line
        - esc
            - the editing applies to all the lines in the block
- special function
    - mark
        - mark and cursor move
            - ma
                - m\[a-zA-Z\]
                - mark the present position as ‘a’
            - ‘a: to the mark-a line
            - \`a: to the mark-a position
        - ‘’ or \`\`: to the previous cursor position
    - buffer
        - ` vi reserves 9 buffers `
            - to the buffer: deleted, copied, replaced
                - buffer 1
                - earlier buffer 1 to buffer 2
        - to paste the earlier deleted buffer
            - np
            - 1pu.u.u.u.  ?
        - 26 buffers from a to z
            - a3yy: 3 lines copied to a
                - ap: paste a
            - bD: delete from here to the end and copied to b
                - bp: paste b

### vim&#9;&#9;vi-editor

- whatitis
    - keymap, RE, macro recording
    - record,
    - .vimrc make copy & paste possible
    - install vim in debian
        - it is not default
        - ` sudo apt-get install vim `
- contents of vi and vim
    - mark
    - record
- recording
    - q: start of macro recording
        - qa enter
            - a is the name of macro
        - name of macro
            - a - z ?
    - ` make macro operation `
        - now cursor is in line 5
        - operation
            - /int&#9;: find int
            - w&#9;: next word
            - i\_&#9;: insert \_
            - esc&#9;: escape insert mode
            - q&#9;: macro finishes
    - execute macro
        - @a
            - execute macro a
- alias to vi
    - alias vi=’vim’
- install vim in debian
    - ` apt-get install vim `

### .vimrc

- whatitis
    - without .vimrc
        - mouse selection goes to visualize
        - paste writes only e
    - ` make ~/.vimrc `
        - this removes the default function
        - ` make copy & paste possible `
- present file
    - e.g. (debian)
        - filetype plugin on
        - syntax on
            - ! this make vim recognize syntax
            - N.B. only vi does not recognize this sentence
        - set autoindent
        - set tabstop=4
        - set shiftwidth=4
        - set expandtab
        - set pastetoggle=\<F9\>
        - set nocompatible
        - set backspace=indent,eol,start
- modify default
    - autoindent makes copy to repeat tab
        - set paste
            - turn off autoindentation
        - set nopaste
            - turn on autoindentation
    - highlighting
        - centos
            - syntax on
            - colorscheme desert
        - debian 10
            - filetype plugin on
            - syntax on
                - E319: Sorry, the command is not available in this version: syntax on
                - install vim
    - different color scheme
        - ` mkdir .vim/colors `
        - upload your own colorscheme into the colors folder
    - enable backspace
        - set nocompatible
        - set backspace=indent,eol,start
            - do not make space between arguments
    - do not use default setting as root
        - /etc/vim/vimrc
            - uncomment (“syntax on) to (syntax on) for highlighting

## Re/ RegEx/ Regular Expression&#9;cf. perl RegEx

### glob in re

- coming from unix
- global command
    - operation that expands a wildcard pattern into the list of pathnames matching the pattern
- most general wildcard
    - \*
        - match with all the character including nothing
    - ?
        - match with any one character
    - \[…\]
        - match with any one in the square bracket
        - \[a-z\]
            - any one from a to z

### 3 category

- Character, character replication, location or connection

### matching operator

- usage&#9;&#9;&#9;&#9;&#9;cf. bash string
    - \[\[ $var =~ “str” \]\]&#9;&#9;&#9;&#9;cf bash if
    - e.g.
        - if \[\[ $VAR =~ \[0-9\] \]\]; then
- $VAR =~ \[0-9\]
    - if string contains numbers

### Character

- E.g.: egrep ‘GNU’ COPYING : COPYING is filename
- ‘   ‘ : to treat \*, ?, \| differently from shell command
- \*, ?, \| have role in shell command
- ‘\[Tt\]he’
- \[  \]: possible character, matches one of them
- \[a-z\]: two character at both side of ‘-‘. a and z should be ASKII order
- \[^a-z\]: not \[a-z\], ‘^’ should be first character
- ‘th..’
- ‘.’ Match with one character including blank (not new line)
- ‘.’ Has no role in shell command
- first character
    - ^\[a-z\]: start with a-z

### POSIX

- POSIX bracket expressions
- Matches one character out of a set of characters
    - So, enclosed by \[ \]
- E.g.
    - \[:alnum:\]  \[a-zA-Z0-9\] in RE
    - \[:alpha:\]&#9; \[a-zA-Z\] in RE
    - \[:digit:\]&#9; \[0-9\] in RE
    - \[:lower:\]
    - \[:space:\]  \[ \\t\\r\\n\\v\\f\]
        - /^\[\[:space:\]\]\*NCORE/
            - ^ start, \[  \]\* 0-infinity times, \[:space:\] any white space
    - \[:upper:\]
    - \[:word:\]&#9; \[A-Za-z0-9\_\]

### Replication (\*, ?, +) and unit ( )

- \*; the previous unit 0 or infinity
- (ab)\*; the previous unit (ab) 0 or infinity
- ?; 0 or 1
- +; 1 or infinity
- a+ is same as aa\*
- It finds the longest match
- \<B\>com\</B\> and \<B\>end\</B\>
- ‘\<B\>.\*\</B\>’ does not finds ‘\<B\>com\</B\>’ but ‘\<B\>com\</B\> and \<B\>end\</B\>’, the longest match
- To find ‘\<B\>com\</B\>’ use ‘\<B\>\[^\<\]\*\</B\>’
- (as)\{n\}, \{n,\}, \{n,m\}
- \{n\}: repeat n turns
- \{n,\}: repeat n or over n
- \{n,m\}: repeat from n to m

### Connection: ^, $, \|, \\\<, \\\>  cf grep

- ‘^\[Tt\]he ‘
    - at the start of a line
    - ‘The ‘ or ‘the ‘ should be first in the line
- ‘te$’
    - The line is ended with ‘te’
- ‘this\|This\|that\|That’
    - Selection one of them
    - Equal to ‘\[Tt\]is\|\[Tt\]hat’
- ‘\\\<the\\\>’
    - ‘\\\<’ from blank to character
    - ‘\\\>’ from character to blank

### Special character

- \[  \]: only ‘^’ and ‘-‘ are special character
- \[^asdg\]: to find not-matched with the characters
- To use not matched –
- Eg: \[^-a-zA-Z0-9.\_\]+
- To find special character
- Out of \[ \]
- Use escape
- ‘what\\?’
- Use square bracket
- ‘what\[?\]’
- In \[  \]
- Almost special character becomes general character in \[ \]
- \[abd^\] to find ‘^’
- \[-adb\] to find ‘-‘

## Environment

### manager setting

- bash
    - /etc/bashrc
    - ` make file /etc/bashrc `
- tcshrc

### user setting

- bashrc
    - .bash\_profile
        - call .bashrc
    - .bashrc
        - set env variables and aliases

### ssh/config

- ` vi .ssh/config					cf. ssh_config `
    - Host name
        - name might be different from domain name
        - Hostname kdft.kaist.ac.kr
            - kdft.kaist.ac.kr might be ip
        - User joonho
        - Port 22
    - ---repeat above
- X forwarding error
    - mod in $HOME/.ssh/config

Host \*

ForwardAgent yes

ForwardX11 yes

ForwardX11Trusted yes

XAuthLocation /usr/bin/xauth

- connection
    - ` ssh kdft `
    - ` ssh –Y kdft `
- graphic

### prompt, dircolor

- present directory
    - ini file of tcsh == .tcshrc
    - set prompt = ‘%/ % ‘
        - %/ for present directory
        - \_%\_ for prompt with blank

## Environment Modules

### whatis

- before: initialize environment when they log in by setting in .bashrc initial file
- easily modify environment during the session with modulefiles
- how to use: module subcommands

### install

- source
    - [http://modules.sourceforge.net](<http://modules.sourceforge.net>)
- requirements
    - tclsh equal to or over 8.4
        - whatitis
            - tchsh is a part of Tcl
            - do not install psychotic version
        - install tcl in centos
            - ` yum install tcl `
        - version check
            - tclsh
                - % puts $tcl\_version
    - bash, make, sed, grep, cut, runtest
        - debian
            - runtest \<- in the dejagnu \<- expect
            - ` aptitude install expect `
            - dpkt –I dejagnu…deb
            - ` which runtest `
        - centos: yum install dejagnu
            - it will make error if psyco-tcl installed
    - install gettext, gettext-dev for autoconf, automake, autopoint, gcc, tcl-devel
        - tcl-devel \>= 8.4 version
            - ` echo ‘puts $tcl_version; exit 0’ | tclsh `
        - no autopoint in /usr/bin/autopoint
        - centos
            - ` yum install gettext gettext-dev `
    - sphinx
        - ` sudo yum install –y postgresql-libs unixODBC `
            - no postgresql-libs
        - ` wget http://sphinxsearch.com/files/sp....rpm `
            - the file is downloaded
        - ` sudo yum install –y sphin…rpm `
        - this is not python version
- installation
    - systems
        - ubuntu
            - ` apt-get install environment-modules `
                - if bash doesnot look good
                - $module  working
            - ` apt-get install tcl `
            - No more setting is required
                - relogin
            - .bashrc
                - ` module load use.own `
                - ` module av   if use.own is loaded, that’s OK `
    - download
        - [https://github.com/cea-hpc/modules](<https://github.com/cea-hpc/modules>)
    - configuration
        - new try \| failed
            - ` ./configure --prefix=$HOME/.local/Modules --modulefilesdir=$HOME /.local/Modules/modulefiles `
            - still looking for /usr/local/Modules…….
        - ` ./configure `
            - ` make Makefile.inc using Makefile.inc.in `
            - “modulerc” will be initial file
            - error Tcl configuration (tclConfig.sh) not found
                - ` apt-get install tcl-dev tk-dev mesa-common-dev libjpeg-dev libtogl-dev `
        - or ./configure –enable-dotmodulespath
            - “.modulespath” will be initial file
        - error: TCL\_LIB\_SPEC missing user --tcl-lib-dir=…
            - ` yum install tcl-devel `
                - this gives /usr/lib64/tcl8.5/tclConfig.sh
                    - ` which has so many environment variable such as TCL_LIB_SPEC `
            - ` cd /usr/lib64/tcl8.5 `
            - sh ./tclConfig.sh
                - then ./configure work in module source directory
    - make
    - ` make install `
        - generate /usr/local/Modules
        - where is default?
            - /usr/share/Modules or /usr/local/Modules
            - in tcsh
                - ` setenv MODULEHOME /usr/share/Modules `

### configuration

- Install directory
    - debian: /usr/local/Modules
    - ubuntu: /usr/local/modules
- tune the initialization scripts
    - N.B: still module command is not working
- enable module and Modules initialization at shell startup
    - using system-wide environment setup in&#9;&#9;! now this is set
        - /etc/profile.d
        - ` ln -s /usr/local/Modules/init/profile.sh /etc/profile.d/modules.sh `
            - 1: module is running at booting time
    - sourced from user initial file
        - bash
            - in ~/.bashrc
                - ① source /usr/local/Modules/init/bash
                    - then modulerc is called
                    - ` module command appears `
            - how to check
                - ` source .bashrc	! module is activated `
                - $module&#9;&#9;! just type, it cannot be seen “which module”
                - PATH includes /usr/local/Modules/bin but module is not there
        - tcsh (?)
            - ~/.tcshrc
                - ` setenv MODULEHOME `
            - ②$MODULEHOME/init/modulerc \{.modulespath\} runs
                - ②in $prefix/init/.modulespath (?)
                    - modulefiles directory is set
                    - Fe/Pt
                        - /TGM/local/etc/modulefiles
- 2: modulerc sets the first module path
    - default
        - modulerc loads module path of modulefiles, which enable to use module files such as use.own
        - $prefix/init/modulerc
            - defines the initial setup for the modulefiles search path
                - e.g.
                    - ` module use path `
                    - ` module load mod `
            - ` module use --append {/usr/local/Modules/modulefiles} `
                - “use --append” for setting modulepath
                    - ` module paths are set here `
                - all the modulefiles including subdirectories are shown by “module av”
    - ` ./configure --enable-dotmodulespath `
        - $prefix/init/.modulespath
            - /path/to/regular/modulefiles&#9;&#9;for each dir
- use.own
    - in the first default modulepath has “use.own”
        - set personal modulepath more here using
            - ` module use --append $HOME/privatemodule_dir `
    - ` module load use.own `
        - 3: by loading use.own, the personal modulepath in use.own is shown by “module av”
    - in case --enable-dotmodulespath
        - .modulefiles initiate default modulepath
            - in the default path, there are some modules including use.own
- configuration detail
    - path and location
- [configuration in python](<file:///C:\Users\jhPark\AppData\Roaming\Microsoft\Word\python_c++.docx>)
- configuration test
    - ` module avail `
    - to check module loaded
        - relogin or source .bashrc
        - ` module li `

### error: do not set default in boot

- boot
    - .bashrc
        - ` module use own		! only active this `
    - after booting,
        - .bashrc can import module
- after booting
    - .bashrc
        - ` module load all_the_working_module `
    - then the terminal after setting will load modules in .bashrc
- error in boot level import
    - PYTHONPATH\_modshare collides:
        - WARNING: PYTHONPATH\_modshare exists ( /home/joonho/sandbox\_gl/pycommon:1:/home/joonho/sandbox\_gl/mymplot:1 ), but PYTHONPATH doesn't. Environment is corrupted.

### module [sub]command

- how to use
    - in shell
        - module&#9;! displays manual
    - in modulefiles
        - the same command as linux shell
    - format
        - ` module subcommand argument `
- use
    - ` module use [-a|--append] dirname `
        - prepend dirname to $MODULEPATH
            - -a for append
- avail \| av
    - all the available modules in the current MODULEPATH
    - all the directory is searched recursively and find files with modulefile magic cookie
- list \| li
    - list loaded modules
- load, unload, reload
    - load modulefile: upload module
    - unload modulefile: remove module
    - reload modulefile: unload and load
- display modulefile
    - display all info
- whatis modulefile
    - display info set up by module-whatis command in modulefile
- initadd modulefile
    - try
        - add modulefile to the shell’s initialization file
        - b shell
            - .modules, .profile
    - error: it removes the initial PATH
    - ` module initrm modulefile `
        - recover the initial condition
- test modulefile
    - is not working

### locate modulefiles

- properties
    - written in the Tool Command Language, Tcl
    - interpreted by the modulecmd.tcl program in $install\_home/libexec
    - can be loaded, unloaded or switched on the fly
- format
    - begins with the magic cookie, ‘#%Moduleversion’
    - Modules specific Tcl commands
    - “Module subcommand” can be used
        - ` module use –a directory		! in modulefile `
- contents
    - the changes to a user’s environment needed to access an application
    - a typical module file: a simple bit of code that set or add entries to the MODULEPATH, MANPATH, or other environment variables
- Modules specific Tcl commands
    - append-path
- configuration \|\| location
    - MODULEPATH
        - every directory in MODULEPATH is searched to find modulefile
            - modulecmd.tcl looks for
                - modulerc file
                - if .version exists
                    - the version will be default
                    - it affects the current directory
                - .modulerc directory
    - first module file to be read is “use.own”
    - when load use.own, /home/joonho/privatemodules is activated
    - other directory can be activated here

### Environment variables

- ModulesCurrentModulefile: full pathname of the modulefile being interpreted
- MODULEPATH: every directory here is searched to find modulefile
    - if modulefile is a directory, it is open and all the modulefiles are loaded
    - first modulecmd.tcl looks for a file in .modulerc
    - how to add directory to MODULEPATH

### modulefile

- whatis
    - information needed to configure the shell for an application
        - instruct module command to alter or set shell environment variables such as PATH, MANPATH
    - files containing Tcl code for Modules package
    - modulefile uses extensions to the standard Tcl
        - modulefile keyword = module-only keyword + Tcl keyword
    - interpreted by modulecmd program
    - magic cookis ‘#%Module’ and version number follows.
        - #%Module1.0&#9;&#9;# 1<sup>st</sup> line
        - without this line, the file is not interpreted by modulecmd
    - each modulefile contains the changes to a user’s env
    - typical
        - set or add entry to PATH, MANPATH or other environment variables
    - version control
        - tcl – conditional statement
- notation
    - #: do not use single # natation
    - comment: ###
- break
    - overloaded command from Tcl
    - exit the modulefile if it is not in a loop
    - the module is unloaded
- chdir directory
- continue
    - exit the module file but it is loaded
- set
    - usage
        - set var value
        - set qchome $HOME/sciwares/QChem
    - define variable in the scope of script
    - get shell env variable
        - set HOME $::env(HOME)
    - referenced by $
        - set QCHOME&#9;$qchome
- ` setenv (module only) `
    - whatitis
        - change the process’ environment
        - the env value is overloaded
            - when “module unload” the env variable is empty, the previous value is not restored
        - env variable cannot be reference in the script
            - even defined env-var cannot be referenced
    - usage
        - ` setenv var value `
        - ` setenv QCHOME	$qchome `
- source
    - only source tcl script not shell script
- puts
    - usage
        - tcl keyword
        - write only one argument
        - puts channel argument
    - puts stdout “source $qc/bin/qchem.setup.sh”
        - can source shell script
- exec
    - usage
        - exec /usr/bin/bash –c “source $qc/bin/qchem.setup.sh”
            - sometimes not working
- \[pre\|ap\]pend-path \[-d C\] var value
    - usage
        - prepend-path PYTHONPATH $ana\_bin
        - prepend-path PATH $ana\_bin
        - prepend-path MANPATH $manpath
        - prepend-path LD\_LIBRARY\_PATH $MPICH\_HOME/lib:$MPICH\_HOME/include
    - prepend or append value to env variable.
    - delimiter
        - default: “:”
- prereq\|conflict modulefile
    - control whether or not the modulefile will be loaded
    - multiple modulefiles act as OR
    - multiple prereq\|confilic act as AND
- is-loaded, is-saved, is-used \[modulefiles\|directories\]
- is-avail modulefiles
- ` module subcommand arguments `
- module-info option args
    - module-info type&#9;&#9;! returns C or Tcl
    - module-info mode \[modetype\]
        - return 1 if mode == modetype
    - modetype: load, unload, remove, switch, display, help, test, whatis
- module-version
- module-whatis string

### chi vs psi structure

- psi
    - auto source .tcshrc
        - load use.own
            - ` module path to /home/joonho/privatemodules is included `
        - load /home/joonho/privatemodules/common\_moduledir
            - ` module path to /qcfs/joonho/privatemodules is included `
                - all the module files have source in /qcfs/joonho/sandbox
        - /qcfs/joonho/privatemodules/mod\_source
            - set MODULE\_HOME &#9;/qcfs/joonho/sandbox
            - set MODULE\_INI&#9;&#9;/qcfs/joonho/privatemodule
        - sourced by files in /qcfs/joonho/privatemodules
            - ` source mod_source `
                - error if not run in /qcfs/joonho/privatemodules
            - fixation
                - ` cp mod_source to home `
                    - ` cp mod_source ~/ because .tcshrc runs in $HOME `
                - or, move to /qcfs/joonho/privatemodules before load
                    - .tcshrc
                    - ` module load /new dir/privatemodules/common_moduledir `
                    - ` cd //new_dir/privatemodules `
                    - ` module load pycommon, pyvasp, etc `
- ` rsync to chi `
    - just change mod\_source
        - set MODULE\_HOME /home/joonho/sandbox
        - set MODULE\_INI /home/joonho/privatemodules

## Cluster

### Hardware install

- Lan
    - Master: 3
        - Extra for ip from outside
    - Node: 2
        - 1st is for storage communication
        - 2nd is for calculation communication

### Node information

- $qnodes
    - commander: show the nodes
- hosts: hostfile
    - $more /etc/hosts

### pcp

- Copy some files to all the nodes
    - pcp /etc/passwd /etc
    - pcp /etc/shadow /etc
    - pcp /etc/group /etc
    - for scratch for qchem &#9;&#9;(in user id)
        - pexec mkdir /scratch/joonho (in qch: /disk2/scratch/Joonho)

### ssh key

- summary for “login without passwd”
    - if not id\_rsa (private key) and id\_rsa.pub (public key)
        - ` make ssh keys by ssh-keygen -t rsa `
            - ssh-keygen -t rsa
                - enter
                - enter
    - copy guest id\_rsa.pub to host .ssh/authorized\_keys
        - scp id\_rsa.pub host@ip:~
        - ` ssh host `
        - cat id\_rsa.pub \>\> .ssh/authorized\_keys&#9;! to append key
            - N.B.: text copy would fail when the key is copied into multiple lines
                - it should be one-line-key
    - vise versa for opposite direction login without passwd
- are there keys?
    - .ssh/
        - authorized\_keys
        - key pair
            - id\_rsa
                - personal key or private key
            - id\_rsa.pub
                - public key
        - known\_hosts
    - if not
        - ` make keys using ssh-keygen `
- what are keys?
    - client private key: should locate in local machine
    - user public key
        - counter part of user private key
        - to allow authorization of the user on a server, the user public key is registered on the server .ssh/authorized\_keys
- ` ssh try `
    - let server not ask passwd
        - copy guest id\_rsa.pub to host authorized\_keys
    - server compare local machine’s public key with authorized\_keys
        - if keys are not matched, it asks passwd whenever login a node
- ` ssh key generation `
    - prerequisite
        - at home
        - ` mkdir .ssh `
        - ` chmod 700 .ssh `
    - ssh-keygen –t rsa
        - to generate public/private rsa key pair
    - enter filename (file location) in which to save the key
        - /home/joonho/.ssh/id\_rsa
            - default directory is ~/.ssh
    - passphrase (long so not word but phrase)
        - enter passphrase (empty for no passphrase)
            - encrypt passphrase into private key
                - 10~30 character
            - for auto login, no passphrase
        - the same passphrase
    - complete with message
        - your identification has been saved … /.ssh/id\_rsa
        - your public key has been saved    .ssh/id\_rsa.pub
    - confirm keys
        - id\_rsa id\_rsa.pub known\_hosts
            - authorized\_keys may not exist
- file explanation
    - id\_rsa: private key, should not be exposed to others
    - id\_rsa.pub: public key
        - be coded (copied) in authorized\_keys of the remote machine
    - authorized\_keys
        - store value of id\_rsa.pub keys of clients
- auto login to server
    - id\_rsa.pub of client should be copied in the authorized\_keys of server
    - copy id\_rsa.pub into $HOME/.ssh/authorized\_keys of remote server
        - manual way
            - scp the client id\_rsa.pub into remote machine
                - scp $HOME/.ssh/id\_rsa.pub [joonho@kdft.kaist.ac.kr:id\_rsa.pub](<mailto:joonho@kdft.kaist.ac.kr:id_rsa.pub>)
                    - donot overwrite server’s id\_rsa.pub
            - add id\_rsa.pub into authorized\_keys file
                - cat $HOME/id\_rsa.pub \>\> $HOME/.ssh/authorized\_keys
        - using ssh-copy-id in guest
            - ssh-copy-id mu.kaist.ac.kr
                - if use $HOME/.ssh/id\_rsa.pub in guest
            - ssh-copy-id –i ~/id\_rsa.pub mu.kaist.ac.kr
                - answer passwd
            - then you can login without passwd
    - if there are several local machine, add each id\_rsa.pub of local machine is added to authorized\_keys
    - in case that client’s id\_rsa is written in a different file, login with
        - ` ssh –i $HOME/auth mu.kaist.ac.kr `
- ` ssh error `
    - ` ssh –v mu.kaist.ac.kr `
        - -vv
        - -vvv

### known\_hosts in cluster

- auto login to nodes
    - first login to nodes using ssh
    - qnodes.sh
- old example
    - procedure
        - login each node
            - this makes “known\_hosts” file in ~/.ssh
        - ` cp id_rsa.pub authorized_keys `
    - miscellaneous
        - check “known\_hosts”
            - if there are not all the hosts, then if you login at each node, key for each node will appear at “known hosts”
        - ` cp id_rsa.pub authorized_keys `
            - at .ssh/ directory
            - Does this make authorized\_keys in each node? Depending on architecture
                - If it is no, to publish public key in the “authorized\_keys” to nodes (this is server in this case. Master node is client and the each node is a server so server should have public key in the “authorized\_keys” file in ~/.ssh)
        - pcp authorized\_keys ~/.ssh (Now it can be omitted)
            - all the nodes have authorized\_keys files in the ~/.ssh directory

### fingerprinter error in known\_host

- amp\_run.py
    - There are problematic in automatic login
    - It ask yes/no whenever login
    - Warning: the RSA host key for 'kdft13' differs from the key for the IP address '192.168.1.13'
    - Offending key for IP in /home/joonho/.ssh/known\_hosts:27
    - Matching host key in /home/joonho/.ssh/known\_hosts:54
    - Are you sure you want to continue connecting (yes/no)? yes

### check ip address and run job

- ping
    - ping node01
        - shows ip address
- AMP
    - cores = \{‘node01’:ncores, ‘node02’: ncores\}
        - cores = \{‘92.168.1.100':ncore, '192.168.1.101':ncore\}  works also
    - Amp(… cores=cores)
    - for job-scheduler
        - qsub … -q skylake@node01 -q skylake@node02 amp\_run.csh

### ssh error

- warning remote host identification has changed
    - IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
    - Someone could be eavesdropping on you right now (man-in-the-middle attack)!
    - It is also possible that the RSA host key has just been changed.
    - The fingerprint for the RSA key sent by the remote host is
    - ea:3f:84:66:bb:8d:ef:5d:aa:e7:39:87:e9:ce:39:1f.
    - Please contact your system administrator.
    - Add correct host key in /home/joonho/.ssh/known\_hosts to get rid of this message.
    - Offending key in /home/joonho/.ssh/known\_hosts:23
        - N.B. this is key in guest
        - remote host key in guest known\_hosts
    - Password authentication is disabled to avoid man-in-the-middle attacks.
- asking passwd
    - copy guest id\_rsa.pub to host authorized\_keys
- Keyboard-interactive authentication is disabled to avoid man-in-the-middle

### Error and problem in parallel job

- When there is not working in a certain node e.g. node22
    - Copy passwd shadow group /home
    - Because after login node22 you can see /home/files(passwd,shadow,group)
    - Then copy under /etc
- System problem
    - When I cannot do ssh to slave node with error message, “Host Key Verification Failed – ssh” (P4 error)
        - Remove all contents in the file, ~/.ssh/known-host
        - Try all the nodes with n1, n2, …
            - For each machine not try alias name
                - Try ssh kdft01; ssh kdft02; and so on &#9;
                - Check known-host
    - Internal IP address is
        - ~/.ssh/known-host
        - 192.168.0.#&#9;: # = 1 ~ 22

## process management

### ps

- ps aux
    - user pid %cpu %mem vsz rss tty state started time
        - vsz: virtual memory size
        - rss: resident set size

### kill process

- pkill name: kill all the processes with “name”
- kill -9 process\_number

### top

- q: soft terminate&#9;&#9;&#9;! linux command top =
    - load average: 5min, 10min, 15min before, the number of load
    - it should be less than the number of process (e.g. 8 processes in the node)
- display
    - E: shows in KB, MB, GB by turn
- sub command
    - kill process
        - k + PID
    - stop top
        - q: termination by program
        - ^c: forced termination of top
    - sort
        - M: by memory
        - P: by CPU
        - T: by running time
        - R: ascending order as default is descending order
- options
    - -H&#9;&#9;show threads instead of processes
    - -p PID&#9;&#9;show only that process
        - with
            - pgrep VirtualBoxVM
- top menu
    - KiB (MiB) Mem: memory by Kilo (Mega) Byte
        - total, free, used
            - 11111111 in 10 GB
            - 11111111+ for 111 GB
- table menu
    - VIRT: total amount of memory consumed by a process
        - program’s code, the data stored in memory, any regions of mem that have been swapped to the disk
    - RES: memory in RAM with %MEM
    - SHR: amount of memory shared with other process

### free

- output
    - total  used   free   shared   buff/cache   available
    - Mem:
    - Swap:
- options
    - -mh
- specification
    - buffers
        - memory used by kernel buffers (Buffers in /proc/meminfo)
        - buffers refers to data that is being written -- that memory cannot be reclaimed until the write is complete.
    - cache
        - Memory used by the page cache and slabs (Cached and SReclaimable in /proc/meminfo)
        - Cache refers to data that has been read -- it is kept around in case it needs to be read again, but can be immediately reclaimed since it can always be re-read from disk
    - buff/cache
        - sum of buffers and cache
    - available

### memory

- structure

Figure 4 Memory structure

- level of memory
    - 1: register in CPU
    - 2: cache mem
    - 3: main mem
    - 4: secondary mem
- top
    - total = real available + real used
        - real available = free + buffers + cached
        - real used &#9; = used - (buffers + cached)
- cache memory
    - special high speed
    - costlier than main memory
    - economical then cpu register
    - buffer between RAM and CPU
- memory check
    - alias.sh
        - runs ps in all nodes if there is the process
            - usage
                - checknodes $1(process\_name)
        - check a node
            - usage
                - checknode $1(node\_number) $2(process\_name)
    - cli
        - node check
            - checknode node13 python
                - check top through ssh
        - kill process if top does not run the job
            - ` ssh node13 pkill python `
            - checknode node13 python

### pgrep

### time

- cpu vs wall
    - cpu time: only time during which cpu contributes the process
    - wall time: real time
- e.g.
    - real time = wall time
    - user = cpu time

## Linux programming&#9;&#9;&#9;&#9;&#9;&#9;

### Compilation

- gcc: compile guider
    - –v&#9;&#9;: verbose
    - –save-temps&#9;: makes a.i, a.s, a.o
- cc1(cc1plus) –E or cpp0&#9;: CPP = C preprocessor, make a.i
    - operation
        - include all the header files in the source file
        - find default dir
        - -I(extra included dir)
- cc1&#9;&#9;: C compiler, makes assembly a.s
    - operation
        - directly make assembly file
- gcc –S main.c&#9;# main.s
    - you can read main.s
- as&#9;&#9;: assembly a.s then make a.o
    - operation
        - as a.o
    - ` make ELF (Executable and Linkable Format) binary format `
- related command
    - readelf –S main.o
- -h&#9;: too see the header of ELF binary file
- ELF
    - Relocatable file: ELF header, section & segment, section header
    - Unrelacatable file: ELF header, program header, section & segment
- ld (collect2)&#9;: linker makes a.out by –o a.out or –o test
    - operation
        - ld a.o b.o … -L/dir  –l/file –o test
            - -l should come after source file
- first connect shared lib (\*.so) if there is not, static lib (\*.a)
- how to see
- gcc –c \*.c or gcc –o test main.c funcs.c –save-temps #make main.o, funcs.o
- ld –dynamic-linker /lib/ld-linux.so.2 –o test /usr/lib/crt1.o /usr/lib/crti.o /usr/lib/crtn.o main.o funcs.o –lc
- actual linking process
- gcc –o test main.o funcs.o # because the gcc compiler and the ld should refer the same linking library crt1.o crti.o (starting)and crtn.o (ending).
- For static lib
- … -o test main.o funcs.o -\\(-lgcc –lgcc\_eh –lc -\\)&#9;# group to find object recursively. Or –start-group –end-group to escape the undefined reference error
- related command for a.o
- objdump a.o
- -D, -j .plt –D, -j .got –s,

### Make Library

- styles
    - static: \*.a
    - shared: \*.so
- Dynamic (shared)
- static library
    - gcc –c \*.c&#9;# make \*.o
    - “mylib.h”&#9;# in the same dir
    - ar rscv libmy.a \*.o&#9;&#9;# archive file
        - ` make my-library as static `
        - s&#9;: index of object file
            - if it was not used, use “ranlib libmy.a” to make index
        - ar –x lib.a&#9;&#9;# extract object files in lib.a
        - ar rus lib.a a.o’s&#9;# add a.o’s
        - ar ds lib.a a.o’s&#9;# delete a.o’s
        - ar t lib.a&#9;&#9;# print file list
- example
    - gcc –o like like.c &#9;
        - In function ‘main’
            - Like.c: undefined reference to ‘func1’
            - Collect2: ld returned 1 exit status
    - gcc –o like like.c –L./
        - The same result
    - gcc –o like like.c –L./ -lmy&#9;&#9;#correct

### shared library

- gcc –fPIC –c \*.o
    - PIC: position independent code
- gcc –shared –W1,-soname,libmy.so.0 –o libmy.so.0.0.0 \*.o # note that there is no space in the “-W1,-soname,libmy.so.0”
- ` ln –s libmy.so.0.0.0 libmy.so	# for gcc link `
- ` ln –s libmy.so.0.0.0 libmy.so.0	# for dynamic link `
    - iii and iv is for dynamic link (/lib/ld-linux.so.2) to find soname
- install for dynamic link to find libmy.so.0.0.0 file
- /etc/ld.so.conf
- $pwd
- ldconfig
    - ` make new /etc/ld.so.cache for dynamic loader to read `
- /etc/ld.so.preload, /etc/ld/so/cache
- nm a.o
- lower case: local
- capital case: global or external
- T: &#9;Typical (a normal definition in a code section)
- U:&#9;used but undefined

## SQL

### install

- hostname
- ` apt-get update & upgrade `
- ` apt-get install mysql-server `
    - use tab for “OK”
    - passwd
    - mysql bind to localhost (127.0.0.1) by default
- sudo mysql\_secure\_installation
    - only for me
- ` which mysql `

### usage

- https://linode.com/docs/databases/mysql/how-to-install-mysql-on-debian-8/
- mysql \[–h\] –u root \[–p\]
    - -h: host if it is not localhost
    - -p: input passwd
    - prompt: mysql\>
- ` make db and table `
    - show databases;
    - create database dbname;
        - user should have ddl authority
    - use dbname;
        - dbname is loaded
    - create table tname( idx int unsigned auto\_increment, name varchar(30), age int, …
    - desc tname;&#9;shows table structure
- for Table
    - insert (DML)
        - insert into tname(name, age, gender, gread) values(‘name’, ‘10’, ‘M’, ‘3’…
            - if there is no column name, the values enter one by one
    - select
        - select \* from tname;
        - select \* from tname where age=23;
        - select name from person where gender=’M’;
        - …

### datatype

- char
    - varchar
    - text
    - int
    - double
    - date
    - datetime

### [pymysql](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\python_c++.docx>)

## Jobs in Linux Env

### image conversion

- jpg to pdf
    - imagemagick package
        - convert a.jpg a.pdf&#9;&#9;&#9;! command line
    - gimp file to pdf
        - file/print/file&#9;extension=pdf
    - gimp
        - rotate picture is saved

### make patch

- whatitis
    - using diff make a patch file and apply it to the original file
- usage
    - apply to a file
        - ` make a patch file `
            - diff -u original\_file new\_file
            - diff -u amp\_orig/\_\_init\_\_.py amp/\_\_init\_\_.py \> amp.patch
        - apply it to original file
            - patch amp\_orig/\_\_init\_\_.py amp.patch
    - can it be applied to a directory?
        - diff -Naur amp\_orig amp \> amp.patch
        - patch -p# amp\_orig \< amp.patch
        - with wrong #, it will display “File to patch: “
            - input filename with path
- options
    - -p#
        - # is number of slash to be excluded in finding a file
        - so when using
            - -p0:

## linux error

### no response

- power off
    - as superuser in command line
        - shutdown
        - reboot
        - poweroff

### to keep Mozilla window

- use shutdown
    - shutdown icon
    - command line shutdown
- <br>

## Machine

## Server Common

### nodefile

- more /etc/hosts
    - listed nodes
- idft: idft01 ~ 22
    - core per node (ppn: processor per node) = 8
- psi: psi01~44
    - ppn = 16
- kdft: kdft01 ~ 24
    - ppn = 12
- rho: rho01 ~ 22
    - ppn = 16

### slurm node management

- initial files
    - /TGM/SLURM/etc
        - slurm.conf
        - gres.conf&#9; gpu
- ` make partition `
    - before make a partition
        - when a node is empty, block to load a job in a certain node
            - scontrol update nodename=n001 state=down reason=none
- Node is down
    - Donot try
        - node rebooting
        - ssh
        - scontrol to node resume
    - check by sinfo -R
        - results
            - Not responding user/slurm NodeLIST
            - ` ssh is possible `
        - diagnosis
            - slurmd is dead
            - slurmctld  slurmd disconnected
            - Munge problem
            - slurmctld restart but register fail
            - No hardware problem
        - ` ssh and run ‘systemctld status slurmd’ `
            - if inactive  slurmd is dead
                - in master
                    - scontrol update nodename=n\[069-092\] state=resume
            - active  Munge or communication problem
                - in node
                    - systemctl status munge
                - in master
                    - munge -n \| ssh n069 unmunge
                - Feb 17 03:08:38 n092.hpc slurmd\[42482\]: slurmd: error: Munge decode failed: Expired credential
                - Feb 17 03:08:38 n092.hpc slurmd\[42482\]: slurmd: auth/munge: \_print\_cred: ENCODED: Mon Feb 16 16:45:10 2026
                - Feb 17 03:08:38 n092.hpc slurmd\[42482\]: slurmd: auth/munge: \_print\_cred: DECODED: Tue Feb 17 03:08:38 2026
                    - time difference
        - if everything is OK
            - scontrol update nodename=n\[069-092\] state=resume
    - confirm Slurm’s view
        - sinfo -N -l : grep n0
            - or: sinfo -N -l \| egrep 'n0(69\|7\[0-9\]\|8\[0-9\]\|9\[0-2\])'
        - check detailed reason
            - scontrol show node n069
- Down-reason
    - scontrol shows
        - State = down
        - SlurmdStart …
        - Reason=Not responding
    - diagnosis
        - slurmctld cannot communicate with slurmd on n069
    - restart slurmd
        - at one time
            - pdsh -w n\[069-092\],gpu systemctl restart slurmd
        - at node
            - systemctl status slurmd
            - systemctl restart slurmd
                - if error, check initial files in /TGM/SLURM/etc
- others
    - reboot by switch
    - as root
        - scontrol update nodename=n046 state=resume

### cluster command

- term
    - NFS: Network File System
    - NIC:
- sinfo
- scontrol
- pdsh
    - parallel distributed shell
        - high-performance, multithreaded command-line utility used for executing the same command on multiple remote hosts in parallel
    - pdsh -w n\[069-092\],gpu systemctl restart slurmd
    - options
        - -w hostnames
            - manually set target host list
            - comma-separation, - range,
        - -x hostnames
            - exclude
        - -a: all hosts listed in a machine file
- pdcp

## PBS

### commands

- commands
    - qsub, qstat, qdel, pestat
- ps x: process in a node (“top” does not show zombie process)
    - pkill qcprog: kill all the process of execution, “qcprog”
    - kill -9 #process: when pkill is not working.
    - ps –aux: to see all the process
- qstat
    - can check
        - current job in the cluster
        - all nodes in the cluster
        - current running jobs
    - current jobs
        - job-id username queue jobname sessID NDS TSK req\_M req\_T S Elap\_T
    - contents
        - State
            - R: running
            - Q: queued
            - H: held (pause during running)
            - C: completed after having run
            - E: exiting after having run
            - W: wait time, qsub with -A
    - alias
        - qs=’qstat -u userid’
        - qsl=’qstat \| grep userid’
    - options
        - without option
            - shows all the jobs from all the users
            - get longer jobname&#9;&#9;&#9;&#9;
                - qstat \| grep UID&#9;&#9;&#9;&#9;cf. alias to qsl
        - -u username&#9;&#9;&#9;&#9;&#9;
            - show user
            - alias qs=’qstat -u x2818a02’
                - shows short form &#9;cf. -x for longer jobname
            - e.g.
                - qstat -u joonho
                - qstat -u “\*” \| grep node11
            - menus&#9;&#9;&#9;&#9;&#9;&#9;&#9;
                - state
                    - qw: waiting
                    - r: run
                - queue (node)
                - slots (number of process)
        - -f: full status
            - qstat -f job\_id
        - -r
            - shows job running and suspended
            - details of queue jobs
            - number of processes, memory,
        - -n
            - see jog in detail
            - see job ID and all the running nodes
            - Before load a job check the empty node by
            - alias to qn
        - -a
        - -x
            - shows all the jobs with status of X, Q, R, F, etc
        - -H
- qsub
    - qsub \<job script\>
        - KISTI: qsub \<job attributes/resources\> \<job script\>&#9;&#9;cf. KISTI
        - command line variable
            - -N qname
            - -l
            - -v var1=varname&#9;&#9;&#9;&#9;cf. qsub variable
        - e.g.
            - qsub -l select=1:ncpus=1 -q normal hellow\_world.sh
    - variable -v&#9;&#9;&#9;&#9;&#9;cf. slurm variable
        - ` export environment variables to the job `
        - -v takes a CS list of name=value pairs
            - -v exe=gam
            - -v exe=’gam’
            - -v “exe=gam”&#9;&#9;&#9;# -v ‘exe=gam’ is wrong
        - multiple variables
            - -v exe=gam,input=data,output=res
- showq
- qdel job\_id
- qselect
    - remove all jobs of a user
        - qselect -u user \| xargs qdel

### PBS script

- Commands that are directives to PBS will always begin with #PBS
    - #PBS -N jobname
        - equal to “qsub -N jobname \<script\>”
        - returns $PBS\_JOBNAME
    - #PBS -e jobname.err
    - #PBS -o jobname.log
        - Set filenames for PBS to log standard error and standard output
    - #PBS -l nodes=2:dual:athlon
        - -l select-1:ncpus=32:mpiprocs=32:ompthreads=1
            - qsub -l select-1:ncpus=32:mpiprocs=32:ompthreads=1 \<script\>
        - rho
            - nodes=2:ppn=16:old&#9;or new
    - #PBS -l mem=512mb
    - #PBS -l walltime=02:00:00
        - Request 2 nodes, with the properties \`\`dual'' and \`\`athlon''. This job requests 512 MB of memory, and expects to run for 2 hours
- The remainder of a PBS script is essentially a shell script that runs the commands that make up your job. For example, the rest of a PBS script could be:
    - `` echo Running on host `hostname` ``
    - `` echo Time is `date` ``
    - `` echo Directory is `pwd` ``
    - $HOME/computejob
- variable
- Shell env variables
    - working
        - $HOME

### PBS environmental variable

- properties
    - PBS sets multiple environment variables at submission time
- envs
    - $PBS\_JOBNAME
        - qsub -N $PBS\_JOBNAME
    - PBS\_O\_WORKDIR
        - PBS sets the environment variable PBS\_O\_WORKDIR to the directory where the batch job was submitted.
        - By default, a job starts in your home directory.
        - Include the following command in your script if you want it to start in the submission directory:
            - ` cd $PBS_O_WORKDIR `
    - PBS\_JOBID
        - PBS sets the environment variable PBS\_JOBID to the job’s ID.
        - A common use for PBS\_JOBID is to append the job’s ID to the standard output and error file(s), such as the following
        - #PBS -o scriptname.o$PBS\_JOBID
    - PBS\_NODEFILE
        - the name of the file that contains the list of the nodes assigned to the job . Useful for Parallel jobs if you want to refer the node, count the node etc
        - to obtain number of nodes
            - set NPROC = \`cat $PBS\_NODEFILE \| wc –l\`
            - used in
                - ` mpirun –np $NPROC –hostfile $PBS_NODEFILE exe < input > output `
    - $TMPDIR&#9;&#9;: tmp dir for job
    - PBS\_NNODES (not in KISTI)
        - PBS sets the environment variable PBS\_NNODES to the number of nodes requested
    - Etc
        - $PBS\_O\_PATH&#9;: path for submission
        - $PBS\_O\_HOST&#9;&#9;# idft
        - $PBS\_O\_LOGNAME&#9;# joonho
        - $PBS\_O\_HOME&#9;&#9;# /home/joonho
        - $PBS\_O\_WORKDIR&#9;: absolute path to $qsub command
- #PBS -W sandbox=PRIVATE&#9;: can check STDOUT, STDERR on job running
    - ./a.out 1\>stdout 2\>stderr&#9;: also can check STDOUT, STDERR on job running

### Writing on outfile

- Echo: write sentence or variable
- Cat: special variable like $PBS\_NODEFILE

### Qsub in empty node

- Fault in loading in a certain node
    - #PBS –l nodes=idft11:ppn=8

### Sleep: Null running to run serial Q-Chem

- Sleep
    - Sleep makes node occupied without running any process
    - Useful for serial runing of Q-Chem
- Example
    - #PBS –l nodes=kdft13:ppn=12
        - By defining node
    - #PBS –l nodes=1:ppn=12
        - Not defining node id
- server
    - sleep in mu

### MPI error

- orte\_session\_dir failed
    - writing permission error
        - you should be able to log in each node. cf. key publish
    - environment variable
        - compare joonho@rho and emergency@rho
    - attacks.

### PBS script

- Definition
    - #PBS –q
    - #PBS –l walltime=300:00:00&#9;#
        - 14400 for second, it is 4 hour
        - 10:00 is 10 min
        - 10:00:00 is 10 hour
    - #PBS –l nodes=1:ppn=8&#9;&#9;# number of nodes & processes per node
        - nodes=node3:ppn=8&#9;&#9;# specify the job node
        - nodes=node1:ppn=8;node2:ppn=8&#9;# choose several nodes
        - #PBS –l nodes=1:ppn=4&#9;&#9;# number of nodes and number of process
        - #PBS –l nodes=node10:ppn=8&#9;# define specific node
    - #PBS –N jobname
    - #PBS –M mail@address
- ENV variables
    - $PBS\_O\_WORKDIR&#9;# job directory
    - $PBS\_JOBNAME&#9;&#9;# defined by #PBS –N
    - $PBS\_JOBID
    - $PBS\_NODEFILE
- Logic
    - ` cd $PBS_O_WORKDIR `
        - after change directory, you can make file in your directory

### pbs\_error

- structure in /usr/local/pbs/sbin
    - pbs\_sched, pbs\_server is deamon in master node
    - pbs\_mom is running in node
- try this
    - check the working node which you try to use
    - in node, kill pbs\_mom and rerun /usr/local/pbs/sbin/pbs\_mom

### server speed check

- speed test for servers
    - Node and speed
        - Pt-X3
            - AIMD: Pt-C54

<table>
<tr>
<td>System: Job: time</td>
<td>partition</td>
<td>Nnode (nproc)</td>
<td>duration</td>
<td>double Node</td>
</tr>
<tr>
<td>Pt-C54 mol: AIMD: 1ps<br>                 <br>5ps</td>
<td>X3</td>
<td>5 (100)</td>
<td>4h 42m</td>
<td>Save 1 Hr, <br>20% speed up</td>
</tr>
<tr>
<td></td>
<td></td>
<td>10 (200)</td>
<td>3h 43m</td>
<td></td>
</tr>
<tr>
<td></td>
<td>X3</td>
<td>10 (200)</td>
<td>19h 50m</td>
<td></td>
</tr>
<tr>
<td></td>
<td>Kisti</td>
<td>20 (400)</td>
<td>12h 50m<br>2h 40m/pc</td>
<td></td>
</tr>
<tr>
<td>HfSe2 1 ML</td>
<td>X2 </td>
<td>1</td>
<td>11h 30m</td>
<td></td>
</tr>
<tr>
<td></td>
<td>X4</td>
<td>1</td>
<td>3h 10m</td>
<td></td>
</tr>
</table>

- hour / number of (RMM and DAV)

<table>
<tr>
<td></td>
<td>X1</td>
<td>X2</td>
<td>X3</td>
<td>X4</td>
<td>X5</td>
<td>KISTI</td>
<td>Cal</td>
</tr>
<tr>
<td>X1: 10 - 80<br>X2:  3 - 36</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>bd</td>
</tr>
<tr>
<td>Nanocore</td>
<td>1:21h<br>2:8h25</td>
<td></td>
<td></td>
<td>1:2h</td>
<td>1:2h17m<br>2:3h10m</td>
<td></td>
<td>Nnode/hr</td>
</tr>
<tr>
<td>X3: Nnode 1<br>           2</td>
<td></td>
<td></td>
<td>0.12<br>0.076</td>
<td></td>
<td></td>
<td></td>
<td>Opt</td>
</tr>
<tr>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>NanoCore<br>HER<br>ORR</td>
<td></td>
<td></td>
<td>4: 4m:13<br>8: 3m:22</td>
<td></td>
<td></td>
<td></td>
<td>(2,2,2) <br></td>
</tr>
<tr>
<td></td>
<td></td>
<td>4: 27h</td>
<td>4: 2h<br>4: 10h<br>8: 18h</td>
<td>2: </td>
<td></td>
<td></td>
<td>[2,2,1]<br>[4,4,1]<br>Pt111-4,4,1</td>
</tr>
<tr>
<td>VASP<br>       </td>
<td></td>
<td></td>
<td><br>53 min </td>
<td>47m (8np)<br>6, 21 min</td>
<td></td>
<td></td>
<td>Zpe<br>3 times </td>
</tr>
<tr>
<td>Band struct<br>SnO2 large</td>
<td>Mem error</td>
<td></td>
<td><br><br></td>
<td>10:60:60<br>10:20:10</td>
<td></td>
<td>12h(48st)<br>2h45m<br></td>
<td>KNL (600)<br>SKL (10)</td>
</tr>
<tr>
<td>    Sc22</td>
<td></td>
<td></td>
<td>N8, np160<br>33m</td>
<td></td>
<td><br><br>N6: 37m</td>
<td>Skl N20<br>21m<br>N20: 26m</td>
<td></td>
</tr>
<tr>
<td>Sc23 band</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td>N3: 1h10m</td>
<td>N20: 1h</td>
<td></td>
</tr>
<tr>
<td>SnO2HClsu34</td>
<td>Accurate<br>normal</td>
<td>10 node<br>20 node</td>
<td>55 DAV<br>9 DAV</td>
<td>28:30<br>3:05</td>
<td></td>
<td>0.52h<br>0.35h</td>
<td>BD<br>precision</td>
</tr>
<tr>
<td>SnO2HClsu34<br>band</td>
<td></td>
<td></td>
<td>N20/half: 4h36m</td>
<td></td>
<td>N8/half: 4h25m</td>
<td>N20/half:3h40m</td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td>H2-Pt-C60-x</td>
<td></td>
<td></td>
<td>2: 28m<br>4: 34:30s<br>8: 17:30s</td>
<td></td>
<td></td>
<td></td>
<td>zpe</td>
</tr>
</table>

- calculation speed, vasp MXene
    - X3 \* 5 = 100 proc
        - 430 step: 5d 17h
    - X1 \* 15 = 200 proc
- X3 vs X1
    - X1 N10 \> X3 N1: X1N10 is much faster about 1.5 times
        - DOS (npar=1) also faster twice
- KISTI speed and memory check
    - memory problem&#9;&#9;&#9;&#9;&#9;cf. kisti memory
    - SKL

| Job | Nnode | Mpiproc<br>(NCORE) | Nproc | Duration |  |
| --- | --- | --- | --- | --- | --- |
| Sc34band | 20 | 20 | 400 | 3h 26m | Mem OK |
|  | 40 | 10 | 400 | 3h 31m | No diff<br>To space Mem |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |

### PBS in KISTI

- nurion&#9;&#9;&#9;&#9;&#9;cf. PBS in system management
    - queue submit directory
        - /scratch/id
            - backup in 15 days
- for basic instruction: go to pbs
    - how to give options
        - qsub script.sh
            - in the script
        - qsub -option
            - on the command line (standard input)
            - e.g.
                - qsub -N pe300 $SB/pypbs/pbs\_vasp.sh
    - options
        - general
            - this part in script is overridden by CLI
            - but -v in the script has higher priority
        - -V
            - #PBS -V: import all the env variables from mother shell
        - -A
            - #PBS -A qchem: application such as qchem
        - -q: Queue
            - KNL(68 core)
                - normal long(5일)
            - SKL(40 core) norm\_skl
            - cli: -q long
        - -l (el)
            - parallel support
            - #PBS -l select=1:ncpus=32:mpiprocs=32:ompthreads=1
            - qsub -l select=1:ncpus=32:mpiprocs=32:ompthreads=1 mpi\_qchem.sh
                - n nodes: n process/cpu:= n process/node : 1
            - qsub -l select=1:ncpus=48:mpiprocs=48+2:ncpus=8:mpiprocs=8 -l walltime=1:00:00 myscript.sh
            - different following HF/DFT/RI-MP2
            - #PBS -l walltime=48:00:00
    - CLI variables
        - -v
            - variable input
            - qsub -v fname=CO2 mpi\_qchem.sh
            - if fname is defined in the script, it will be used
        - several variable
            - -v a=’b’ -v c=’poscar.pt’
            - -v a=’b’,c=’poscar.pt’&#9;&#9;# comma separated
        - -v np is not working
            - for qchem -pbs -np $np
    - CLI
        - qsub -N jobname -q long -l walltime=90:00:00 -l select=20:ncpus=40:mpiprocs=20:ompthreads=1, -v a=’b’,c=’poscar.pt’ $SB/pypbs/pbs\_vasp\_kisti\_skl.sh
- job monitoring
    - showq&#9;&#9;&#9;# show queue
    - pbs\_status
    - pbs\_queue\_check
    - pbsnodes -ajS
        - mem f/t&#9;&#9;# free/total
        - ncpus f/t&#9;&#9;# number of cpu’s
    - qstat
        - -u $USER
        - -a
        - -n
        - -s
        - -H
        - -x
        - -f \<job ID\>
            - -fw \<job ID\>
        - -i -w -T -u UID&#9;# estimate delaying time
            - -i, -H: list in Q state
            - -w: detail
    - suspend/resume
        - qsig -s \<suspend\|resume\> \<job ID\>
    - qdel job\_id
        - job\_id: qstat -u $USER/ the 1<sup>st</sup> column
        - e.g. : qdel 11111.pbs
    - samples
        - /apps/commercial/QCHEM/v5.2/samples

## Slurm

### Simple Linux Utility for Resource Management

- function
    - job scheduler for server
        - platinum
        - KISTI: Neuron
    - resource allocation: cpu, gpu, memory
    - manage queue
    - node status
    - parallel job execution
- communication
    - slurmctld \<-\> slurmd
    - sbatch request
    - srun request
    - sub credential
    - all the communication go through authentication with sign
- structure
    - user  sbatch  slurmtld  slrumd
        - every step requires munge
            - without munge slurm is not working

### Architecture

- Allocated clusters
    - Kingspeak, ember
- Partitions
- Accounts
- E.g.
    - --account=baggins –partition=ember

### sbatch

- e.g.
    - ` #!/bin/bash `
    - #SBATCH -J &#9;&#9;&#9;#jobname
    - #SBATCH -o stdout.txt&#9;# output and error
    - #SBATCH -p X1&#9;&#9;# partition name
    - #SBATCH -N 20&#9;&#9;# number of nodes
    - #SBATCH -n 160&#9;&#9;# number of process
- command line input
    - sbatch \[option\] scriptfile
        - sbatch script file locates at the last
    - options
        - -n, --ntasks : number of process
            - default: 1 per node
        - -c, --cpus-per-task
            - ncpus number of procs per task
            - default: one proc per task
            - e.g.
                - sbatch -J dname -p X3 -N 16 -c 10 $SB/pypbs/slurm\_sbatch.sh
        - --ntasks-per-node
            - looks similar to -c
            - does not require knowledge of the actual number of cpus on each node
            - try
                - batch -J dname -p X3 -N 16 --ntasks-per-node 10 $SB/pypbs/slurm\_sbatch.sh
        - -N : number of nodes
        - -o stdout filename
        - -e stderr filename
        - -t maximum job time, format=02:00:00
        - --gres=gpu to use gpu
        - --nodelist n068&#9;&#9;&#9;&#9;&#9;! this is working
            - --nodelist=n\[nodename1,nodename2\]&#9;&#9;! wrong
            - n\[nodename1-nodename2\]
            - with partition
            - to submit to the specific node
        - -p partition
        - -J job name
    - sbatch script\_name
        - submitted
    - memory
        - --mem=\<size\[units\]\>
            - Real memory required per node
            - Default M
            - Units
                - \[K\|M\|G\|T\]
        - --mem-per-cpu
        - --mem-per-gpu
- variables
    - input variables
    - output variables
        - SLURM\_JOB\_ID
        - SLURM\_JOB\_NAME&#9;&#9;&#9;-J
        - SLURM\_JOB\_NODELIST
        - SLURM\_JOB\_NUM\_NODES&#9;&#9;-N
        - SLURM\_JOB\_PARTITION&#9;&#9;-p
        - SLURM\_NTASKS&#9;&#9;&#9;-n total num of process
        - SLURM\_SUBMIT\_DIR
        - SLURM\_CPUS\_PER\_NODE&#9;&#9;number of cpus on Node
        - SLURM\_NTASKS\_PER\_NODE
            - --ntasks-per-node
    - variables --export (same as -v in qsub)&#9;cf. qsub variables
        - --export=exe=gam
        - --export=exe=’gam’
        - variable A and b
            - use only A, b and SLURM\_\* envs
                - --export=A=5,b=’test’
            - add A, b to the existing var
                - --export=ALL,A=4,b=’test’
        - jobname, output file can be passed on the command line
            - ` A=5 `
            - b=’test’
            - sbatch --job-name=$A.$b.run --output=$A.$b.out --export=A=$A,b=$b batchfile

### Command

- commands
    - qsub commands
        - qsub, qstat, pestat
    - sbatch (qsub), sacctmgr, salloc, scancel, scontrol, sinfo, squeue, sbatch, srun, strigger, sview,
- jub submission
    - sbatch ( = qsub)
    - srun
    - scancel jobid
    - squeue ( = qstat)
        - qstat -u $USER
    - e.g.
        - sbatch job.sh
        - squeue -u $USER
- manage node/cluster (manager level)
    - sinfo
        - status of different partitions
            - partition avail timelimit nodes state nodelist
            - state
                - maint: maintenance
                - alloc: allocated
                - drain: not being used
                - idle:
        - alias
            - alias si=”sinfo –o \\”%20P %5D %14F %8z %10m %10d %11l %16f %N\\””
            - alias si2=”sinfo –o \\”%20P %5D %6t %8z %10m %10d %11l %16f %N\\””
    - scontrol show job JOBID
    - sacct
    - sprio
    - strigger
    - sview
    - salloc
    - e.g.
        - scontrol update nodename=n069 state=resume
- internal contents (daemon)
    - slrumctld
    - slurmd
    - slurmdbd
    - munge
        - MUNGE Uid & Gid Emporium
        - HPC cluster authentication service

### pestat

- show all nodes
- format
    - Node queue state load pmem ncpu mem resi usrs tasks NetMbit jobids/users

### squeue

- whatitis
    - shows all the running job
- format
    - jobid partition name user   st   time nodes nodelist
    - status
    - details
        - st: status
            - R
            - PD: pending
- squeue \[option\] -N -l
    - options
        - -l long
        - –u id
            - user id
        - --account=owner-guest
        - --partition=kingspeak-guest
    - menu
        - st: status
            - R: running
            - pd: pending
            - s: suspended
            - st: stop
            - cd: completed
            - ca: cancelled
            - f: failed
            - nf: node\_fail
    - alias sq=”squeue –o \\”%8i %12j $4t %10u %20q %20a %10g %20Q %5D %11l %lL %R\\””

### sacctmgr

- whatitits
    - to view or modify Slurm account information&#9; go to command
        - maintained within database provided by slurmdbd
    - slurm account information is recorded based on four params
        - four params: user, cluster, partition, account
            - user: login name
            - cluster: name of Slurm managed cluster specified by CusterName param in slurm.conf
            - account: bank account for a job
- usage
    - sacctmgr \[-options\] command
- commands
    - format
        - command \<ENTITY\> \<SPECS\>
    - add&#9;
        - identical to create
        - precommand by jLee to add user to slurm user
            - ` cd /var/yp `
            - make
        - add user
            - sacctmgr add user hubsjy account=users
    - show
        - check slurm users
        - sacctmgr show user  shows registered users
    - create
    - delete
        - sacctmgr delete user where name=yeo
    - list \<ENTITY\> \[\<SPECS\>\]
        - sacctmgr list user
    - load
- ENTITY
    - account
        - root\|users
    - association
    - cluster
    - configuration
    - user
- SPECS
    - general SPECS
    - SPECS for accounts
        - Cluster
        - Name

### Workload manager

- sacctmgr
    - view and modify slurm account information
- ` make a user a slurm user `
    - commands
        - su -
        - ` cd /var/yp `
        - make
        - ### after making ID, add slurm user
        - sacctmgr add user userid account=users

## Servers in EE

### System

- System connection
    - System and hard
        - Pt – home1
            - 143.248.247.113
        - Au – home2
            - 143.248.247.114
        - C – home3
            - 143.248.247.180
        - Backup1 to home1
        - backup2,
        - backup3 to home2
    - mount each other
        - Pt:/root
        - Au:/root
        - C:/etc/fstab
- shutdown in case blackout
    - Backup hard: Login and shutdown
        - Backup1, backup2, backup3
        - shutdown –h now
    - disconnect mutual mounting and shutdown in the order of C, Au, Pt
        - dismount in each /etc/fstab
        - reboot&#9;&#9;&#9;&#9;# to shutdown later
            - ` ssh carbon/ systemctl reboot `
            - df: check /home1, /home2 is not mounted in C
            - ping carbon.kaist.ac.kr &#9;# to confirm the connection
            - ` ssh gold/ systemctl reboot `
            - df: check /home1, /home3 is not mounted in Au
            - ping gold.kaist.ac.kr
            - systemctl reboot&#9;&#9;# in Pt
            - df: check /home2, /home2 are note mounted
        - shutdown
            - ` ssh carbon/shutdown –h now `
            - ` ssh gold/shutdown –h now `
            - shutdown –h now
- System power on
    - In the reverse order
        - Pt, Au, C, backup1,2,3
    - Turn on Pt, Au, C, backup1,2,3
    - Reboot with mount

### platinum

- hard – home1
- hpc node
    - partition 1 ~ 6
- apps
    - /TGM/Apps
    - VASP
        - /TGM/Apps/VASP
        - old version
            - /TGM/Apps/VASP/OLD\_BIN/5.4.4/O2/NORMAL
        - new version
            - /TGM/Apps/VASP/bin/5.4.4.pl2/
            - /TGM/Apps/VASP/bin/6.3.1/
- mount after boot at pt & au
    - pt:: /root/AFTER\_BOOT.sh
        - #home1-ib0:/home      /home    nfs   rw,defaults,vers=4.2,hard,noatime,nofail,lookupcache=positive 0 0
        - #mount -t nfs -o rw,defaults,vers=4.2,hard,noatime,nofail home2-ib0:/home2 /home2
        - mount -t nfs home2-ib0:/home2 /home2
        - mount -t nfs home3-ib0:/home3 /home3
    - au: /root/AFTER\_BOOT.sh
        - mount -t nfs home1-ib0:/home /home
        - mount -t nfs home1-ib0:/home1 /home1
        - mount -t nfs home3-ib0:/home3 /home3
        - #mount -t nfs master:/TGM /TGM
        - mount -t nfs 192.168.200.1:/TGM /TGM
- adduser for slurm
    - qsub activation after adduser
    - /root/ADDUSER.txt
        - adduser -gusers -d/home/ID ID
        - passwd ID
        - ` cd /var/yp `
        - make
        - ## After making ID, add slurm user
        - sacctmgr add user ID account=users
        - ##
        - For example.
        - adduser -d/home2/ID ID
        - passwd ID
        - ....
        - ` cd /var/yp `
        - make
        - sacctmgr add user ID account=users

### C

- ` ssh -Y carbon `
- nvidia-smi
    - GPU
        - 0&#9;Titan rtx
        - 1&#9;GeForce
- GPU machine
- check
    - nvidia-smi
- if not working
    - ` pip install torch==1.10.1+cu113 torchvision==0.11.2+cu113 torchaudio==0.10.1+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html `
- .bashrc
    - ` module add CUDA/11.3.0 `
- python-torch
    - the index is applied to oppositely
        - device = torch.device(“cuda:0”)&#9; runs at 1 GeForce
            - torch.device(“cuda:1”)&#9;&#9; runs at 0 Titan
        - model.to(device)

### infiniband

- (2022) mpi can be run by
    - ` mpirun -np $SLURM_NTASKS $EXE `
    - ` EXE= cf. vasp in pt `
- (deprecated) mpi fabrics
    - I\_MPI\_FABRICS
        - improper setting cause problem in VASP
            - WARNING in EDDIAG: sub space matrix is not Hermitian
    - syntax
        - ` I_MPI_FABRICS=<fabric>|<intra-node fabric>:<inter-nodes fabric> `
        - \<fabric\> : shm, dapl, tcp, tmi, ofa, ofi
        - \<intra-node fabric\>: shm, dapl, tcp, tmi, ofa, ofi
        - \<inter-node fabric\>: dapl, tcp, tmi, ofa, ofi
    - default
        - env \| grep -i fabric
            - ` I_MPI_FABRICS=shm:tmi `
    - e.g.
        - ` mpirun -genv I_MPI_FABRICS “shm:ofa” -np $SLURM_NTASKS ….vasp.x > $outfile `
    - different infiniband to other paritions
        - X2 ~ X5
            - use default
            - ` I_MPI_FABRICS=shm:tmi `
        - X1
            - ` I_MPI_FABRICS=shm:ofa `
            - in sbatch script
                - ` mpirun -genv I_MPI_FABRICS “shm:ofa” -np $SLURM_NTASKS …./vasp.v > a.out `

## KISTI

### integrated site & blog

- integrated site
    - login https://[www.ksc.re.kr/kor/index/main](<http://www.ksc.re.kr/kor/index/main>)
        - be careful: when logout it goes to [www.ksc.re.kr/mobile/](<http://www.ksc.re.kr/mobile/>)
            - not support help
    - connect id to supercom id
    - Nurion: [https://docs-ksc.gitbook.io/nurion-user-guide](<https://docs-ksc.gitbook.io/nurion-user-guide>)
    - Neuron: [https://docs-ksc.gitbook.io/neuron-user-guide](<https://docs-ksc.gitbook.io/neuron-user-guide>)
- software guide
    - blog.ksc.re.kr
    - search lammps, qchem, vasp

### application

- advertisement
    - 3 times/year
    - kinds
        - grand(거대연구)
        - creative(창의 - 이걸로 선택)
        - new(혁신)
- requirement
    - application
        - 신청서
            - 연구주제가 다를 경우 연 2개
    - result
        - result report
            - in a month in principle
        - register achievement (성과등록)
            - 이 논문은 국가초고성능컴퓨팅센터로부터 초고성능컴퓨팅 자원과 기술지원을 받아 수행된 연구성과임 (과제번호)
            - This work was supported by the National Supercomputing Center with supercomputing resources including technical support (과제번호)
- application
    - 구좌 (account) - 창의 (creative)

| Application limit | KNL | Neuron |
| --- | --- | --- |
| Node Hr | 320,000 | 18520 |
| N account | 50 | 10 |

- Total scheme

| Scale | KNL | Neuron |
| --- | --- | --- |
| NHr/account (hr) | 6400 | 852 |
| Total account | 1746 | 140 |

- node hour

<table>
<tr>
<td>만 node hour</td>
<td></td>
<td>Grand</td>
<td>Creative</td>
<td>Innovative</td>
</tr>
<tr>
<td>total</td>
<td>KNL</td>
<td>540</td>
<td>660</td>
<td>330</td>
</tr>
<tr>
<td></td>
<td>Skylake</td>
<td></td>
<td>20?</td>
<td>10?</td>
</tr>
<tr>
<td>per subject</td>
<td>KNL</td>
<td></td>
<td>32</td>
<td>32</td>
</tr>
<tr>
<td></td>
<td>Skylake</td>
<td></td>
<td>16</td>
<td>16</td>
</tr>
<tr>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</table>

- Core

|  | KNL | SKL |
| --- | --- | --- |
| total nodes | 8305 | 132 |
| n cpu/node | 1 | 2 |
| n core/cpu | 68 | 20 |
| n core/node | 68 | 40 |
| mem/core | 1.4 | 2.4 |
| mem/node | 96G | 192G |
| total mem | 797.3T | 25.3T |
|  |  |  |

### procedure for account

- if application is accepted
    - is emailed to me with account.pdf
    - [로그인 정보 삭제]
    - [로그인 정보 삭제]
        - [로그인 정보 삭제]
        - a02: 2<sup>nd</sup> user
- ` make OTP activation code `
    - app download
        - [http://goo.gl/Ed56Fl](<http://goo.gl/Ed56Fl>)
        - 앱 입력
            - [로그인 정보 삭제]
            - app install url
                - go to url
                - install through android  install new app (anyauth)
            - id
            - authentification code
- Generate OTP w. new ID
    - web login in computer
        - [https://otp.ksc.re.kr](<https://otp.ksc.re.kr>) &#9;# use main web browser, not VM
        - select OTP issue/re-issue
        - [로그인 정보 삭제]
        - [로그인 정보 삭제]
        - authentification and register
            - ID and authentification code: input to app
            - in app: ‘+’ add one more anyauth
                - input id and code
                    - app makes new anyauth
- login with account info (emailed to me)
    - Nurion
        - [로그인 정보 삭제]
            - [로그인 정보 삭제]
        - change passwd
    - Neuron
        - neuron01.ksc.re.kr
        - neuron02.ksc.re.kr
        - neuron.ksc.re.kr for random access
- help
    - ksc helpdesk
    - 080-04101991/042-869-0518
    - account@ksc.re.kr
- resource
    - nurion
        - allocated SRU Time: 14,760,000 s
        - fs&#9;&#9;kbytes&#9;quota&#9;files&#9;quota
        - /home01&#9;80k&#9;64G&#9;24&#9;200000
        - /scratch&#9;&#9;4k&#9;100T&#9;1&#9;1000000
- passwd
    - change at website
        - [https://www.ksc.re.kr/kor/index/main](<https://www.ksc.re.kr/kor/index/main>)
        - login/manage account/manage account
            - change supercom passwd
        - both web-site and supercom account
        - supercom
- data move for new account
    - ask to help
    - ` mv all the files (.* means all the hidden files) `
    - activate anaconda
        - change ID in .bashrc
            - to apply shell variable uid=x3346a02, single quote  double quote
        - change shebang in the following script
            - initialization file in .bashrc
                - "/home01/$uid/miniconda3/bin/conda"
                - /home01/$uid/miniconda3/etc/profile.d/conda.sh
            - ase command
                - ~/miniconda3/bin/ase

### Machines

- Nurion
    - cpu limit: 20 min
    - ` ssh disconnected `
        - ` make ssh awake and stay in login mode `
            - watch -d ‘ls -lrt’
- Nurion-dm
    - no cpu limit
        - ` ssh (sftp) nurion-dm.ksc.re.kr `
        - for data transfer
            - such as rsync, wget, git etc
    - sftp/ftp
        - sftp is not disconnected
        - connect to DM node
            - kisti sftp
                - sftp [x2232a02@nurion-dm.ksc.re.kr:/scratch/x2232a02/SnO2](<mailto:x2232a02@nurion-dm.ksc.re.kr:/scratch/x2232a02/SnO2>)
    - scp/rcp is working also
        - from eta
            - with absolute path
                - rcp x2232a02@nurion.ksc.re.kr:/scratch/x2232a02/SnO2/s002.tar .
        - from pt
            - scp x2232a02@nurion.ksc.re.kr:/scratch/x2232a02/SnO2/s002.tar .

### Module

- setup in .bashrc
    - for KNL
        - ` module load craype-mic-knl intel/18.0.3 impi/18.0.3 cmake/3.12.3 python/3.7 `
- usage
    - ` module command modulefile `
        - ` module --help `
    - ` module av `
        - cf. tachyon2\_startguide.pdf
        - print all the available module
        - amber, gromacs, lammps, python, g09, mvapich2, openmpi, fftw, intel
    - ` module help `
        - ` module help mpi/mvapich2-2.1 `
    - ` module load `
        - set env variable to use the module
        - cf.
            - ` module load compiler/inter-2015 mpi/mvapich2-2.1 `
    - ` module purge `
        - initialize all the env variables
    - apply the module to all the node at once
        - ` vi .bashrc `
            - ` module purge `
            - ` module load compiler/intel-2015 mpi/mvapich2-2.1 `
        - ` source ~/.bashrc `

### Nurion manual

- manual
    - [https://docs-ksc.gitbook.io/nurion-user-guide/undefined/running-jobs-through-scheduler-pbs#id-1](<https://docs-ksc.gitbook.io/nurion-user-guide/undefined/running-jobs-through-scheduler-pbs>)

### System: SKL vs KNL

- System Nurion
    - KNL
        - KNights Landing
    - SKL
        - Skylake

### Job scheduler strategy

- states of Nurion
    - nurion uses PBS
- backfilling
    - ref: [https://www.ksc.re.kr/cmnt/gjsh/sstgjsh/view?gjshkey=579](<https://www.ksc.re.kr/cmnt/gjsh/sstgjsh/view?gjshkey=579>)
    - filler job: it runs earlier than top job by backfill
        - to be filler job
            - walltime should be less than that of top job
            - walltime: default = 48 hour
                - if walltime is 48 hours, the waiting time can be prolonged
    - e.g.: top job인 A가 2시간 뒤에 작업 실행 예측일때, job B의 walltime이 2시간 이하면 A 보다 먼저 실행
- large job priority
    - For the same walltime
        - the larger select, ncpus have priority
- lapse time
    - table

| Waiting job | Lapse time |  |
| --- | --- | --- |
| 1 K | 16 h |  |
| 2.2 K | 14 h |  |
| 1.7 K | 11 h |  |
| 1.2 K | 12 h |  |
| 2 K | 11h | Correct test |
|  |  |  |

### Queue & PBS (Portable Batch System)

- site
- queue
    - queues
        - KNL
            - exclusive
            - normal
            - long - 120 H (5 days)
            - flat
            - debug
        - SKL
            - commercial
            - norm\_skl
    - Howtouse queue
        - #PBS -q long
        - #PBS -l walltime
        - CLI ‘-q long -l walltime=120:00:00’
    - queue(node)
        - KNL: knights landing
            - massive parallel job
            - -l select=4:ncpus=68:mpiprocs=68:ompthreads=1
                - n nodes: n cpu/node:
            - queuename
                - #PBS -l walltime=48:00:00&#9; normal
                - #PBS -l walltime=72:00:00&#9; long
        - SKL: skylake
            - fast as normal
            - -l select=10:ncpus=40:mpiprocs=40:ompthreads=1
                - in case memory problem
                    - -l select=10:ncpus=40:mpiprocs=20:ompthreads=1
    - memory problem
        - - 변경 전 : #PBS -l select=2:ncpus=64:mpiprocs=64:ompthreads=1
        - - 변경 후 : #PBS -l select=4:ncpus=32:mpiprocs=32:ompthreads=1
- env in KISTI&#9;&#9;&#9;&#9;&#9;&#9;cf PBS env
    - PBS\_JOBID
    - PBS\_JOBNAME
    - PBS\_NODEFILE
    - PBS\_O\_PATH
    - PBS\_O\_WORKDIR
    - TMPDIR

### commands

- isam
    - 1: show sru time per each user
    - view job history
        - select menu (enter)
        - select menu  2 System batch job use detail
        - select menu  1 Nurion
            - start date  20240101&#9;# format: YYYYMMDD
            - end date  20241231
- pbs\_status
    - show queue
- motd
    - shows queue policy
- PBS commands
    - pbs\_status
        - status of nodes
        - e.g.
            - Queue&#9;total alloc run\_jobs que\_jobs
            - normal  5272 5082  1165    1266  estimate when my job will run
        - Queue in Normal
            - # of queue: 1266
            - submit:   19:18:30  run
    - show\_topjob
        - qstat for top jobs to be run soon
        - can compare these jobs in normal to my job using Job ID
    - qstat
        - shows only UID jobs
    - qstat\_all
        - shows all jobs in queue
    - showb
    - qstat -f jobid\[.pbs\]
        - submitted job status

### Run (VASP, Siesta, Q-Chem)

- VASP
    - basic
        - load module
        - copy executable
            - from iron to kisti
                - ldd show whether the link is probable
                - ` module load makes complete the dynamical `
        - pbs\_vasp.sh
            - ` #!/bin/sh `
            - #PBS -V
            - #PBS -A vasp
            - ##PBS -N pe500
            - #PBS -q normal
            - #PBS -l select=20:ncpus=60:mpiprocs=60:ompthreads=1   # max=68
                - but it is better to take 60
            - #PBS -l walltime=48:00:00
            - ` EXEC="/home01/g129a89/bin/vasp_5.4.4_GRP7_NORMAL_20170903.x" `
            - ` mpirun $EXEC > $log_dir/$jobname.log `
                - N.B. no -np N
        - qsub
            - qsub -N dirname $SB/pypbs/pbs\_vasp.sh
                - the same with “pbs\_vasp\_kisti.sh”
    - details
        - mandatory option in the script
            - #PBS -A Application\_Name
                - gaussian, vasp gromacs charm qchem amber lammps namd qe tf pytorch etc
            - #PBS -P burst\_buffer
                - flush the important data to /scratch periodically
        - for single job
            - ` #!/bin/bash `
            - #$ -V&#9;&#9;# apply env of job submit node to computation nodes
            - #$ -cwd&#9;&#9;# cwd is working directory
            - #$ -N CO2&#9;&#9;&#9;&#9;# job name
            - #$ -q normal&#9;&#9;&#9;# queue name
            - #$ -R yes&#9;&#9;&#9;&#9;# resource reservation
            - #$ -o CO2.out&#9;&#9;&#9;# std output
            - #$ -e CO2.err&#9;&#9;&#9;# stderr
            - ##$ -wd /scratch/user\_id/CO2\_test&#9;# if pwd is not working directory
            - #$ -M email@address&#9;&#9;# set email address
            - #$ -m e&#9;&#9;&#9;&#9;# at job end, send email
            - #$ -l h\_rt=48:00:00&#9;&#9;&#9;# expected run time
        - openmp job
            - #$ -pe openmp 4&#9;&#9;&#9;# number of thread 1 ~ 8
            - #$ -v OMP\_NUM\_THREADS=4&#9;&#9;# it should be the same as openmp
            - ` export OMP_NUM_THREADS=4 `
            - /scratch/user\_id/omp.exe&#9;&#9;# env setting and commander
        - mpi (IntelMPI, oenMPI) job in “mpi.sh”
            - ` #!/bin/sh `
            - #PBS -N IntelMPI\_job
            - #PBS -V
            - #PBS -q normal&#9;&#9;# long
            - #PBS -A \<pbs option: Application name.
            - #PBS -l select=4:ncpus=64:mpiprocs=64:ompthreads=1
            - #PBS -l walltime=04:00:00
            - ` cd $PBS_O_WORKDIR `
            - ` mpirun ./a.out `
        - mpi old version (skip this part)
            - #$ -pe mpi\_fu 32&#9;&#9;&#9;# number of process
                - mpi\_1cpu: 1 cpu per node
                - mpi\_2cpu: 2 cpu per node
                - mpi\_4cpu
                - mpi\_8cpu
                - mpi\_fu: &#9; all cpu in node
            - ##$ -wd /scratch/user\_id/mvapich
            - mpirun\_rsh –machinefile $TMPDIR/machines –np $NSLOTS ./mpi.exe &#9;# mpi execution file
    - Interactive qsub
        - use -I
            - qsub -I -l select=1 1:ncpus=64:ompthreads=1 -l walltime=02:00:00 -q normal -A \{application\}
        - -V
            - inherit env variables
            - qsub -I -V ….
- Q-Chem
    - ENV
        - No ENV in .bashrc
        - set ENV in script
    - PBS
        - ` source $QC/bin/qchem.setup `
        - ` module purge `
            - in the case that load module in .bashrc, it might collide
        - ` module load compiler/intel-11.1 `
        - ` module load mpi/openmpi-1.4.2 `
        - ` setenv PBS_NODEFILE $TMPDIR/machines `
        - ` setenv QCSCRATCH /scratch/x777pjh/qchem `
            - ` make directory `
        - qchem -pbs -np 64 co2.in co2.out
    - Path
        - ` export PATH="/usr/local/bin:${PATH}:/sbin:/usr/sbin:/bin:/usr/bin:/usr/X11R6/bin:/applic/sge/bin/lx24-amd64" `
        - ` export PATH="$PATH:/applic/applications/qchem_tk/bin:/applic/applications/Qchem/bin" `
    - qchem
        - qsub -N NiFe5 -v fname=5-NiFe.in -v np=18 qchem\_skl.sh
- siesta

### port

- ssh, scp, sftp
    - go-outside is not working
- only connect from outside

### miniconda, p4vasp

- miniconda
    - install by sh
        - rather than bash
- fltk and p4vasp
    - composite version in here
    - fltk
        - ` module purge `
        - ` module load intel/18.0.3 impi/18.0.3 cmake/3.12.3 `
        - ` wget https://www.fltk.org/pub/fltk/1.3.7/fltk-1.3.7-source.tar.gz `
        - ` tar -xzvf fltk-1.3.7-source.tar.gz `
        - ` cd fltk-1.3.7 `
        - ` ./configure --prefix={fltk 설치경로} `
            - ` ./configure --prefix=$HOME/.local `
        - make
        - ` make install `
            - install at
                - $HOME/.local/
                    - include
                    - lib
                    - bin
                    - share
        - ` $ export PATH={fltk 설치경로}/bin:$PATH `
        - ` $ export CPATH={fltk 설치경로}/include:$CPATH `
        - ` $ export LD_LIBRARY_PATH={fltk 설치경로}/lib:$LD_LIBRARY_PATH `
    - p4vasp
        - ` $ wget https://github.com/orest-d/p4vasp/archive/refs/heads/master.zip -O p4vasp.zip `
        - ` $ unzip p4vasp.zip `
        - ` $ cd p4vasp-master `
        - ` $ sh install-local.sh `
            - installs at ~/p4vasp
                - bin/
                - …
        - commands
            - p4v, p4v.py
    - error
        - ImportError: /home01/x2232a02/p4vasp/python-packages/\_cp4vasp.so: undefined symbol: \_ZN12Fl\_Gl\_Window6resizeEiiii

## IBS (slurm)

### Connection through Cisco SSL VPN

- site
    - [https://rscvpn.ibs.re.kr](<https://rscvpn.ibs.re.kr/>)
- login
    - group: adsl
    - [로그인 정보 삭제]
    - [로그인 정보 삭제]
- Download and install
    - sudo bash anyconnect-linux64-4.10.05111-core-vpn-webdeploy-k9.sh
- execute Cisco SSL VPN
    - Application/Internet/Cisco Anyconnect Secure Mobility Client
    - connect to [rscvpn.ibs.re.kr](<http://rscvpn.ibs.re.kr/>)
        - group: adsl
        - [로그인 정보 삭제]
        - ciscon ssl vpn 계정으로 로그인
    - error in connection

### Olaf account and connection

- olaf connection
    - [로그인 정보 삭제]
        - [로그인 정보 삭제]
        - [로그인 정보 삭제]

### Schedular partition

- olaf는 slurm이라는 작업 스케줄러를 사용하며 여러 개의 파티션(다른 스케줄러에선 큐라고 부릅니다)이 존재합니다.
- 간단한 설명은 아래와 같습니다.
- 1) cryoem : gpu(V100) 8장씩 있는 노드가 5개 할당되어있는 큐로서 주로 gpu 작업용으로 사용됩니다.
- 2) jepyc : gpu(1080ti) 2장씩 있는 노드가 20개 할당되어있는 큐이며 amd cpu가 있는 것이 특징입니다.
- 3) jepyc-rtx : gpu(2050ti) 8장이 있는 노드 1대가 할당되어있는 큐입니다.
- 4) HQ2comp : cpu 전용 큐로써 28개의 노드(약 744개의 코어)가 있습니다.
- 5) HQcomp : cpu 전용 큐로써 28개의 노드(약 720개의 코어)가 있습니다.
- 6) HQmem : cpu 전용 큐로써 4개의 노드(약 720개의 코어)가 있으며 노드당 256GB의 메모리를 지니고 있습니다.
- 이 중 계산하려는 작업에 맞는 큐를 선택하여 job submit하면 됩니다.
- 간단한 slurm 사용가이드를 송부 드리오니 첨부파일 확인 부탁드립니다.
- 해당 자료는 무단 복사 및 배포를 할 수 없음을 알려드립니다.
- ※ 로그인 노드에서 작업을 돌리면 안됨을 안내드립니다. 스케줄러에 작업을 submit하여 실행하여주십시오.

### Software

- 일반적으로 필요로 하시는 소프트웨어는 사용자 홈 디렉토리 아래에 설치해주시면 되며,
- 시스템에선 module 형태로 소프트웨어를 제공합니다.
- 시스템에서 제공하는 소프트웨어를 확인하시려면 module av 명령어를 통하여 확인이 가능합니다.
- 사용자 홈 디렉토리에서 설치가 불가능한 소프트웨어의 경우 저에게 요청주시면 확인 후 설치해드릴 수 있도록 하겠습니다.

### Data storage

- 스토리지 공간 할당은 그룹단위로 이루어집니다.
- 할당된 공간을 같은 그룹의 유저들이 나누어 사용하는 형태입니다.
- 데이터 스토리지를 10TB를 요청하셨으므로 총 용량을 10TB로 설정하였습니다.
- 변경을 원하시는 경우 저에게 회신 부탁드립니다.
- 그리고 사용자의 홈디렉토리는 /mnt/lustre/ 하위에 있으나,
- 실제 10TB 용량이 할당된 공간은 /proj/internal\_group/adsl이므로 실제 사용하실 데이터는 이곳에 저장하면 됩니다.

## Parallel package

### Qchem

- ` setenv QCSCRATCH /disk2/scratch/joonho/QCSCR/ `
- ` setenv QCLOCALSCR /disk2/scratch/joonho/ `
    - even though you run with option “-save”, the scratch files on local directory, that is, $QCLOCALSCR are deleted but those in $QCSCRATCH are saved. So do not define $QCSCRATCH as the same directory of $QCLOCALSCR

### VASP

- structure

Figure 5 Q-Chem and VASP Compilation Structure

Figure 6 Q-Chem and VASP build structure

- need to check compiler, mpi version
- [install](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\vasp_qe.docx>)
- running
    - parallel-compiled exe
        - vasp
            - /opt/applic/vasp/bin/vasp-5.3.5-xe11-openmpi-1.6.3-full
        - Qchem
            - Qchem –np 12 a.in a.out
    - run with mpi
        - ` mpirun –np x –hostfile hostfile exe `
    - script from H. Kim and J. Kim
        - qsub\_qcin\_multiple.py S 12
        - qsub vsp\_all.pbs

### Quantum Espresso

### common check

- to see env var
    - env
- to see var
    - set

<br>

## GitHub & git

## GitHub

### What is it?

- a code hosting platform for version control and collaboration
    - it lets you and others work together on projects from anywhere
- cf git

### kinds

- github
- gitlab

### How to use in github

- Basics
    - What to learn?
        - create and use a repository
        - start and manage a new branch
        - ` make changes to a file and push them to GitHub as commits `
        - open and merge a pull request
    - github essentials
        - repositories
        - branches
        - commits
        - pull requests
    - protocol
        - ` git should use https `
            - switch the remote from ssh to https
- passwd vs token
    - whatitis
        - passwd: to log in github.com
        - token: to pull or push to github.com
    - account
        - [로그인 정보 삭제]
    - token
        - create
            - login github.com
            - go to
                - /Settings/Developer settings/Personal access tokens
                - Generate new token
                    - give descriptive name for the token
                    - select expiration date  long such as 3 month
                    - select repo or all check boxes
                    - Generate token
                    - save token separately in another document
        - how and when
            - ` git push `
                - [로그인 정보 삭제]
                - Password: stored
                    - copy and paste
            - to save username and passwd
                - [https://stackoverflow.com/questions/2233590/is-there-a-way-to-make-git-remember-the-password-for-webdav-remotes](<https://stackoverflow.com/questions/2233590/is-there-a-way-to-make-git-remember-the-password-for-webdav-remotes>)
                - using ~/.netrc

machine github.com

[로그인 정보 삭제]

[로그인 정보 삭제]

- set permission: (optional)
    - 600
        - (run in guest)
            - ` git config credential.helper store `
                - cf. for github not to ask passwd
                    - then push to the server once
                        - ` git push `
                    - the credential you use to push to the server will get saved in ~/.git-credential

### hello-world

- create a new repository
    - click ‘+’ next to my ID, then select New repository
        - fill out repository name, description initialize with README
        - check “Create repository”
- create a new branch
    - branch

Figure 7 Git branch and merge

- ` make a branch of feature from master `
    - then, do work there and merge to master
    - ` make new branch `
        - click branch
        - dropdown: input branch name
        - enter\|Create box
    - now on a new branch with a copy of master
- ` make and commit `
    - click README.md file and write icon
        - modify file
        - fill out commit change
            - title
            - optional extended contents
        - click “commit changes”
        - now the new branch is different from master
- open pull request
    - Now we have changes in a branch off of master, we can open a pull request
        - by opening pull request,
            - initiate discussion about the commit
            - someone review the difference and pull in the request and merge them into their branch
    - click Pull requests on menu bar then
        - click New pull request
    - in the Example Comparisons box, select the branch to compare with master
        - look over changes
        - if you accepts the changes
            - click big Create pull request
                - add comment
                - click Create pull request (or draft pull request)
- merge pull request
    - click Merge pull request
    - click confirm merge
    - click Delete branch since its changes have been incorporated

### setting

- go to each repository
    - settings
- Settings
    - Options
        - Danger Zone
            - locates at bottom
            - Delete repository
    - Branch
        - Rename branch  click pencil

### advanced

- create a repository
    - repository
        - used to organize a single project
        - can contain folders, files, images, videos, spreadsheets, and data sets – anything project needs
        - recommend to include
            - README
        - license file
- create a branch
    - master is a main branch
    - use branches to experiment and make edits before committing them to master
    - create a branch at \[Branch:master\]
        - branch copies master
- checkout different branch
    - check all the branches
        - ` git tag -l `
    - move to another branch
        - if you have already other branch locally and are not on this branch
            - ` git checkout stable_3Mar2020 `
            - N.B. the dates of files are not changed. Check out the contents of a file
        - if it does not exist locally
            - “git checkout stable\_3Mar2020” is same as
            - ` git checkout -b othername origin/stable_3Mar2020 `
                - othername for your own job
        - ` git checkout -b stable_3Mar2020 `
            - checkout the branch and move to the branch
    - checkout another branch
        - the above checkout will work
        - or
            - ` git fetch origin branch `
            - ` git pull origin stable_3Mar2020 `
- delete branch
    - delete local branch
        - ` git branch -d branchname `
    - delete remote branch
        - ` git push origin –delete branchname `
- commits
    - download & update from github
        - download
            - ` git clone address `
                - address appears in “clone or download”
            - Download zip
        - update
            - ` git pull `
    - some saved changes on GitHub

### GitHub and local git

- adding an existing project to GitHub
    - GitHub
        - create a new repository
    - local
        - ` cd /local_project `
        - ` git init `
        - ` git add . `
        - ` git commit -m “first commit” `
        - copy the remote repo by click icon in GitHub
    - add remote URL
        - ` git remote -v `
        - ` git remote add origin URL `
            - add id in URL
                - ` git remote add origin https://hopefulp@github.com/hopefulp/water.git `
            - or modify by set-url
        - ` git remote -v `
        - ` git push -u origin master `
- ` git pull again `
    - recover the original status
        - after git pull
        - modified some files
        - want to recover the original files with the modified version untouched
    - fetch and reset
        - ` git fetch origin master `
        - ` git reset --hard FETCH_HEAD `

### error

- whenever push, it requires passwd
    - input personal key rather than passwd
        - passwd is obsolete but used in login website
    - how to permanently save key in server
        - [https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git](<https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git>)
        - github cli in conda
            - ` conda install gh --channel conda-forge `
                - upgrade
                    - ` conda update gh --channel conda-forge `
            - gh auth login
                - selection
                    - GitHub.com
                    - HTTPS
                    - Yes
                    - Paste authentication tocken
                    - Done
            - gh config set -h github.com git\_protocol https
            - authentication credentials saved in plain text

## Git

### Basic Explanation

- [https://blog.naver.com/PostView.naver?blogId=parkjy76&logNo=220308491051&parentCategoryNo=&categoryNo=73&viewDate=&isShowPopularPosts=false&from=postView](<https://blog.naver.com/PostView.naver?blogId=parkjy76&logNo=220308491051&parentCategoryNo=&categoryNo=73&viewDate=&isShowPopularPosts=false&from=postView>) in the book (pdf) From bottom to up by [John Wiegley](<http://newartisans.com/2008/04/git-from-the-bottom-up/>)
- Repository
    - start from root directory/ directory and files
        - file
            - leaf node
            - meta data stored in directory and i-node
        - blob: leaf node of tree
- some basic idea
    - ` make a file		# before git initialize `
        - ` echo ‘hello’ > fname `
        - ` git hash-object fname	-> shows hash id `
    - after git init
        - ` git cat_file -t hashid `
            - blob
        - ` git cat-file blob hashid `
            - hello
    - blob is stored in trees
        - ` git ls-tree HEAD `
        - ` git rev-parse HEAD `
        - ` git cat-file -t HEAD `
        - ` git cat_file commit HEAD `
- commit
    - commit and tree
    - commit with other name
        - branch: alias to the last commit
            - when checkout a last commit, HEAD directs to the commit
        - tagname: tag to a commit is constant
        - HEAD: present checked out commit
            - if check a special commit, it doesnot direct a branch and becomes a detached HEAD
        - c8ed… 40 character of SHA1 hash id
            - 6-7 letters are enough to identify
        - name
            - name^: parent commit
            - name^n
            - name~n
            - name1..name: return (name1, name2)
            - name1…name2: different commit&#9;# .. and … are different
- branching and rebase
    - rebase vs merge
        - rebase: in case another branch may use the commit as base
        - merge: except above, use merge
    - e.g.
        - ` git branch: D, Z `
        - ` git show-branch: `
    - merge: from z merge D
        - ` git checkout z `
        - ` git merge D `
    - rebase
        - ` git checkout z `
        - ` git rebase D `
- index
- reset
    - mixed reset: default
        - ` git add foo.c `
        - ` git reset HEAD	# remove index `
    - soft reset
        - properties
            - move HEAD to other commit
            - not change working tree
        - ` git reset --soft HEAD^	# move HEAD to parent and ignore last commit `
        - ` git update-ref HEAD HEAD^ `
    - hard reset (danger)
        - properties
            - HEAD to the present HEAD  remove all the changes in the present working tree
                - files are at HEAD
            - for safety
                - do git stash
            - similar to git checkout
                - if index is empty, the same as reset --hard
                - if not, working tree is in index
        - ` git reset --hard HEAD~3	# move to back in 3 commits and discard changes `
            - the same as
            - ` git reset --soft HEAD~3 `
            - ` git reset --hard 	# == git reset --hard HEAD `
        - compare with stash (more safe way)
            - ` git stash `
                - when not sure the branch is to be changed
                - to recover previous one
                    - ` git stash			# good habit `
                    - ` git reset --hard HEAD~3	# go back with removal of 3 commits `
                    - ` git reset --hard HEAD@{1} # it was mistake `
                    - ` git stash apply		# `
            - ` git checkout -b newbr HEAD~3 `
                - to make newbr to master
                - ` git branch -D master			# goodbye old master `
                - ` git branch -m newbr master		# newbr is my new master `
    - reset is a radical change  do dangerous things in branch

### conflict

- conflict in git push
    - conflict occurs when there is another commit at the same branch of remote repo
        - modified in the same file
    - ` git pull `
    - ` git status `
        - identify conflicting files
    - edit conflicting file
        - conflicted region
            - \<\<\<\< HEAD
            - contents in repo
            - =======
            - contents in my commit
            - \>\>\>\>\>
        - remove HEAD and leave only parts to keep
    - ` git add file `
    - ` git commit -m “message” `
        - message is combined with “resolved merge conflict”
    - ` git push `
- to see the conflict in one file
    - ~/.gitconfig
        - \[merge\]
        - conflictstyle = diff3

### terminology

- basic
    - repository: collection of commits
    - the index or staging area: changes are registered in stage before commit
    - working tree: directory with .git subdirectory
    - commit: snapshot of working tree
        - the previous commit of HEAD becomes parent commit
        - HEAD moves to the new commit
    - branch: name of commit
    - upstream: main branch
        - Git uses “origin” as the remote name for the upstream repo
    - tag: name of commit with hash id, always same
    - master: main branch
    - head: present checked out branch and commit
        - when check-out a special commit, HEAD to the commit and it is “detached HEAD”
- advanced
    - fast-forward
        - history of commit A is included in B
        - not fast-forward relation
            - History of A is not included in B

## Collaborator work

### Permission as collaborator

- (manager) in web
    - Projectsettings/Manage access
    - Invite a collaborator using id in github

### Projects

- Managing your project
    - Managing project access
        - admins of organization-level
            - can invite individual collaborators and manage their access
        - admins of user-level projects
            - can invite individual collaborators and manage their access
        - project admin
            - control visibility of their project for everyone on the internet
    - managing access for organization-level projects

### Download

- Sites
    - [https://github.com/yhkimlab/NanoCore](<https://github.com/yhkimlab/NanoCore>) (No permission)
    - [https://github.com/starnmj/NanoCore](<https://github.com/starnmj/NanoCore>)
- Clone
    - ` git clone site `

### Check the status of the local directory

- ` git remote -v `
    - origin (server)
    - master (branch)
- ` git status `
    - check this directory is the newest one
        - it compares the HEAD of local repo and HEAD of master branch
    - if it doesnot properly work
        - set git branch upstream
- ` git branch `
    - ` git branch `
        - shows the downloaded branches in local
    - ` git branch -a `
        - all the local and remote branches
        - local branches: \* for the present branch
        - remote branches
- ` git log `
    - commit history
    - Note: commit HEAD
        - Just copy the front part of HEAD
- Move to the other version
    - ` git checkout HEAD_front `
    - ` git checkout master `
        - the latest version of master

### Pull request & merge on web

- merge
    - (on website)
    - Go to the new branch
        - “Compare & pull request”
    - (manager)
        - Test
            - In local repo
                - ` git checkout branchname `
        - Merge (pull) on website
            - Accept pull request
        - if pull is possible, pull request shows “merge pull request”
- repair merge conflict in command line
    - clone
        - ` git clone http:// `
        - ` git pull origin master	 already done `
    - ` git checkout jpark `
        - working
    - ` git merge master `
        - conflict error
    - push the change
        - ` git push -u origin jpark `

### Pull request from git push

- problem
    - I have cloned a github and modify and try to commit and push
    - another user already pushed several times so it is ahead of my previous branch
    - ` git murmurs `
        - I need to pull before push because it is ahead of mine
- solution
    - safe steps to keep local commit and sync with remote
        - Make a branch
            - ` git branch backup-local			cf. git branch vs checkout `
                - this is done after commit
                - this is safe copy of my current local commit
                - but git stays at master
        - Pull from remote
            - ` git pull origin master `
                - how to reconcile the diverge?
                - 1. git pull --no-rebase origin master
                - 2. git pull --rebase origin master
            - (old)
                - ` git checkout -b branchname `
                    - makes branch in local
                - commit in a new branch
                    - ` git add . -A `
                    - ` git commit -m “message” `
                    - can’t push now
                        - because there is not the branch
        - (1<sup>st</sup> time)
            - ` git push --set-upstream origin branchname `
        - check branch
            - ` git branch -a `
                - shows remote branch including new branch
            - In website, branchname appears
        - Then normal push
            - ` git add . -A `
            - ` git commit -m “message” `
            - ` git push `

### github and branches

- https://git-scm.com/book/ko/v2/Git-브랜치-브랜치와-Merge-의-기초
    - to do something in master,
        - A branch (iss53) need to be saved
        - A
            - if not commit  collision with branch to be checked, cannot checkout other branch
                - stash, commit amend or stashing and cleaning
    - now commit and move to master
        - ` git checkout master `
    - ` make a new branch and complete work `
        - ` git checkout -b hotfix `
    - merge hotfix to master
        - ` git checkout master `
        - ` git merge hotfix		# from master merge hotfix `
            - appears Fast-forward because C4 is based on C2
            - not merge, it is just push the commit
    - after merge hotfix can be removed
        - ` git branch -d hotfix `
    - go back to branch A and continue to work
        - ` git checkout iss53 `
        - go on work
    - merge master to A
        - ` git merge master		# merge master to A (iss53) `

## Personal Git

### general

- what is it?
    - built-in command
    - version control system for tracking changes in computer files and coordinating work on those files among multiple people
    - window, linux, Mc package
    - to use github
    - go to example
    - ` git options `
    - in using git to remote server
        - turn off module animation in .bashrc
- contents
    - ` git two remote `

### git port

- usable protocol
    - Local, SSH, Git, HTTP
        - Local, SSH, Git should be installed to be used
- Local
    - when repository locates in the same server
        - use path as URL
    - e.g.
        - ` git clone /opt/git/project.git `
        - ` git clone file:///opt/git/project.git `
        - ` git remote add local_proj /opt/git/project.git `
- SSH
    - ssh: write/read possible unique protocol
        - http, git: only readable
        - has identification step for login
    - as normal
        - ` git clone URL `
        - ` git clone ssh://id@server/project.git `
        - ` git clone id@server:project.git `
    - needs to setup SSH-git server
        - in case: anonymous push or let anybody pull it
    - e.g.
        - ` git clone ssh://id@host:[port]/dir `
            - if no \[port\], omit ‘:’
                - error: mydomain.com:no address associated with name
- git
    - port number: 9418&#9;&#9;cf. open port
        - not identification step
- smart HTTP/S
    - port
        - http
            - port 80
            - ` git clone http://.....git `
            - not encrypted
        - https
            - open port 443
            - ` git clone https://....git `
            - encrypted
    - change to 443
        - httpd opens 80
        - check apache
            - systemctl status httpd
                - active (running)
        - ` sudo vi /etc/httpd/conf/httpd.conf `
            - Listen 80 → Listen 443
        - sudo systemctl restart httpd
        - netstat

### main properties

- version
    - ` git --version `
- properties
    - no difference between each repos
        - but original repository has bare attribute
    - origin master
        - origin: default name of remote repo in pull and push
        - master: name of branch in remote repo
- three tree system: actually not tree, bunch of files
    - HEAD&#9;(cf. HEAD, HEAD2)
        - pointer to the present branch and commit
        - point to the present branch and the last commit when you commit or checkout
            - cf git log
        - snapshot of the last commit which is the parent commit to the next commit
            - ` git cat-file –p HEAD `
            - ` git ls-tree –r HEAD `
        - then push to repo
    - Index
        - something to be commit
        - last check out files and their contents in the branch
        - after changing files, the index is updated and “git commit” makes the index to new commit
            - ` git ls-files –s `
        - staging: to write index
    - working directory
        - above two trees are stored in .git but not conceivable to human
        - files are recognized by human called sandbox
        - then add to
- three trees matches?
    - ` make files in working directory `
        - ` HEAD == Index ≠ Working directory `
        - ` git status `
            - “changes not staged for commit”
    - ` git add . -A[--ignore-removal] `
        - --ignore-removal: does not delete removed files
        - HEAD ≠ Index == Working directory
            - writing to index is to be staged
        - ` git status `
            - “changes to be committed”
    - ` git commit -m “message” `
        - ` HEAD == Index == Working directory `
        - Message will appear in “git log”
        - ` git status `
            - no stdout
- checkout vs reset
    - https://git-scm.com/book/ko/v2/Git-도구-Reset-명확히-알고-가기
    - checkout a branch
        - HEAD points to the branch and the snapshot of last commit of the branch comes to Index and copy the contents of the new index to Working directory, the three trees are same
    - reset
        - inside the same branch, points to the pointed commit (HEAD)
            - HEAD points the same branch, does not change the branch but the branch points to the pointed commit
        - reset --soft
        - reset --hard
            - overwrite the working directory and cannot go back
- bare vs non-bare
    - ` git init --bare `
        - use bare for remote repository
            - makes env in the repo directory
            - ` source files are not shown `
            - normally it has .git extension
        - there is no file so no can bother another commits
            - “push “ pushes only commits, not real file
            - you can retrieve remote repository by git clone
        - cannot use source file-related command
            - e.g. git add a.txt
    - ` git init `
        - non-bare directory, working directory
        - where you can work
            - it makes .git subdirectory and install env in .git
        - use non-bare for work-tree (local work directory)
- short manual
    - if you have files, it is local working dir
        - ` make remote repository `
        - ` make local working dir to git repo `
            - ` git init (--non-bare) `
            - connect to remote repo
            - add, commit, push to remote repo
    - ` make clone `
        - ` git clone remote repo `
- initialize
    - usage
        - ` git config --global user.name “Joonho” `
        - ` git config --global user.email REDACTED_EMAIL `
        - ` git config --global color.ui auto `
        - ` git config --global alias.co checkout `
            - co for checkout
    - property
        - in different repo, can use different initialization
        - check
            - ` git config --global –list `
    - written in .gitconfig

### basic operation and status

- in local git
    - modify local git
        - ` git status `
            - up to date with ‘origin/master’
            - Changes not staged for commit: …
    - ` git add . -A `
        - ` git status `
            - up to date with ‘origin/master’
            - Changes to be commited: …
        - local & remote HEADs are same
    - ` git commit -m ‘test head’ `
        - ` git status `
            - ahead of ‘origin/master’ by 1 commit
            - nothing to commit, working tree clean
        - HEADs are different
            - HEAD check
                - ` git rev-parse master `
                - ` git rev-parse origin/master `
    - ` git push `
        - to remote repo
            - oldhash..newhash
        - both HEADs are same
        - ` git status `
            - up to date
            - nothing to commit, working tree clean
- in another local git
    - remote HEAD does not change while remote HEAD was changed in the main local
        - Why?
            - ` git status checks only .git/refs/remote/origin/master without interaction with remote server. `
            - up to date means that it is the same as the last pull of remote commit not current commit of remote.
    - to check behind
        - ` git remote show origin `
            - (local out of date) means it is behind
            - (up to date) means it is at the same commit with remote repo

### merge

- ` git more `
    - ` git command can be run in any location in the directory, that is, in subdirectory `
- how to use two local git directories
    - fast forward merge

Figure 8 Fast forward merge

- when nothing was changed in local master branch(monkey)

Figure 9 Git merge: When nothing was changed in master

- when there is change in local branch
    - need to merge

Figure 10 Git merge: both repos are modified

- when there is no collision
    - merge occurs
        - do merge and commit
        - if there is collision
            - modify by hands then pull and commit
    - two local git management

Figure 11 Pull and merge

- wrong: pull = fetch & merge
    - local M:
        - ` git push `
        - local N:
            - ` git add . -A; git commit -m “message”; git fetch; git merge `
                - raise error
            - ` git add .; git pull `
                - “git fetch” brings all the files without merge
                - then add those to HEAD and commit
                - ` git pull is done `
- ` make branch and merge later `
    - ` git checkout `
        - ` git checkout <hash> `
        - ` git checkout –b branch_name `
            - ` make branch and change to branch `
            - work in branch
        - ` git checkout master `
            - back to master
        - ` git branch –d branch_name `
            - delete branch
        - ` git push origin branch_name `
            - push branch to server
    - update local repo
        - ` git pull `
            - fetch server and merge to local repo
    - merge cf. merge
        - ` git merge branch_name `
            - merge other branch to the present branch
        - modify conflicted files
            - A: addition of a file
            - D: deletion of a file
            - U: file is unmerged
            - C: copy of a file into a new one
            - M: modification of the contents or mode of a file
        - resolve manually
            - ` git add filename && git commit -m “removed merge conflicts” `
        - ` git add filename `
            - ` git diff original_branch comparing_branch `
        - merge file marker
    - add tag to version
        - ` git tag 1.0.0 identifier `
        - ` git log `
    - maintain current local commits by creating a branch from master before reset
        - ` git checkout master `

### git practice

- ` make local working directory `
    - ` make git dir with empty directory				cf `
        - ` mkdir tutorial `
        - ` cd tutorial `
        - ` git init `
            - initialized empty git repository …/tutorial/.git
        - cf. make git dir w. data
            - This might make a “not working tree” error
                - after push
                    - “git add . “ is not working
                - ` make clone directory again and use it `
            - ` cd qc_data `
            - ` git init `
            - ` git add . `
            - ` git commit –m “git start” `
                - this procedure include the next process ii
    - ` git commit in local repo `
        - ` git status `
        - ` vi sample.txt `
            - add sentence “monkey can do git”
        - ` git status `
            - # untracked files:    sample.txt
        - ` git add sample.txt `
            - ` git add . [-A]		! for whole directory `
        - ` git status `
        - ` git commit –m “any sentence” `
            - makes HEAD
        - ` git status `
            - nothing to commit&#9;&#9;! perfect
        - ` git log `
    - ` make a local git with data files `
        - inside dir w. data
        - ` git init `
            - initialize empty git repo in .git
            - ` git status `
                - untracked file
                - nothing add to commit (not staged)
        - ` git add . -A `
            - ` git status `
                - new file
                - “git rm --cached \<file\>…” to unstage
        - ` git commit -m “test” `
        - modify v1.txt
            - ` git status `
                - modified
                - changes not staged for commit
                - ` git checkout -- <file>… to discard change in working directory `
- ` make remote repo `
    - ` mkdir remo `
    - ` cd remo `
    - ` git --bare init					cf. git init local `
        - this makes many directories
- local repo: setting and push
    - ` git remote add <name> <url> `
        - ` git remote add origin joonho@chi.kaist.ac.kr:/NAS1/Repository/git_tutorial `
    - ` git push -u origin master `
        - once use -u then master can be omitted later
        - for the first push to empty remote repo, repo name and branch name cannot be skipped
        - if “git push”
            - … current branch master has no upstream branch
- ` make clone `
    - ` git clone repo_directory [download_directory] `
        - ` git clone /NAS1/Repository/git_tutorial tutorial2 `
        - in remote
            - ` git clone id@ip_address:/path/to/repo `
            - ` git clone id@ip_address:~/path/to/repo `
        - \<stop fast lecture\>
    - ` cd tutorial2 `
    - ` vi sample.txt `
        - modify
    - ` git add sample.txt `
    - ` git commit –m “modify” `
    - ` git push `
- full from first local directory
    - ` git pull `
    - ` git log `
- Merge
    - when the local repo is different from remote repo
        - remote repo was modified from another repo
    - ` git pull `
        - shows the collision part
        - modify the collision part manually
    - ` git push `

### git merge practice

- ` make git dir `
    - ` make dir gold and file a.txt `
        - ` git status (only run in working directory) `
    - ` make repo and connected from gold `
    - ` git clone repo gnew `
- at gnew
    - modified a.txt and made new.txt
        - ` git status `
            - modified: a.txt
            - untracked file: use git add to included ..new.txt
            - no changes added to commit
        - ` git add . -A/ git status `
            - changes to be committed
                - modified a.txt, new file: new.txt
        - ` git commit `
            - 2 files changed…
            - ` git status `
                - branch is ahead of origin/master
                - nothing to commit
        - ` git push `
            - writing objects …
- gold
    - ` git pull `
        - Fast-forward: two files changed
        - new file is drawn
        - modified file is drawn
    - modified new.txt, delete a.txt
        - ` git status `
            - changes not staged for commit
            - deleted, modified
        - ` git add . -A `
            - changes to be commited
            - the same
        - commit and push
- new
    - modified new.txt
        - ` git status `
            - changes not staged for commit
            - modified new.txt
        - ` git pull `
            - error: local changes would be overwritten by merge
            - commit your changes or stash before merge
            - Aborting
    - first commit and pull
        - ` git add . -A `
            - ` git status `
                - your branch is behind ‘origin/master’ by 1 commit
                    - ` git pull to update `
        - ` git commit `
        - ` git pull `
            - remove a.txt
            - Auto-merging new.txt
            - Automatic merge failed: fix conflicts and the commit the result
                - it is written in the file

### deal with two remotes

- one is url, and the other is local
    - ` git remote rm origin `
        - ` make clean `
    - ` git remote add origin https://hopefulp@github.com/hopefulp/sandbox.git `
        - ` git remote set-url origin --push --add https://hopefulp@github.com/hopefulp/sandbox.git `
        - ` git push -u origin master `
    - ` git remote add nas /NAS1/Repository/sandbox.git `
        - ` git remote -v `
- with two url (?)
    - ` git remote set-url origin --push --add user1@repo1 `
    - ` git remote set-url origin --push --add user2@repo2 `
    - ` git remote -v `
- in case difficult
    - for safety, make local branch to save

### detached HEAD

- reference
    - [http://sunphiz.me/wp/archives/2266](<http://sunphiz.me/wp/archives/2266>)
- HEAD&#9;(HEAD1)
    - pointer to any reference (hash ID) at present
        - reference to the current branch-and-commit
        - a commit that you have checked in the working directory
        - on top of “git commit” when new commit is done
    - HEAD is only one
    - checkout
        - when you move HEAD to checkout branch, if the previous HEAD was detached HEAD (direct indicate), if you do not know the revision number,
            - you can’t go back
- logic of git
    - branch
        - ` git manage commit by branch `
        - Detached HEAD commit is not connected to branch  cannot manage
            - no graph, if you move the branch, it disappears
        - cf. VCS: version control system
            - HEAD indicate the last commit in the order of time
        - ` git HEAD indicates the last checkout, so, if the commit is not connected to a branch, the commit cannot be used `
        - How to solve the detached HEAD problem
    - HEAD
        - branch indicates a revision number of a commit
        - HEAD indicates the branch
- solve the detached HEAD problem
    - ` make a branch `
        - ` git checkout -b <new branch> `
            - all the modification is saved in new branch
            - then, merge to master
                - go to github  pull request  accept pull request : master is changed
    - stash and unstash
        - 변경 사항을 stash -\> master branch 체크아웃 -\> 변경 사항을 un-stash -\> master branch에 commit
    - summary
        - commit to branch
        - if it became the commit to a detached HEAD  make a branch or move the modification to the previous branch
- how to become detached HEAD
    - ` git checkout master^ `
    - ` git checkout HEAD~2 `
    - ` git checkout origin/master `
    - ` git checkout <tag name> `
    - ` git checkout <revision number> `
- attached HEAD
    - indirect commit
    - HEAD  branch  a specific commit
- detached HEAD
    - indicate a commit not indirectly but directly
    - if you are not on the latest commit
    - can point directly to a commit
        - being on unnamed, anonymous branch
- after move from a detached HEAD
    - how to find the lost commit
        - ` git reflog `
- e.g.&#9;cf HEAD1
    - when switch branches using checkout, HEAD is transferred to the new branch
    - when a repository is committed, HEAD is generated
    - ` which can be used for “git checkout HEAD” `
- just a forepart of HEAD to check out
- tracked files
    - once they are committed so it is under management

### gitk

- ` yum install gitk `
- run in the git repository

### git message

- ` git add <file>… to update what will be committed `
    - what will be committed == index
- ` git checkout --- <file>… to discard change in working directory `

### error

- fatal: protocol error: bad line length character: modu
    - related with module
        - turn off module in “.bashrc”
- error for identity
    - use git config
        - ` git config --global user.email “REDACTED_EMAIL” `
        - ` git config --global user.name “Joonho Park” `
        - ` git commit –m “test” `
- ` git pull, git merge error `
    - ` git merge error `
    - error:
        - Your local changes to the following files would be overwritten by merge
        - Please commit your changes or stash them before you merge
        - Aborting
        - # git merge commit
    - solution
        - ` git stach `
            - ` git stash			# save the present changes into stash `
            - ` git pull origin master	# apply origin changes into local `
            - ` git stash pop		# apply the changes and remove from stack `
        - at once
            - ` git stash && git pull origin master && git stash pop `
        - ` git add ? `
            - ` git add `
            - ` git commit -a `
            - ` git pull `

### git submodule

- whatitis
    - ` make git subdirectory inside git directory `
- ` make sub git directory `
    - ` git submodule add url `
        - cloning
- check
    - ` git status `
    - ls
        - .gitmodules
    - ` git diff --cached submodule `
    - ` git diff --cached --submodule `
- commit including submodule
    - ` git commit -am ‘added submodule’ `
    - ` git push origin master `
- clone including submodule
    - ` git clone url `
    - ` cd gitdir `
    - ls submodule
        - nothing
    - #additional two commands are required
    - ` git submodule init `
    - ` git submodule update `
- others
    - ` git clone together with submodule initialization `
        - ` git clone --recurse-submodules `
- ` git rm `
    - problem
        - the removed files on local repository are not removed in origin/master
    - ` git rm filename `
        - remove filename in local and remote directory
    - ` git rm --cached filename `
        - remove filename in remote directory but not in local directory

### multiple remote repo

- go to technique

### terminology

- ID: the designated name for a repository
- branch
    - branch points to the last commit in the branch
- staging
    - staged by “git add”
    - staging area: place git command will treat in “git commit”

### head to the old hash

- to recover the old hash
- using git reset and git push
    - method
        - ` git checkout branch `
            - branch to modify head
        - ` git reset --hard hash-id-to-put-as-head `
        - ` git push -f `
    - possible error
        - without -f
            - updates were rejected because the tip of your current branch is behind
- revert each commit you don’t want
    - ` git revert commit-id `

## technique

### recover a previous commit

- whattodo
    - disregard some recent commit
    - checkout a previous commit
        - ` make it the last commit and push `

### manage two working directories

- in any directory
- commit
- ` git pull – pointing to other working directory `

### manage two remote repositories

- comparison with svn
    - svn has only one remote repository
    - ` git can have several repositories `
- How to make a branch to a new remote
    - present
        - ` git remote -a `
            - remotes/origin/master
    - add the second remote, and then create a local branch
        - add the second remote
            - ` git remote add hub remote-url `
                - ` git remote add <remote-name> <remote-url> `
            - ` git remote -v `
                - remotes/origin/master
                - remotes/hub/master
        - create a local branch
            - no local branch to hub/master
        - download a new repo and make a branch
            - ` git fetch hub `
            - ` git checkout -b hubmaster --track hub/master `
                - hubmater is new branch to hub/master
    - check it
        - ` git remote -v `
        - ` git branch -vv `
    - Usage in new branch: hubmaster
        - hubmaster is set up to track hub/master
        - ` git pull `
        - ` git push `
            - ?git push hub HEAD:master
            - initial push
                - use --set-upstream
- Sync two remote repos
    - status
        - origin is ahead and hub is behind
        - (the ahead local has committed to its remote repo)
    - simple way:
        - check master (ahead) is updated
            - ` git checkout master		cf. go to master `
            - ` git pull				cf. update master `
        - copy master to hubmaster
            - ` git checkout hubmaster		cf. go to hubmaster `
            - ` git merge master			cf. copy master to here `
            - ` git push				cf. sync hubmaster to hub/master `
    - option2: update hubmaseter from origin/master
        - move to behind repo
            - ` git checkout hubmaster `
        - merge or rebase origin/master to hubmaster
            - ` git merge origin/master `
            - ? git fetch origin/master&#9;# hub/hubmaster is not working, hub/master?
            - ` git rebase origin/master `
            - if there are untracked file
                - ` git add <file> `
        - push to hub
            - ` git push hub hubmaster:master `
    - option2: sync github first
        - fetch everything
            - ` git fetch --all `
        - push origin/master to Github (overwrite)
            - ` git push hub orgin/master:master `
            - if github is ahead, use force
                - ` git push hub origin/mster:master --force `
- from git
    - ` make all ID `
        - ID
            - ` git push ID branch `
    - method
        - Create a new remote called "all" with the URL of the primary repo.
            - ` git remote add all git@github.com:jigarius/toggl2redmine.git `
        - Re-register the remote as a push URL (? necessary)
            - ` git remote set-url --add --push all git@github.com:jigarius/toggl2redmine.git `
        - Add a push URL to a remote. This means that "git push" will also push to this git URL.
        - ` git remote set-url --add --push all git@bitbucket.org:jigarius/toggl2redmine.git `
- setting 2<sup>nd</sup> repo using different name
    - ` git remote add alt alt_server:/path/to/repo `
    - ` git remote add alt https://alt_server.com/project/myproj.git `
        - if ID and passwd is required
            - ` git remote add alt https://userid@alt_server.com/project/myproj.git `
- setting two repos with the same name for push at once
    - ` make two repos as the same branch of origin `
        - ` git remote -v `
            - github&#9;https://github.com/hopefulp/eta2fe.git (fetch)
            - github&#9;https://github.com/hopefulp/eta2fe.git (push)
            - origin&#9;joonho@chi.kaist.ac.kr:/mnt/NAS1/Repository/eta2fe.git (fetch)
            - origin&#9;joonho@chi.kaist.ac.kr:/mnt/NAS1/Repository/eta2fe.git (push)
    - ` git remote set-url origin --push --add <a remote> `
        - ` git remote set-url origin --add --push https://github.com/hopefulp/eta2fe.git `
            - github&#9;https://github.com/hopefulp/eta2fe.git (fetch)
            - github&#9;https://github.com/hopefulp/eta2fe.git (push)
            - origin&#9;joonho@chi.kaist.ac.kr:/mnt/NAS1/Repository/eta2fe.git (fetch)
            - origin&#9;https://github.com/hopefulp/eta2fe.git (push)
    - ` git remote set-url origin --push --add <another remote> `
        - ` git remote set-url origin --add --push joonho@chi.kaist.ac.kr:/mnt/NAS1/Repository/eta2fe.git `
            - github&#9;https://github.com/hopefulp/eta2fe.git (fetch)
            - github&#9;https://github.com/hopefulp/eta2fe.git (push)
            - origin&#9;joonho@chi.kaist.ac.kr:/mnt/NAS1/Repository/eta2fe.git (fetch)
            - origin&#9;https://github.com/hopefulp/eta2fe.git (push)
            - origin&#9;joonho@chi.kaist.ac.kr:/mnt/NAS1/Repository/eta2fe.git (push)
    - check it
        - ` git config -e `
- usage
    - ` git remote update `
        - bring all the updates from remote (not merged to HEAD)
    - ` git pull alt master `
        - fetch from alt and pull to HEAD

### clean git history

- why happen
    - in personal git, sometimes larger size of file was committed
        - but github permits only \< 50M for each file
        - At the moment, no larger files but it is included in git history
    - need to clean git history
- recipe
    - in local repo
        - rm -rf .git
        - ` git init `
        - ` git add . `
        - ` git commit -m “initial commit” `
        - ` git remote add origin <url> `
            - \<url\> = [joonho@chi.kaist.ac.kr:/mnt/NAS1/Repository/eta2fe.git](<mailto:joonho@chi.kaist.ac.kr:/mnt/NAS1/Repository/eta2fe.git>)
        - ` git push -u --force origin master `
            - check branch name by “git branch -a”
    - remote repo is also cleansed by this
- if another local repo
    - remove repo and do git clone

### keep my branch while main is developing

- ` make my local branch `
    - ` git checkout -b jpark `
- keep main updated
    - ` git checkout main `
    - ` git pull origin main `
        - my local main matches the upstream main
- Merge updates into jpark
    - ` git checkout jpark `
    - ` git merge main `
        - This merge only the new commits from main into jpark
            - if no conflict  fast forward
            - if conflict  manual resolve
- merge problem&#9;&#9;&#9;cf. merge, merge1
    - if a file changed in main and changed in jpark  merge conflict
        - only if both you and main modify a.py, Git will stop and ask you to resolve conflicts manually
    - if a file changed in main but not in jpar  git applies the new changes
    - if a file change in jpark but not in may  git keeps my version without conflict

## git options

### all the options

- basic
    - clone, add, commit, push, pull, config, remote, log
- advanced
    - reset, fetch

### basics: clone, add, commit,

- error
    - environment module collides with git
        - comment out modules in .bashrc
        - ` git push : protocol error `
        - ` git pull: `
- ` git clone `
    - whattodo
        - ` make clone of remote directory to local `
            - copy remote directory
    - ` git clone server_dir.git [local_dir] `
        - server\_dir.git
            - when server is remote url
                - remote path = SSH url
                - [git@bucket.org:roy/path](<mailto:git@bucket.org:roy/path>)
        - local\_dir
            - local directory name
            - w/o local
                - dirname of server is copied
                - if it is a.git, ~/a is made
    - ` git clone server local_dirname `
        - ` git clone joonho@chi.kaist.ac.kr:/Data/Repository/draw_qcmo_gs draw_qcmo_gl `
- ` git add .				! local repo `
    - add files to index
        - before the commit, index can be changed whatsoever
    - options
        - ` git add . –A `
            - add deleted paths&#9;! ! when some files are removed
        - ` git add . –-ignore-removal `
            - not add deleted paths
- ` git commit `
    - ` git commit –m 1 `
        - it is added to HEAD
        - these change stays in head of local repository
        - whenever commit, it has check point
        - save in .git/objects
            - locals: .git/refs/heads/
            - remote: .git/refs/remote/
    - options
        - -m “add explanation”
    - commit error
        - error: Changed but not updated
            - some files were deleted but it is not committed
        - ` git commit –a –m “message” `
- ` git config `
    - -l, --list
        - user.email=
        - user.name=Joonho
        - push.default=simple
        - core….
        - branch.master.remote=origin
        - branch.master.merge=
        - remote.origin.url=
        - remote.origin.fetch=
        - remote.github.url=https://
    - if not defined user
        - impossible to do Github count
        - initial setting
    - user setting
        - global setting
            - ` git config --global user.name “Your name” `
            - ` git config --global user.email “email address” `
        - local setting, at each repo
            - ` git config --global user.name “your name” `
            - ` git config --global user.email “email address” `
    - view
        - global setting info
            - ` git config --global --list `
        - local setting info
            - ` git config --list `
    - ` git config --local receive.denyCurrentBranch updateInstead `
        - if you cannot push due to the above setting
            - error
                - Working directory has staged changes
                - error: failed to push some refs to …
            - gif config receive.denyCurrentBranch ignore
    - ` git config --global push.default matching `
        - push all the branch
    - ` git config --global push.default simple `
        - push current branch
- ` git stash `
    - save uncommitted files before overwrite by merge such as git pull
- ` git help `

### status

- ` git remote update `
    - to bring remote refs up to date
    - cf. git fetch origin&#9; to fetch remote to local
- check local HEAD ahead or behind remote
    - ` git fetch origin `
    - ` git status -sb `
        - ## master…origin/master \[behind 4\]
- ` git status -uno `
    - whether the present git is ahead, behind, or has diverged.
    - if it says nothing, the local and remote are same
- how to check the present status
    - ` git status `
        - nothing to commit

### push

- makes branch of master in origin (bare repo)
    - ` git push origin master `
- load changes on remote server
- cf. push.default: git config --global
- collision error
    - ` git push -f `
        - --force
    - ` git push origin master --force `
    - if there is unsaved file
        - your local change to the following files would be overwritten by merge, … commit your changes or stash them before you can merge
    - ` git stash `
- to use ‘git push’
    - receive.denyCurrentBranch updateInstead
- ` git push –u origin master `
    - once use –u then master can be omitted later
    - for the first push to empty remote repo, repo name and branch name cannot be skipped
- if ask id/pass from remote url
    - use set-url

### fetch

- fetch remote repo to local repo but not merge
    - ` git fetch origin `
        - get all the branches in origin
        - can check HEAD of remote and local by status
    - ` git fetch --all `
    - ` git fetch origin master `
        - only fetch master branch
    - local repo does not change
        - ` git pull == git fetch + merge `
- FETCH\_HEAD
    - all the remote branch head is recorded in .git/FETCH\_HEAD
        - available after using git fetch
- ` make branch newest `
    - fetch master
        - ` git checkout master `
        - ` git fetch `
        - ` git pull origin master `
    - newest branch
        - ` git checkout branch `
        - ` git reset --hard origin/branch `
            - if you are in modification,
                - ` git stash		 stash `
                - ` git reset --hard `
    - check the recent history of remote
    - fetches to no-name branch in local
        - branch name ‘FETCH\_HEAD’
        - if you want to pull
            - merge FETCH\_HEAD
            - or pull
                - pull == fetch + merge
- pull vs fetch
    - pull
        - when remote repo has only newest version
    - fetch
        - when local has a newest version
        - ` git fetch, then, modify conflicts `
            - then, merge or git pull
            - in case of merge, you can use FETCH\_HEAD

### pull

- ` git pull			cf git pull  overwrite `
    - basic mode
        - pull = fetch + merge
        - ` git fetch followed by git merge FETCH_HEAD `
            - generate git merge commit
    - ` git pull origin master `
        - it fetches and merges
            - origin: url name, master: branch
        - save local changes to branch
            - cf. branch
        - ` git pull w/o [origin master] `
            - .git/configure
                - \[branch “master”\]
                    - remote = origin
                    - merge = refs/heads/master
    - Marks
        - U file is unmerged
        - M&#9;modified
        - D&#9;deleted
        - A&#9;addition
        - C&#9;copy of a file into a new one
        - R&#9;renaming of a file
        - T&#9;change of type of the file
        - X&#9;unknown
    - e.g.
        - pull is not possible because of unmerged files
- conflict in pull
    - remote is ahead of local repo
    - error
        - Pulling without specifying how to reconcile divergent branches is…
            - ` git config pull.rebase false `
            - ` git config pull.rebase true	 mv local HEAD to remote last commit `
                - normal: if conflict occurs (can’t merge), you need to fix up by yourself
            - ` git config pull.ff only `
        - Head: A - B by another
        - ﹂C by me
            - rebase: A - B - C &#9; fetch B & rewrite C on B, good for solo
            - merge (no-rebase): A - B - M(C)&#9; fetch B & merge C on B, good for collaboration
    - three options for pull
        - rebase, merge (no-rebase), fast forward
        - ` git pull --no-rebase origin master `
            - --no-rebase == --merge
            - preserve full history (good for collab)
            - fetches remote changes and then merges them into local branch
                - show all merge history
                - if no conflict, merge will succeed in
                    - ` git push `
        - ` git pull --rebase origin master `
            - rewrite history, cleaner, linear history, good for solo jobs
            - fetches remote changes and then reapplies local commits on top of the fetched remote changes.  It effectively rewrites local branch’s history
            - may need --force-with-lease
                - ` git push origin master --force-with-lease `
- how to fix unmerged files for the above case
    - status
        - remote: A  B  C  D
        - local:   A  B\*
    - two options
        - option 1: ignore local change
        - option 2: retain the local change
- option1: Ignore local change, overwrite the local changes
    - method 1
        - ` git reset --hard origin/master `
            - resets local to remote origin/master
            - --hard changes all the files in working directory to match the files in origin/master
        - ` git reset --hard HEAD  not working `
            - local: B not B\*
            - ` git pull `
                - local: D
    - method2 – not working
        - ` git checkout `
    - N.B.
        - ` git reset --hard `
            - would be different
                - not working  do not use
            - modification in local disappears
        - 3 step
            - ` git branch -d master `
            - ` git fetch origin master `
            - ` git checkout -b master origin/master `
        - cf. git fetch --all
            - downloads the latest from remote without trying to merge
- option 2: retain local change
    - It looks that already M, A, D are reflected to origin/master
    - You can open each file in your IDE and look for the following symbols:
        - \<\<\<\<\<\<\< HEAD
            - // your version of the code
            - =======
            - // the remote's version of the code
            - \>\>\>\>\>\>\>
        - fix up the file
        - ` git add file `
        - ` git commit -m “m” `
        - ` git pull `
    - fix U
        - ` git rm U-file `
            - whether U is already removed from local
        - commit again
            - ` git add . -A `
            - ` git commit -m “ok” `
            - ` git pull `

### merge

- to merge branch A to B
    - in case approve the changes of remote branch
        - ` git merge remote `
- resolve conflict
    - in python, .pyc files
        - .pyc is updated constantly because of ‘git add . ‘
        - not track
            - ` git rm `
            - ` git .gitignore will not track .pyc `
            - ` vi .gitignore `
                - \*.py\[cod\]&#9;&#9;# \*.pyc
                - \_\_pychche\_\_/
        - if not, remove all .pyc files
            - find . -iname ‘\*.pyc’ -exec rm \{\} \\;&#9;# \\; is necessary
            - find . -name \*.pyc \| xargs rm

### diff

- whatitis
    - the changes in local git, the changes in staging for commit, diff between repos
- ` git diff brA brB `
    - the changes in untracked files
        - ‘-‘ &#9;deleted
        - ‘+’&#9;added
- ` git diff --cashed `
    - changes in tracked files on stage
- ` git diff HEAD `
    - HEAD: latest commit in the branch

### show

- ` git show HEAD `
- ` git show index `
- ` git ls-file [-s] `
- ` git cat-file –p HEAD `
- ` git ls-tree –r HEAD `

### branch

- https://stackoverflow.com/questions/43550302/what-is-the-base-branch-when-a-new-one-is-created
    - base branch (actually no base branch)
        - ` git checkout -b newbranch `
            - newbranch is made based on the base branch (present branch, current code)
    - current commit (only exists)
        - A - B - C -- master
            - each commit has its own hash ID
            - branch can grow with a new commit
        - can pick any one of these commits and make a new branch
            - A
            - \\
            - B   \<-- newbr
            - \\
            - C
            - \\
            - D   \<-- master
        - ` make a newbr from B `
            - ` git branch newbr <thing-that-finds-B> `
                - using hash ID
                - branch name
            - another branch to B
                - ` git branch thirdbr newbr `
                    - add new branch label therdbr to B commit
    - tip commit
        - commit to which a branch name points
    - we only have one branch at the time
        - ` git checkout thirdbr `
            - A--B   \<-- newbr, thirdbr (HEAD)
            - \\
            - C--D  \<-- master
            - HEAD indicates B in thirdbr
                - HEAD is how git knows which branch-and-commit are the current branch and commit&#9;(cf. HEAD, HEAD1)
        - new commit  HEAD automatically moves to tip commit of the branch
        - checkout a commit and make a new branch
            - ` git checkout -b newname commit `
- subcommands
    - ` git branch	[ no subcommand] `
        - show all the local branches
        - find local and remote branches
            - output
                - \* : the current branch
    - ` git branch newname			# git branch vs checkout `
        - ` make a new branch `
        - the new branch is equal to the present branch
        - ` git checkout -b newbranch `
            - making newbranch and move to the newbranch
    - move to another branch
        - ` git checkout branch `
        - ` git switch branch `
- Options
    - Without option
        - List the existing branches in local
            - Whenever checkout a branch, it is included in local
    - -r: list remote branches
    - -a: list all branches
    - -u: --set-upstream-to
    - -d: delete branch
    - -m: rename or modify
        - ` git branch -m master hubmaster `
        - set up track
            - ` git branch --set-upstream-to=hub/master hubmaster `
- update remote branches (?)
    - ` git remote update `
    - ` git remote update origin –prune `
- delete branch
    - local
        - ` git branch -d branchname `
    - remote branch
        - ` git push origin --delete branchname `
- rename branch
    - in another branch
        - ` git branch -m oldname newname `
    - in the current branch
        - ` git branch -m newname `
- rename branch and push to origin
    - ` git branch -a `
        - jpark
        - modularize
    - ` git branch -m jpark vasp `
    - ` git branch -m modularize jpark `
    - ` git push myrep :jpark vasp `
        - in repo
            - jpark deleted
            - vasp  vasp \[new branch\]
    - ` git push myrep :modularize jpark `
        - in repo
            - modularize deleted
            - jpark  jpark \[new branch\]
- set upstream
    - sometimes git status shows
        - nothing to commit, working directory clean though I made a change in a local directory
    - set upstream
        - ` git branch --set-upstream-to origin/master	! or `
        - ` git branch -u origin/master `

### log

- to see the commit list
    - brief history with commit
        - commit: HEAD and message, date
        - show commit history chronically
        - how to get out
            - :q
                - Quit
        - s
        - ` git log -p `
    - ` git log br1 br2 `
        - show commits not in br1 but in br2
- options
    - --stat
        - show long history
    - --oneline \[ --branches \[ --graph \] \]
        - each commit with one line
    - -n
        - display n commits
        - e.g.
            - ` git log -1 `
            - ` git rev-parse HEAD `
- e.g.
    - ` git log --oneline -1 `
    - ` git log --oneline -2 `

### checkout

- ` git checkout [HEAD|branch] `
    - branch
        - move to another branch with the latest HEAD
        - if the branch name is the same
            - checkout the latest HEAD
    - HEAD
        - move to another commit point, HEAD
            - it is an old version
            - retrieve the version at the HEAD point
            - check the point by “git log”
- option
    - \<branch\>
        - switch to branch
    - -b \<branch\>
        - ` make a new branch and chekcout `
        - ` git checkout -b newbranchname `
    - -t \<remote/branch\>
        - check out remote/branch with the same name
        - -b name -t \<remote/branch\>
            - change the branch name
- check out old version
    - ` git log `
        - ` git show HEAD^:./file.py `
            - HEAD# committed before
                - HEAD^^
                    - up to tow commit before
                - HEAD~4
            - shows the old version file
        - ` git show HEAD^^:./file.py > new.py `
            - retrieve an old version file
    - ` git checkout HASH `
    - modification
        - if want to create a new branch to retain new commits
            - ` git switch -c newbranch `
        - undo commits
            - ` git switch - `
- ` git checkout with aborting the modification in a present branch `
    - ` git checkout -f branchname `

### reset

- HEAD keeps the present branch
- change HEAD to another commit
    - ` git reset <head name> `
- soft reset
    - ` git reset --soft HEAD~ `
        - HEAD~ is the parent HEAD
        - just move HEAD to the new commit (HEADname)
        - HEAD~1: remove last commit
    - do not change index
    - keep the changes in the working directory
- reset --hard
    - can remove files
        - the final version is committed, then it can be recovered by reflog
            - but if it was not committed, it cannot be restored
    - ` git reset --hard ID/branch  git pull overwrite `
    - ` git reset --hard HEAD~ `
        - to reset the working directory to a clean checkout from master git reset
    - ` git reset --hard HEAD~1 `
        - remove last commit and discard changes
        - will delete any uncommited changes
- mixed reset
    - --mixed is default
    - index update to the present HEAD
        - M v2.txt
        - unstaged changes after reset
    - ` git reset --mixed HEAD~1 `
        - undo last commit but keep changes staged
        - Files remain unchanged
        - the changes are unstaged
- if already pushed the commit and want to remove if from the remote
    - reset locally first by soft, hard, or mixed
    - ` git push --force		! attention: force-pushing can overwrite collab’s changes `

### remote

- ` git remote					cf remove repo `
    - shows all the repo with alias name
    - ` git remote -v `
        - shows repos with url
        - as for the same remote
            - one for fetch
            - one for push
        - e.g.
            - github&#9;https://github.com/hopefulp/eta2fe.git (fetch)
            - github&#9;https://github.com/hopefulp/eta2fe.git (push)
- subcommand
    - add
        - to add another remote repo
        - ` make github `
        - ` git remote add origin url `
            - “origin” is name of remote repo
        - modify URL rather than remove
            - ` git remote set-url origin http://id@server/a.git `
        - set origin for two repos&#9;cf. git\_multirepo
    - set-url
        - change url
            - ` git remote set-url remote_name(origin) https://... `
            - ` git remote set-url origin joonho@chi.kaist.ac.kr:/mnt/NAS1/Repo/a.git `
            - (https url) git remote set-url origin [https://github.com/id/a.git](<https://github.com/id/a.git>)
            - (ssh url) git remote set-url origin git@gitlab.com:..../...git
        - to keep id/passwd in github
            - ` git remote set-url github https://github.com/id/a.git `
                - it asks id/passwd
            - ` git remote set-url github https://id@github.com/id/a.git `
                - it asks only passwd
            - ` git remote set-url github git@hithub.com:id/a.git `
                - without authority it complains
    - show
        - ` git remote show origin `
            - to compare with remote repo
    - remove repo
        - remove branch
            - ` git push origin --delete branch-name `
        - ` git remote remove origin `
            - ` git remote rm origin `
            - cf. git remote add
    - update
        - when remote branches are deleted in remote repo
        - ` git remote -v: shows still the deleted branches `
        - ` git remote update origin --prune `
            - get remote branches
    - rename
        - ` git remote rename origin hub		cf see also rename branch `
- to approach the remote branch
    - error: cannot update paths and switch to branch
    - ` git remote update `

### stash & unstash

- points
    - situation
        - during some jobs, another request comes and just stop for a while and need to change a branch
        - stash but not commit then reload and continue the job
    - ` git stash `
        - just save modified files in working directory
    - files to be stashed
        - modified and tracked
        - in staging area
- contents
    - save temporary
        - ` git stash `
        - ` git stash save:	save the present jobs and branch goes to HEAD `
        - ` git stash push:	can use option: -m message `
    - list stash list
        - ` git stash list `
    - apply stash
        - ` git stash apply	still remained in stash list, get newest version `
        - ` git stash pop	remove stash list and apply `
        - ` git stash apply --index	recover staging files `
    - remove stash
        - ` git stash drop	remove the recent stash `
        - ` git stash clear	remove all the stash `

## Fork and AI

### fork

- original github
    - fork (top right menu)//create fork  generate git repo on my own github
- my github
    - for wiki
        - change display link address
            - right side of Code  about  next toothed wheel
            - change http address or check my website
        - turn on web browser function

<br>

## GNUPLOT

## Bash or gnu script

### Bash

- ext: sh
    - gnu\_1f\_nc.sh
        - ` #!/bin/bash `
        - run
            - gnu\_1f\_nc.sh fname args
- script
    - bash command
    - gnuplot -persist \<\< EOF
        - gnuplot command
    - EOF

### Gnuplot script

- ext: gplot, gps, ps, figure files
- run
    - gnuplot --persist ae.gplot

## plot

### plot

- ` RANGE=”[:] `
- gnuplot -persist \<\< EOF
    - setting
        - set xlabel
    - plot
        - plot \<range\> plot-element \{, ,plot-element, …\}
        - plot $RANGE $STYLE
    - EOF

### gnuplot command

- set
    - whatitis
        - just setting until plot, splot, replot
        - show command report the current setting
        - unset  setting goes to default
    - subcommands
        - multiplot
        - size 0.5,0.5
        - origin 0.0,0.5
    - e.g.
        - set print “-“&#9;&#9;# output to printer, define at the front
        - set style data lines
        - set multiplot
        - set size 0.5,0.5
        - set origin 0.0,0.5
        - set nomultiplot
        - there\_is\_s=\`test -f AEWFNR0 && echo 1 \|\| echo 0\` # command
        - print there\_is\_s&#9;&#9;# can print STDOUT

### using

- read data from data file
- format
    - plot file using \{\<entry\> \{:\<entry\> …\} \{format\}
    - entry: column number enclosed by ( ) or not
        - (1): 1<sup>st</sup> item
        - $1 == (1)
        - col(0) is sequence
        - valid(N) test whether there is N-th column
- style
    - u 1 = same as 0:1
        - integer is the number of column starting from 1
    - u 1:2 = u $1:$2
    - u 1:($2+$3)
    - plot ‘file’ u 1:2 w l lw 2; replot …
- replot

### loading gnufile

- \>load ‘plotwfc.gnu’

## set figure design

### range

- set xrange \[xmin:xmax\]
- set yrange \[ymin:ymax\]

### label

- set title
- label
    - set label “string” at x, y &#9;&#9;! x, y for position coordinates
        - set label “Si LDA” at 4.0, 2.5
        - set label “1s” at 0.2, 2,2
        - set label “2s” at 0.8, -1.3
    - set xlabel “a.u.”
    - set ylabel “\{/Symbol y\}\_\{nl\} (r) “

### text

- subscript
    - title=”E\_\{RMSE\} \[eV/atom\]”
- superscript
    - title=”x^\{2\}”

### style

- linetype == lt
    - lt number
    - lt -1&#9;black

## output

### encoding

- set encoding iso\_8859\_15

### terminal

- set terminal postscript enhanced solid color “Helvetica” 20

### output

- set output “gnuplot.ps”
- ps can be seen by

### key

- set key off

## 3D plot

### splot “his2d.txt” w style

## output

### default

- when x11 is working
    - Terminal type set to ‘x11’

### write file

- \>set term png
    - write png file

<br>

## TCL/TK

## TCL

### whatis

- tclsh, wish after Tcl installation&#9;&#9;&#9;cf. necessary for environment module
    - wish is extension of tclsh to interpret Tk
- alternative to csh, sh
- tclsh prompt
    - %

### execution

- ` source filename `
- script
    - ` #!/usr/bin/tclsh `
    - command line argument
        - a.tch arg1 arg2 …
            - argv0 is a.tch&#9;&#9;&#9;! script name
        - argv = \{ arg1 arg2 … \}&#9;&#9;&#9;! list
        - argc: number of argument, integer

### syntax - comment

- sentence
    - ; semicolon terminates sentence
    - comment
        - start line with ‘#’
            - # bla..
        - in line use ;#
        - block comment, use if 0 \{  \}
    - \\ is for connection line
        - comment
            - # bla…\\
            - comment is continued  \\
            - this is comment too
        - sentence
            - for (set $i) \{… \\
                - sentence is connected
- command format
    - command arg1 arg2 …
        - return or ; next sentence
    - grouping and substitution can extend the above
        - grouping \{   \}
        - substitution \[   \]
- data structure
    - string = “This is string”
    - list dos not has index
        - for short data
        - set list\_name \{val1 val2 …\}
        - lindex $list\_name 0&#9;&#9;&#9;! return 1<sup>st</sup> index
        - list = \[ list 1 2 3 \]
    - array
        - for long data
        - index is string also -\> it’s like hash
        - 2 types of declaration
            - set my\_arr(index) value
            - array set my\_arr \{ ind1 val1; ind2 val2\}
        - set array(2,3) Sat&#9;&#9;&#9;&#9;! array
            - puts $array(2,3)
- basic
    - variable
        - declare
            - set var value
        - referenced by $
            - puts $x&#9;&#9;&#9;! prints
            - prevent substitution by \\
            - puts $$
                - prints $
    - expr for math
        - expr 3 + 1
    - preprocess of \[   \]
        - set I \[ expr $j + 1 \]
    - list by grouping
        - use \{ \}, “  “
            - \{   \} does not permit substitution
            - “   “ permits substitution
        - set var \{apple orange banana\}

### proc

- function define
    - proc pname arg\_list \{    \}
- call proc
    - pname \{args\}
    - pname arg1 arg2 …

### keywords

- set
    - set var value
        - if there is value, value is assigned to var
    - set var
        - if there is not value
        - print value of var if not $
    - set $var
        - print value of $var if there $
    - e.g.
        - set li \{a b c\}
        - set name li
        - set name
            - li
        - set $name
            - a b c
- info exists var
    - boolean
- puts arg
    - puts “bla… “
- incr var \[arg\]
    - means “x = x + 1”
    - incr x -3
- append
    - set x 1
    - append x “00”&#9;&#9;&#9;&#9;! returns x=100
- eval

### condition and loop

- if, while, for, foreach, switch, continue, break
- if
    - if \{ $x \< $y \} \{ ….\}
    - else if \{   \} \{   \}
    - else \{    \}
- while \{Boolean\} \{
    - incr a \}
- for start test next command
    - for \{set i 1\} \{$i \<= 10\} \{incr i\} \{ puts i \}

### namespace

- whatis
    - collection of commands and variables
    - Tcl has always had one namespace called global namespace
- namespace eval
    - create new namespace
    - e.g.
        - namespace eval one \{
            - variable greeting hello&#9;&#9;! define new variable of greeting
                - \}
        - set one::greeting \[new\_value\]
        - put $one::greeting

### env variable

- env
    - when tcl runs, it starts a new process
    - the process is given a set of variables called environment variables, that is, default
    - env is list of keys of env variable
- parental shell environment
    - $::env
        - $::(env\_var)&#9;returns value of env\_var
            - puts $::env(HOME) $::env(PATH)
                - /home/joonho,
- shell variables set but not put into the environment are not accessible by child process
    - set MODULE\_SOURCE /qcfs/joonho/sandbox
        - this can be read in other tcl script
            - ` source file `
            - use $MODULE\_SOURCE
        - but cannot be load in python by os.env(MODULE\_SOURCE)
    - ` setenv MODULE_SOURCE /qcfs/joonho/sandbox `
        - this is set in parental shell
        - can be load in python

## TCL command

### array

- cf. module commands
- to make array
    - set arr(0) 1&#9;&#9;&#9;! this makes arr array with initialization
    - for \{set a 1\} \{$a \<= 10\} \{incr a\} \{
        - set arr($a) \[expr $a \* $arr(\[expr $a -1 \]) \] \}
- options
    - names
        - array names
        - foreach index \[array names arr\] \{ command \}
            - returns array hash-names
    - get
        - returns name and values in set
        - array get arr
        - array get env HOME
            - env command gets array and get gets name of HOME
    - set
        - “array set “ might be same as “set”

### string

- string option argument
- option
    - comp

### append

### env

- shows env variables and values
- it is connected with shell

### exec

- run other program
- exec /bin/bash –c “source path arg”
    - exec /usr/bin/bash –c “source $HOME/anaconda3/bin/activate”

### file

- manipulate file name and attribute
- options
    - exists
        - file exists filename&#9;&#9;! if it exists, return 1, otherwise 0
    - mkdir
        - file mkdir dirname

### format

### info

- info library&#9;&#9;! location of library

### puts

- simple
    - puts “this is tcl tutorial”
    - puts stdout “this is”
    - puts \[open messages w\] “this is “
        - cat messages
            - this is
- stdout for shell command
    - puts stdout “source $HOME/anaconda3/bin/activate”
- error
    - use only one argument
        - error: “puts $qc $home”

### scan

### set

- set var \[value\]
    - return var if not value
    - save var to value if value
    - set resolves namespace when it creates var
- use variable to first declare a variable in a namespace before using set to modify that variable
- if value has ( ), it is array

### source

- including tcl script
    - ` source /usr/local/Module/modulefiles/use.own `
    - all the values in sourced file comes into global namespace of sourcing file
    - to run bash source, use exec or puts

### package

- require
    - include package

### variable

- declare variable in the namespace

### not keyword: setenv

- ` setenv is not keyword of tclsh `
    - cf. modulefile keyword

## library

## package

### Tk

- usage
    - package require Tk
- pack
- every
- set ::time
- clock
    - clock second\[seconds\]&#9;-\> 1522028911
    - clock format \[clock seconds\] &#9;-\> Mon mar 26 10:49:05 KST 2018
    - clock format \[clock seconds\] –format %H:%M:%S&#9;-\> 10:49:05

## wish

### clock

- canvas

### proc drawmarks

- set angle
- set x1
- set x2
- set y1
- xety2

<br>

## Ubuntu

## install

### as Virtual Machine

- Host Windows 10
    - VB 5.2 can use full size of display
        - higher version cannot use full screen even w. guest addiaion

### version

- 20.04
- version check
    - launcher/system setting//All Setting/System/Details/Overview
    - lsb\_release -a
- upgrade without disconnecting servce (for web service)
    - ` sudo apt update `
        - if errors, they should be fixed
        - error in teamviewer, cuda
            - teamviewer
                - sudo rm /etc/apt/sources.list.d/teamviewer.list
                - sudo apt-key list \| grep -i teamviewer
                - if there is key
                    - sudo apt-key del \<KEYID\>
            - cuda
                - better to remove and install after new OS
                - sudo rm /etc/apt/sources.list.d/cuda\*
                - sudo rm -rf /var/cuda-repo-ubuntu2004-\*
    - ` sudo apt upgrade `
    - ` sudo apt full-upgrade -y `
    - tmux (terminal multiplxer)
        - to sustain ssh connection stable during do-release-upgrade
        - run before long and vurnerable task
        - run do-release-upgrade inside tmux
    - sudo do-release-upgrade
        - if no error in previous step, it starts to upgrade
            - fails if there is error in update/upgrade
        - middle ask
            - restart services  y
            - reinstall firefox snap
            - sshd\_config&#9; keep the local version currently installed
    - sudo reboot
        - check version
        - web service
            - systemctl status nginx
            - systemctl status apache2
        - port check
            - ss -tuln

### 9 recommended things after 17.10 Ubuntu installation

- [https://itsfoss.com/things-installing-ubuntu-17-10/](<https://itsfoss.com/things-installing-ubuntu-17-10/>)
    - Update your system
        - update & upgrade
    - Enable Canonical Partner repositories
        - Super key(Windows key)/software & update/ open it
        - tab//other software/check Canonical Partners
    - install media codecs
        - ` apt-get install Ubuntu-restricted-extras `
            - use Tab\_key to click “OK”
    - install software from center
        - VLC: media player for videos
        - GIMP: photoshop alternative
        - Shutter: screenshot
        - Calibre: eBook management
        - Chromium: web browser
        - Kazam: screen recorder tool
        - Gdebi: package installer for .deb package
    - install from web
        - Chrom web browser
        - Slack
        - Dropbox
        - Skype
        - Viber: instant messenger
    - Tweak

### host guest Ctrl^C & V

### packages

- Hangul
    - shift/space bar for changing language
    - H/E key

## Ubuntu-desktop version

### root

- did not make root passwd at installation
    - ` make root passwd	N.B. Now the user is sudoer `
        - sudo passwd root
            - ` make passwd `

### ssh

- open ssh port
    - ` sudo apt install openssh-server `

### directional key

### command to other user

- sudo -u USER bash -c ‘command’

## desktop

### terminal

- find terminal
- install new terminal
    - $gnome-terminal –show-menubar
        - when menu bar does not appear
        - when right-click is not working

### favorite/ launcher

- 1<sup>st</sup> run application
    - short cut appears in launcher
- two-finger tap / lock to launcher

### network

- https://choco-life.tistory.com/39
- modify /etc/netplan/00-…yaml&#9; sudo vi /…

network:

ethernets:

enp6s0f0:

addresses:

- 143.248.148.4/24

gateway4: 143.248.148.1

nameservers:

addresses:

- 143.248.1.177

- 143.248.2.177

search:

- 143.248.1.177

-143.248.2.144

version: 2

- apply
    - sudo netplan apply

## Applications

### cuda

### apache

- install
    - ` sudo apt update `
    - ` sudo apt install apache2 `
- basic site
    - /var/www/html/
        - index.html
        - address: [https://chi.kaist.ac.kr](<https://chi.kaist.ac.kr>)
        - move all the files to /var/www/html
- setting by editing virtual host file
    - /etc/apache2/sites-enabled/000-default.conf
    - redirect to …/sites\_available/000-default.conf
        - ServerName chi.kaist.ac.kr
        - ServerAdmin&#9;REDACTED_EMAIL
        - DucumentRoot&#9;/var/www/html
- activating virtualhost file
    - sudo a2ensite 000-default.conf
    - service apache2 reload

<br>

## CentOSRocky/Fedora

## Installation

### make bootable usb

- rufus for usb installer
    - [https://rufus.akeo.ie/](<https://rufus.akeo.ie/>)
    - MBR …
    - more in [windows.doc](<file:///C:\Users\jhPark\AppData\Roaming\Microsoft\Word\Windows_software.docx>)
- for dual booting system go to common linux structure

### check hardware

- main board: SuperMicro
- check harddisk data cable
    - sata data cable: a, b, c, d for dev/sda, sdb, sdc, sdd
    - after installation
        - connect data cable
        - mount in /etc/fstab
- RAM position of Motherboard
- for safety use sda only
    - disconnect data cable or power cable except sda
- CMOS check
    - harddisk recognition

### Installation

- region
    - select Seoul
- keyboard
- language support
    - English (United States)
- installation source
    - sdb1 is usb
- software selection
    - gnome desktop
- Device partition
    - before partition
        - centos default is xfs
            - try to use xfs for centos and ext4 for harddisk
            - do not modify fstab for default of xfs
    - select manual partition
        - /boot 1 GB&#9;&#9;xfs for CentOS
        - swap 10 GB
        - /home 190 GB&#9;# let the remaining storage become about 40 ~ 50 GB
        - /    (empty GB)
            - takes the remaining region for root, /
    - select device: sda
        - + for adding partition
        - - for removing partition
- network
    - local\_server.local\_domain==chi.kaist.ac.kr
    - Ethernet configure
        - IPv4 setting
            - ip, netmask, gateway, DNS servers
            - search domain: kaist.ac.kr
    - this will make a use of all the repository to install
        - e.g. X, GNOME Extension, all the commander
- during installation
    - ` make superuser passwd `
    - user id with authority
- reboot
    - do not unplug installation usb when rebooting
        - it makes an error
    - remove usb and reboot

### initial setup

- can be done in installation: set up nameserver
    - /etc/resolv.conf
- ` yum update (check network if fails) `
    - upgrade all the package installed
    - it is better for this to be done at early stage
    - if you update fails
        - ps -ef \| grep yum
            - pkill pid yum-update
- remove blocking for network
    - /etc/sysconfig/selinux
        - ` SELINUX=disabled `
- iptables to replace firewall
    - basic info
        - as for v. 7, firewall replaced iptables
        - firewalld generates iptables rule
    - to enable iptables instead of firewall
        - systemctl stop firewalld&#9;! stop firewall
        - systemctl mask firewalld&#9;! block reuse of firewall
        - ` yum install -y iptables-services `
        - systemctl enable iptables
        - systemctl start iptables
- network speedtest

### nvidia - CentOS

- contents
    - CUDA
- it might depend on the driver
    - download nvidia driver
        - [http://www.nvidia.com/object/unix.html](<http://www.nvidia.com/object/unix.html>) ==\> Latest Long Lived Branch version
            - linux X64 (AMD64/EM64T) Display Driver -\> download
    - depending on driver, the method might be different
        - the previous driver: deactivated nouveau by NVIDIA
- installing method 1
    - [https://www.advancedclustering.com/act\_kb/installing-nvidia-drivers-rhel-centos-7/](<https://www.advancedclustering.com/act_kb/installing-nvidia-drivers-rhel-centos-7/>)
    - prepare machine
        - ` yum -y update `
        - ` yum groupinstall "Development Tools" `
            - GNOME Desktop is already installed in OS installation
        - ` yum install kernel-devel epel-release dkms `
            - after installing epel, dkms is installed
    - reboot for the booting with the newest kernel
    - method to disable nouveau (possible in gnome)
        - edit grub
            - ` vi /etc/default/grub `
            - ` GRUN_CMDLINE_LINUX=”rd.driver.blacklist=nouveau nouveau.modeset=0” `
                - original=”crashkernel=auto rhgb quiet”
        - generate a new grub configuration to include above change
            - grub2-mkconfig -o /boot/grub2/grub.cfg
        - edit\|create /etc/modprobe.d/blacklist.conf and append
            - blacklist nouveau
        - backup the old initramfs and make a new one
            - ` mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r)-nouveau.img `
            - dracut /boot/initramfs-$(uname -r).img $(uname -r)
        - to reboot with text mode
            - systemctl set-default multi-user.target
        - reboot to text mode
    - install NVIDIA
        - sh NVIDIA…..run
        - yes to all question
        - systemctl set-default graphical.target
        - reboot
    - setting after installation
        - sudo nvidia-settings
- reinstall NVIDIA
    - just set
        - systemctl set-default multi-user.target
    - reboot
    - run NVIDIA driver
        - chmod
        - ./NVIDIA……run
            - will remove the previous driver
            - yes to all
    - systemctl set-default graphical.target
    - reboot
- skip: the others are for another case
    - install X if there is not (if it is, skip)
        - when OS is installed as text mode
            - server version doesn’t have X
        - ` yum groupinstall “X Window System” “GNOME Desktop” `
        - startx
        - if strange things happen
            - reboot
                - if not going to login on GUI
                    - systemctl get-default
                        - multi-user.target
                        - only with networking enabled with run level 3
                    - systemctl isolate graphical.target
                        - ` make us move to graphical target with run level 5 `
                    - systemctl set-default graphical.target
                        - whenever login, it goes to GUI
            - setting (?)
                - systemctl isolate multi-user.target
    - nvidia is not installed automatically
        - even though it is installed automatically, it is wrong
            - as for CentOS server
                - lspci \| grep VGA
    - nvidia will be installed again
        - in case: nvidia was installed in old kernel
            - uninstall nvidia and reinstall
    - reboot and let a latest kernel active
        - this is default in grub
        - cf kernel management
    - go to terminal mode
        - systemctl set-default multi-user.target
            - default will be text mode
        - reboot
            - should boot the desired kernel
            - shell prompt appear
        - ./NVIDIA-LINUX…..run
            - to run driver, change mode NVIDIA driver (.run) to 755
            - this can uninstall the pre-existing nvidia driver
            - nouveau will be automatically blacklisted
            - install w. or w/o dkms
                - w. dkms will take a little more time
                - w.o. dkms
        - systemctl set-default graphical.target
            - symlink /etc/system/system/default/target to /usr/lib/system/system/graphical.target
        - reboot
    - reinstall due to kernel upgrade
        - symptom
            - after kernel upgrade (yum update), driver is not working
            - the monitor is black out
        - system
            - if the nvidia driver is not automatically reinstalled, it will not work after kernel update
            - if you write dkms module in register, in case the kernel is updated, nvidia driver will be reinstalled automatically
        - install nvidia driver
            - find login window
                - alt+ctl+F6
            - login with root
            - step graphic driver
                - systemctl stop gdm&#9;&#9;! gdm3 is not working
                    - this stop graphic driver
                    - don’t need to reboot before install nvidia driver
            - come back to login window
                - alt+ctl+F6
            - find driver and uninstall installed nvidia-driver
                - ./NVIDIA-LINUX…..run –uninstall
                    - nvidia-xconfig --restore-original-backup -\> yes for backup
                    - Error: /usr/.../xorg/modules/extensions/libglx.so' is not a smbolic link
                        - can be skipped
            - install driver
                - ./NVIDIA-LINUX…..run
                    - with dkms&#9;! if error, install without dkms
                    - install nvidia 32-bit lib ? -\> yes
                    - making dkms module
            - reboot
    - further installation

### HiDPI – 4K monitor

- tweak top bar menu
    - Application/Accessories/Tweaks
- later
    - tweak in gnome-shell extension
        - tweak/window/scale
    - system setting
        - Settings\>Devices\>Displays\>Scale
            - only 100\|200\|300 %

### mount /dev

- mount hard disk using uuid
- as for new harddisk
    - gdisk for partition
    - mkfs for formatting
- change 1002 to joonho
    - manual change of file permission for files out of home or somewhere
        - #find / -group 1002 -exec chgrp -h joonho \{\} \\;
        - #find / -user 1002 -exec chown -h joonho \{\} \\;

### GNOME Shell integration

- login
    - GNOME Shell login&#9;← use this
        - after login nothing on desktop
    - GNOME Classic
- gnome version
    - rpm –qa \| grep gnome-shell
- install addon GNOME Shell integration
    - no package in CentOS 7
- it is through gnome-tweak-tool
    - ` yum install gnome-tweak-tool `
- tweak
    - Extensions
        - Frippery panel favorites on &#9;! favorites on top bar

### skip grub

- grub
    - /boot/grub2
    - if cursor doesn’t move in grub
        - use ps2 wire keyboard
    - Windows OS is already installed but
        - do not try about grub
    - straightforwad
        - debian
            - boot and mount windows system (simply open the disk on Nautilus)
            - ctl+alt+t, sudo os-prober
            - if Windows found
                - sudo update-grub
        - centOS
            - sudo fdisk –l
                - shows Windows
            - do not try to modify /boot
            - grub2-mkconfig –o /boot/grub2/grub.cfg
                - changes to setting
                - Windows 10 is recognized in grub

### manual fix in reboot

- software
    - environment module
        - shut down
            - .bashrc: unload all the module except “module load use.own”
        - boot
            - .bashrc&#9;&#9;&#9;&#9;&#9;cf. bash
                - ` module load use.own `

## Settings

### general

- position: Power icon/Setting icon//Settings
- items
    - Wi-Fi, Bluetooth
    - Background
    - Notification, Search
    - Region & Language, Universal Access
    - Online Accounts, Privacy, Sharing
    - Sound
    - Power
    - Network
    - Devices
    - Details

### Background

- Background & Lock Screen

### Universal Access

- Seeing
    - Cursor Size: select icon
        - mouse cursor size control

### sound

- master OS - CentOS
    - position: general setting
    - HDMI/Display port --- not tested
    - when you put in, this appears
        - audio round outlet - foreside
            - Headphones - Built-in Audio
        - usb
            - Digital Output (S/PDIF) - HyperX 7.1 Audio
            - Analog Output - HyperX 7.1 Audio
- Virtual Machine - windows 10
    - No options
        - Speaker(High Definition Audio)
        - Microphene(High …
- Mike test
    - check and turn on the switch on headset

### Details

- device name
- memory
- processor
- Graphics: GeForce GTX 1060
- Gnome
- os type: 64 bit
- disk : total 6.4 TB

### Power Saving

- Blank screen: never
- Automatic suspend off
- When the Power Button is pressed: suspend

### more basic settings

- centos version
    - cat /etc/centos-release
        - 7.6.1810
- error for graphical login
    - if other ID’s has no problem
        - use initial .bashrc and then find the collision application there
- blank screen (screen save, auto-lock)
    - set up in gsetting
    - suspend need to press power button again
- skip: do not use “stop CentOS 7”
    - in the status of GNOME screen lock
    - cf. stop icon in CentOS 7 (in status of log out)
        - stop everythings except power
            - cannot login from outside
        - power button is blinking
        - touch power button make it alive
- Home files in Desktop
    - have ~/Desktop
    - ` vi .config/user-dirs.dirs `
        - ` XDG_DESKTOP_DIR=”$HOME/Desktop `
        - log out and in again

### crontab

- 0 1 \* \* \* rsync -avz --delete /home/joonho/ /Data/Backhome/joonho
- 0 2 \* \* 0  rsync -avz --delete /Data/Backhome/joonho/ /Data/Backhome/joonho\_sunday
- 0 12 \* \* \* rsync -avz --delete /shared/share\_win/share\_Res2/share\_CO2\_red/QCsinglemol/Ni\_CO2red /scratch2/Rsync

## System Architecture & OS

### Linux OS

- OS is composed of underlying kernel and outermost shell
- sometimes both are separately treated as
    - OS
        - is referred to as underlying kernel
    - shell
        - is regarded as software, which handles the command line interface
        - operates like an application and can be replaced
        - requires users to know the syntax of a scripting language

### Architecture of kernel

- AMD: Advanced Micro Devices, Inc
- X86-64
    - also known as x64, AMD64, and Intel 64
    - 64-bit version of x86 set
- Ia64 vs AMD64 for zeon
    - https://www.linuxquestions.org/questions/debian-26/ia64-or-amd64-xeon-352008/
    - IA-64 ("ia64")
        - First officially released with Debian 3.0. This is a port to Intel's first 64-bit architecture.
        - Note: this should not be confused with the latest Intel 64-bit (EM64T)extensions for Pentium 4 and
        - Celeron processors, called EM64T
    - amd64
        - First officially released with Debian 4.0. Port to the 64 bit AMD64 processors. The goal is to
        - support both 32bit- and 64bit-userland on this architecture. This port supports AMD's 64-bit Opteron,
        - Athlon and Sempron processors, and Intel's processors with EM64T (64-bit) support, including
        - the Pentium D and various Xeon and Core2 series.
- how to know
    - uname –a
        - uname -r
    - /lib/modules
- kernel update
    - ` yum update `
- kernel management
    - default booting
        - the latest installed kernel is default
    - to change default kernel
        - boot in old (or present) kernel
        - ^@ F2
            - go to another shell mode log in
        - if new-kernel is not default
            - find kernel in /boot
                - initramfs-3.10.0-862.9.1.el7.x86\_64
            - ` yum reinstall new-kernel `
                - when rebooting, the reinstalled kernel will appear at first as default

## Booting

### booting process

- start
- system bios
- boot manager
- linux kernel
- Initd
- klogd, xinetd…  xfs

### basic start utility

- teamviewer
- dropbox
    - ./dropbox-dist/dropboxd &
- modprobe
    - su –
    - modprobe vboxdrv

### booting

- kernel is run
- run related initial script in / following login shell
- run initial files in $HOME
    - bash
        - .bashrc&#9;! .profile &#9;&#9;cf. shell
- dirty PATH during multiple running of .bashrc
    - unset PATH
    - if \[ -z “$PATH” \]; then
        - ` export PATH=”/usr/local/bin:/usr/bin:/bin” `

### boot error & login failure

- stop during boot (general)
    - if remote ssh is working
        - graphic card problem
    - if not
        - reinstall OS
            - reinstall kernel before OS-reinstall
- log in failure
    - fail to graphical login - bounced
        - check virtual environment such as anaconda in .bashrc
- after kernel update, Failed to start Crash recovery kernel arming
    - reinstall kernel
- after CUDA installation, reboot, Failed to start Crash recovery kernel arming
    - boot is stopped around process 12…..
    - when occurred?
        - after CUDA installation
        - reboot: don’t forget comment out all the virtual environment variables
            - after gui login, x-window became frantic
        - comment out anaconda, reboot
            - Failed to start Crash recovery kernel arming
            - stopped booting
    - 1<sup>st</sup>, kernel check
        - systemctl set-default multi-user.target
        - reboot
        - if login succeed, kernel would be right
    - 2<sup>nd</sup>, time to read /var/log/Xorg.n.log and /var/log/messages
        - for success login file
            - process number 5, 6, then goes to 70
        - for failed login file
            - 12…… NVIDIA
            - NVIDIA: Failed to initialize the NVIDIA kernel module, see system's the kernel log
            - no devices detected
            - Fetal server error:
            - no screens found
            - server terminated with error
    - install NVIDIA driver again
- error check
    - stop kdump if you are not expert
        - systemctl status kdump.service
        - kdump can be disabled
            - #systemctl disable kdump.service
    - kernel selection in grub2
    - /var/log/messages
        - is this same as journalctl
        - perf tool
            - perf: interrupt took too long
            - informational and nothing to worry about
            - kernel determines the sample rate
        - journal: g\_simple\_action\_set\_enabled: assertion ‘G\_IS\_SIMPLE\_ACTION (simple)’ failed
            - gnome desktop environment bug

### reinstall kernel

- kernel check&#9;&#9;&#9;&#9;cf. kernel management
    - rpm -qa \| grep kernel \| sort
- to install a kernel
    - boot with another kernel
    - it cannot remove the current kernel
- remove the latest kernel
    - ` yum remove kernel-3.10.0-957.21.3.el7.x86_64 `
        - it is removed with all the dependency
        - check /boot
- reinstall kernel
    - ` yum install kernel-3.10.0-957.21.3.el7.x86_64 `
- update kernel
    - dracut -f --kver KERNEL\_VERSION
    - kernel version
        - uname -r
        - /boot/initramfs-$\{kernel\_version\}.img

## Package Manager

### set sudoer (if not)

- install process
    - check authorization for user
- if not set up
    - edit /etc/sudoers file
    - not working
        - #usermod –aG wheel user
            - wheel group members have the authority of superuser

### RPM & YUM

- both are package manager applied to many linux except Debian and Ubuntu
- rpm: red hat package manager
    - it shows dependency hell
        - it shows many dependency and they are to be installed separately
- yum: yellow updater modified
    - ` yum is frontend which uses rpm `
    - ` yum installs all the dependent packages in advance before the installation of the target package `

### RPM

- whatitis
    - Red hat Package Manager
    - operation: install, uninstall, upgrade, query, verify
    - rpm package has name of “\*.rpm”
        - filename = packagename.versio.release.architecture
- find rpm package
    - red hat network
- options
    - -q, --query: query for info of pakcage
    - -U: upgrade
    - -F: fresh, applied to only existing file
    - -i, --install: install
    - -e, --erase: eliminate
    - -V, --verify:
    - --version
    - -?, --help
    - -v: detail info
- Install
    - rpm –ivh package\_name
        - if there are not dependent package, it fails. cf. YUM
        - url is possible
            - rpm -ivh http:// mirror.centos.org/centos/6/os/x86\_64/Packages/gzip-1.3.12-19.el6\_4.x86\_64.rpm
    - -Uvh package\_name
        - install upgraded version of package\_name than the existing package
    - --repalcepkgs
        - ignore error and reinstall package
        - when it is already installed,
            - package … is already installed
        - when it conflicts other package
    - unresolved dependency
        - error: failed dependencies: A is needed by B
            - suggested resolution: A…rpm
        - rpm –ivh B A…rpm
    - uninstall
        - rpm –ev foo-….rpm
            - -e: eliminate
        - dependency problem
            - --nodeps: ignore dependency
- query
    - whatitis
        - rpm database stores info for installed packages
            - /var/lib/rpm/
    - rpm –q packagename
        - shows
        - combined option
            - -a: all currently installed packages
                - usage: rpm -qa
                    - it is long list so: rpm -qa \| grep kernel
            - -f: when specifying a file, it shows the related package
            - -p: uninstalled package
            - -i: info
            - -l: list of files which belongs to the package
    - to check whether a certain package is installed
        - rpm –qa \| grep package\_name
    - rpm –qf filename
    - rpm –qi package\_name
    - rpm –qip filename.rpm
    - rpm –ql packagename

### Yum & dnf

- ` yum subcommand [package_nake] `
    - ` yum update	: update all the package to newest version `
    - if fails
        - ` yum clean all `
            - check repo setting error
                - url in /etc/yum.repos.d
        - ` yum update `
- install dnf
    - ` yum install dnf -y `
- update
    - ` yum list updates		! updated installed package `
    - ` yum update 		! update all the package `
    - ` yum update package `
        - also all the dependencies are updated
    - ` yum check-update `
        - shows update package among all the installed packages
- list
    - ` yum list		! list all the available package in t `
    - ` yum list mysql `
    - ` yum list mysql* `
    - ` yum list | grep mysql `
    - ` yum list installed `
    - ` yum list installed | grep kernel `
- search
    - ` yum search keyword `
        - when you don’t know the exact name
    - search for a specific package
        - ` yum list openssh `
- install
    - ` yum install *.rpm `
    - ` yum install firefox `
    - option –y shows yes for installation
        - ` yum –y install firefox `
    - error-related
        - missing environment variable
            - such as missing CURL\_LIBRARY CURL\_INCLUDE\_DIR
        - ` yum install curl libcurl libcurl-dev `
            - dev version is necessary
- remove
    - remove all the dependency also
    - ` yum remove firefox `
    - ` yum –y remove firefox `
    - package installed from rpm
        - ` yum remove packagename (excluding .rpm) `
- info
    - ` yum info package `
- related to group
    - grouplist
        - linux provides a bundle package which includes several packages which works together
        - ` yum grouplist `
            - present all the available package
    - ` yum groupinstall group-package-name `
        - when failed
        - try
            - ` yum groupinstall “Development Tools” --setopt=group_package_types=mandatory,default,optional `
    - ` yum groupupdate group-package-name `
    - ` yum groupremove group-package-name `
- repository
    - /etc/yum.repos.d/
        - adobe…&#9;for adobereader
        - CentOS
            - -Base
            - -CR
            - -Debuginfo
            - -fasttrack
            - -Media
            - -Sources
            - -Vault
        - cuda&#9;&#9;for cuda
        - epel
            - -testing
        - nux-dextop
        - teamviewer
        - virtualbox
    - ` yum repolist `
        - lists all the enabled repository
    - ` yum repolist all `
        - list all enabled and disabled repository
    - install repository
        - rpm
            - rpm -i …….rpm
    - remove repository
        - disable repo&#9;(cf. cuda)
            - edit repo file
                - enabled=0
- provide function
    - it gives the related package name w.r.t. a certain file
    - ` yum provide /etc/httpd/conf/httpd.conf `
- options
    - ` yum –y update `
        - yes

### error in installation

- common technique for installation
    - download
        - wget
        - git
    - install
        - make
        - cmake
            - ` make build directory `
            - ` cd to build directory `
            - ` cmake dir_of_CmakeLists.txt `
        - .run
        - .rpm
- Cmake cannot download
    - error in DOWNLOAD a dozen files
    - solution: using wget, manually download all the files in “cmake/projects.cmake”
        - then cmake recognize the existent file
- Cmake Error
    - message: the following variables are used but they are not found
        - e.g. GLUT\_XI\_LIBRARY
    - solution
        - find relative package name in web or yum search package\_name
        - install package
            - ` yum install package `

### libraries

- extension&#9;&#9;cf. library
    - .o: &#9;object file
        - gcc –c filename.c&#9;&#9;! –c : compile
            - filename.o
        - .out: executive file from gcc a.c –o (outfile) a.out
    - .a: an archive library containing many .o files
        - ls \*.o
            - a.o, b.o, c.o
        - ar q libmy.a \*.o
            - makes libmy.a
        - ar t libmy.a
            - a.o b.o c.o
    - .lo: library object when compiled with –fPIC
        - position independent object files
            - libtool compile command
            - -fPIC option
        - libtool compile gcc –c a.c
            - libtool: compile: gcc –c a.c –fPIC –DPIC –o ./libs/a.o &#9;! PIC code
            - libtool: compile: gcc –c a.c –o a.o \>/dev/null 2\>&1&#9;! non-PIC code
            - ls
                - a.lo, a.o
    - .so: shared object which contains PIC objects
- static executable
    - use .o and .a
- dynamic executable
    - bind with libraries at run time
    - use .lo and .so

### gcc upgrade

- source
    - [https://medium.com/@bipul.k.kuri/install-latest-gcc-on-centos-linux-release-7-6-a704a11d943d](<https://medium.com/@bipul.k.kuri/install-latest-gcc-on-centos-linux-release-7-6-a704a11d943d>)
- ` sudo yum -y update `
- ` sudo yum -y install bzip2 wget gcc gcc-c++ gmp-devel mpfr-devel libmpc-devel make `

## Install Package

### binary vs. source

- binary: download and install the already compiled package
- source: download source and install using yum

### GNU GPL, GTK, Qt

- GNU General Public License
    - such as linux kernel
- GTK
    - GIMP Toolkit
    - support X-window system, Gnome
    - coded by C, OOP widget
        - use Xlib to draw widget
    - not based on Xt
    - e.g. C code
        - #include \<gtk/gtk.h\>
    - gtk2 for
    - gtk3 for eclipse
- Qt

### tweak & firefox & terminal

- ` make icon and put into favorite ? `
    - gather icons
        - ~/.icons
    - Make a new icon for a command
        - Application/Accessory/Main Menu
            - E.g. go to Accessories
        - New Item
            - Command: e.g. rdesktop –g 1910x1100 143.248.247.238
            - Icon: click and change icon
        - New icon appears on the right column
        - Find icon in Application/Activities Overview/left column-bottom click
            - Find the icon move it to favorite, the left column
- terminal
    - font size
        - “ctrl” + “+/-“
    - color
        - Edit/Preferences/Colors
            - Palette
                - Built-in schemes: linux console

### printer

- Application \> Sundry \> printer setting
    - color printer was installed
        - driver works for Samsung CLP-680ND
    - install Samsung driver, uld
        - [https://www.samsungsvc.co.kr/online/faqList.do](<https://www.samsungsvc.co.kr/online/faqList.do>)
            - input model
            - get driver
                - ` tar xvzf ….zip.dz `
                - ` cd uld `
                - sh install.sh
        - error in duplex install
            - get right diver from above homepage
            - ` cd  ~/uld `
                - if already another version was installed
                    - ./uninstall.sh
                - ` ./install.sh `
    - Add \> Network Printer \> (ipp) Internet Printing Protocol
        - Network Printer shows drivers
            - if not, install Samsung driver of uld
                - find ip
                - connection: LPD network printer via DNS-SD
                - another option
                    - connection: IPP
                    - ipp://ip/ipp&#9;! ip is ip address
                        - ipp://143.248.37.188/ipp&#9;! for black
                    - option for driver
                        - search for a printer driver to download
                        - automatic detect
                        - provide PPD file&#9;! postscript printer description
                        - select printer from database
- using cups for black printer
    - the direct install fails
        - error: M38X driver can’t be used for M38X… printer
    - install cups
        - ` yum install cups-pdf `
        - systemctl start cups
        - systemctl enable cups
        - systemctl status cups
            - Applications/Sundry/Printer Setting shows Cups-PDF printer
    - configure cups to be accessible on LAN by editing /etc/cups/cupsd.conf
        - prepend following at the begging of the file
            - DefaultEncryption Never
        - append following next to ‘Listen’ directives to listen on additional IPs (non-loopback)
            - Listen \<lan-ip\>:631
                - Listen \<143.248.37.188\>:631
        - remove deny in the following to give access to others to cups print server
            - \<Location /\>
            - Order allow
        - remove deny in the following to give admin access to admin station IPs
            - \<Location /admin\>
            - Order allow
        - systemctl restart cups
    - Now cups can be accessed at [https://143.248.37.188:631/](<https://143.248.37.188:631/>)
        - what is this?
    - use URL to add printer on any linux machine over IPP
        - Printer Setting
            - add
            - URL
                - ipp://143.248.37.188/printers/cups-pdf
            - select driver
                - if M38X is not working
                    - select default of CX…
                        - test page is not correct
                - new printer app. was made
                - change driver of the printer
                    - Make and Model … change
                        - select M332x model driver
                        - test page
- printing error
    - everythings are OK but printing invokes error: check printer permission

### Teamviewer

### Virtual Box

- download from CentOS 7 repo
    - manual
        - [https://linuxize.com/post/how-to-install-virtualbox-on-centos-7/](<https://linuxize.com/post/how-to-install-virtualbox-on-centos-7/>)
        - ` sudo yum install kernel-devel kernel-headers make patch gcc `
        - ` sudo wget https://download.virtualbox.org/virtualbox/rpm/el/virtualbox.repo -P /etc/yum.repos.d `
    - using repo
        - ` make file of /etc/yum.repos.d/virtualbox.repo `
- install
    - install from repo
        - ` sudo yum install VirtualBox-5.2	cf. next 2nd extension pack `
            - y or enter during installation
    - upgrade from repo: remove and install
        - ` sudo yum remove VirtualBox-5.2 `
        - ` sudo yum install VirtualBox-6.0 `
        - cf. find version
            - ` yum list installed `
    - verify installation
        - systemctl status vboxdrv
            - output: enabled,
    - check version
        - menu/Help/About VirtualBox…
- additional package
    - install VB extension Pack for
        - download
            - [https://www.virtualbox.org/wiki/Downloads](<https://www.virtualbox.org/wiki/Downloads>)
                - VirtualBox version Oracle VM VirtualBox Extension Pack
                    - this supports any platform
                    - install by click the file in nautilus (file explorer)
                        - cf. 3<sup>rd</sup> Guest Edition
        - usb 2.0, 3.0 devices
        - RDP
        - images encryption
    - VB guest addition
        - e.g.
            - [https://www.smarthomebeginner.com/update-virtualbox-guest-additions-on-windows/](<https://www.smarthomebeginner.com/update-virtualbox-guest-additions-on-windows/>)
        - VM menu \> Devices \> Insert Guest Edition image
            - new CD appears in
                - D:\\ driver or later
                - install by click VBoxWindowsAddtions or -amd64
            - Note the guest addition is installed in GUEST OS, not HOST OS
            - after installation, reboot Guest OS and automatically windows is sized up
            - for VB version upgrade
                - D:\\, E:\\...
                - remove the previous version of Guest addition driver
        - if not working
            - install epel repository
                - sudo rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
            - ` yum install update `
            - ` yum install perl gcc dkms kernel-devel kernel-headers make bzips `
            - ls -l /usr/src/kernels/$(uname -r)
                - displays kernel headers
            - #export KERN\_DIR=/usr/src/kernels/$(uname -r)
- ` make VM `
    - making new VM
        - new OS
            - VM setting
    - read pre-existing VM
        - vmdk is generated through VM ware
- after OS installation
    - copy and paste test
        - Devices
            - Shared Clipboard
                - bidirectional
                - for copy and paste
            - Drag and Drop
                - bidirectional
    - software installation
        - menu:Devices/Optical Devices
            - IDE
                - Choose Disk Image…
                    - select iso file
                        - appear on new driver in Windows such as CD Drive (D:)
    - Install Hangul language pack in English Windows 10
        - setting/
            - region: Korea
            - Language: 한국어/Korean

### VB tips

- include disk permission
    - VM permission error
    - vigr group setting
        - vigr
            - add joonho in the line of disk
                - disk:x:6:joonho
        - vigr –s
            - shadow file of vigr
            - do the same thing
            - :wq!&#9;due to read-only property
        - reboot
        - check: groups shows disk
- usb error
    - install VM VB extension pack
        - for usb 2.0, 3.0 can be available
    - cannot make usb device
        - vigr group setting
        - add user name in to vboxuser group
            - #usermod –a –G vboxuser joonho
        - groups
            - joonho disk wheel(sudo) vboxusers
                - if not reboot
        - ` make usb device `
            - setting/USB/
                - enable USB 3.0
                - +: USB Optical Mouse
                    - if it does not work, make joonho group member of device, vboxusers
- mouse error
    - mouse is stuck during VM guest OS is running
        - check out menu:Device/USB/
            - uncheck Logitech USB receiver
- screen size is fixed
    - normally it is fixed up by insert Guest Addition
    - if not
        - lower VB version
            - v. 5.2 uses full screen even without installing Guest-Addition
- for more detail - skip this part
    - binary installation
        - [https://www.itzgeek.com/how-tos/linux/centos-how-tos/install-virtualbox-4-3-on-centos-7-rhel-7.html](<https://www.itzgeek.com/how-tos/linux/centos-how-tos/install-virtualbox-4-3-on-centos-7-rhel-7.html>)
        - setup epel repository if not
            - rpm –Uvh [https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm](<https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm>)
        - install header and dev tools if not
            - ` yum install kernel-devel kernel-headers dkms `
            - ` yum groupinstall “Development Tools” `
            - ` yum update `
        - Download oracle public key
            - ` wget http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc `
        - import oracle public key
            - rpm –-import oracle\_vbox.asc
        - download virtualbox repo file
            - ` wget http://download.virtualbox.org/virtualbox/rpm/el/virtualbox.repo -o /etc/yum.repos.d/virtualbox.repo `
        - install virtualbox v5.2
            - ` yum install VirtualBox-5.2 `
        - rebuild kernel
            - service vboxdrv setup
                - if this is not working
                    - /usr/lib/virtualbox/vboxdrv.sh setup
                        - not in /etc/init.d/
        - start virtualbox
            - virtualbox
        - VM VB Extension Pack
            - install
                - download
            - VM menu \> File \> Preferences \> Extensions \>
                - + add:

### VM Windows 10

- after windows update, the size of window became smaller
    - try full screen \[View/Host+F\] and back
- rsync
    - requires bash command system
        - Git Bash: useful
        - cygwin
- Git Bash &#9;: backup for VM Windows
    - (not necessary) install Git for Windows
        - C:/Program Files/Git
            - or /Program Files (x86)/Git
    - rsync
        - [https://superuser.com/questions/701141/how-to-add-more-commands-to-git-bash/1381448#1381448](<https://superuser.com/questions/701141/how-to-add-more-commands-to-git-bash/1381448>)
            - download rsync from futureware.at
            - extract to anywhere
                - such as C:/rsync…
                - download WinZip for freeware
                    - Winzip in windows 10 doesn’t work
            - just use rsync
                - ` make .bashrc at home (cd ~) `
                    - ` export PATH=”/c/rsync/usr/bin/”:$PATH `
                - ` which rsync `
                    - /c/rsync/usr/bin/rsync
    - run
        - ./rsync\_win.sh
        - ` rsync error `
            - when .bashrc puts output
                - protocol incompatibility
                    - use -zz for compression
            - it is not clean shell
                - protocol version mismatch -- is your shell clean?
                - NB. do not activate anaconda in server
- how to use rsync
    - rsync\_at\_local.sh
        - ` rsync -avzz --delete /c/WinData/Res_Chem/ $remote_dir/WinData/Res_Chem `
        - remote\_dir=[joonho@chi.kaist.ac.kr:/Shared\_win/shared\_win/Windows10\_backup](<mailto:joonho@chi.kaist.ac.kr:/Shared_win/shared_win/Windows10_backup>)
    - ` rsync from to `
        - C:/WinData/Res\_Chem  &#9;$remote\_dir/WinData/Res\_Chem
        - My\_Computer/Documents &#9;$remote\_dir/WinData/my\_docu
        - My\_Computer/Pictures&#9;$remote\_dir/WinData/my\_pic
    - sundry
        - ssh-keygen for remote login without asking passwd
- Cygwin (not using now)

### dropbox (not now)

- web
    - https://www.dropbox.com/install-linux
- install in usermode
    - ` wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf - `
        - ` which makes `
            - ~/Dropbox
            - ~/.dropbox-dist
- run daemon whenever you login
    - ~/.dropbox-dist/dropboxd
- running the daemon from your own account
    - run /bin/lib/dropbox.py
    - now (?)
        - /etc/init.d/dropbox
            - /home/joonho/bin/lib/dropbox.py

### add repo & multimedia

- default repository
    - base: centos.
    - extras:
    - updates: mirror
- install epel repository
    - epel: mirror.ho
- setup multimedia on CentOS 7
    - nux-dextop depends on epel
    - install nux-dextop repository
        - ` yum -y install http://li.nux.ro/download/nux/dextop/el7/x86_64/nux-dextop-release-0-5.el7.nux.noarch.rpm `
    - install adobe repo
        - ` yum -y install http://linuxdownload.adobe.com/adobe-release/adobe-release-x86_64-1.0-1.noarch.rpm `
    - install the desired packages
        - ` yum install flash-plugin `
        - ` yum install icedtea-web `
        - ` yum install vlc smplayer ffmpeg HandBrake-{gui,cli} `
            - installs 4 packages with 58 dependency
        - ` yum install libdvdcss gstreamer{,1}-plugins-ugly gstreamer-plugins-bad-nonfree gstreamer1-plugins-bad-freeworld `
            - installs 10 packages
- smplayer (not necessary)
    - follow the multimedia installation
    - previous fails
        - ` apt-get install smplayer `
        - it just movie player
        - Error
            - you could try using –skip-broken to work around the problem
            - you could try running: rpm –Va –nofiles --nodigest
    - install mplayer
        - ` yum install yum-priorities mplayer mplayer-gui `
        - if not searched in yum repository
            - /etc/yum.repos.d/dag.repo
            - \[dag\]
            - name=DAG RPM Repository
            - baseurl=http://apt.sw.be/Redhat/el$releasever/en/$basearch/dag
            - gpgcheck=1
            - enabled=1
        - then
            - ` yum install libdvdcss libdvdplay libdvdnav lsdvd `

### mendeley

- download source
- ` tar xvf `
- execution
    - sudo ./bin/mendeleydesktop
        - write in /
- update
    - automatic
    - manual
        - ` apt-get update `
        - ` apt-get install mendeleydesktop `

### evince: pdf reader

- default in linux
- acroread (Foxit viewer – pdf reader)
    - ` wget http://ardownload.adobe.com/pub/adobe/reader/unix/9.x/9.5.5/enu/AdbeRdr9.5.5-1_i486linux_enu.rpm `
    - in Fedora (works for centos also)
        - rpm -Uvh --nodeps AdbeRdr9.5.5-1\_i486linux\_enu.rpm
        - ` wget -O /opt/Adobe/Reader9/Reader/intellinux/lib/libidn.so.11 https://www.if-not-true-then-false.com/dl/libidn.so.11.6.18 `
        - ` dnf install AdbeRdr9.5.5-1_i486linux_enu.rpm `
        - ` dnf install libcanberra-gtk2.i686 adwaita-gtk2-theme.i686 PackageKit-gtk3-module.i686 `
            - if not
                - Canberra, adwaita error makes the acroread closed
    - CentOS 7.6
        - ` yum localinstall http://li.nux.ro/download/nux/dextop/el7/x86_64/nux-dextop-release-0-5.el7.nux.noarch.rpm `
        - ` yum localinstall AdbeRdr9.5.5-1_i486linux_enu.rpm libcanberra-gtk2.i686 adwaita-gtk2-theme.i686 PackageKit-gtk3-module.i686 `

### image viewers

- Vokoscreen (not needed)
    - download binary
    - install
        - ` yum install voko… `

### movie

### gifsicle/gifview

- install
    - ` yum install gifsicle `
    - ` yum install gifview `
- ` yum makes collision `
    - anaconda3 make collision with yum for python
- usage
    - gifsicle  pic.gif … \> animation.gif
    - gifsicle --delay=10 --loop \*.gif \> anim.gif
    - options
        - --delay
- run gif animation
    - gifview animation.gif

### zoom

- install
    - download rpm
        - zoom\_x86\_64.rpm
    - ` yum install zoom_x86_64.rpm `
    - run
        - ` $ zoom or Application/Internet `
- test audio and video
    - $zoom
    - sign in
        - [로그인 정보 삭제]
        - [로그인 정보 삭제]
    - click New Meeting
    - test audio and video
        - select speaker as HyperX
        - select Microphone as HyperX
- ` make zoom Meeting `
    - for 1 to 3 above
    - select use machine audio and video
        - speaker: toggle for turn on/off
        - Stop Video: toggle for turn on/off
    - top-right icon
        - Meeting ID: can be used for others to join the Meeting with Passcode
            - copy the Passcode to guest
        - Invite Link
            - click “Copy Link” then paste
        - setting icon
            - can select speaker/Mic when required

### Avogadro 1.0 & openbabel

- if you have home
    - ` yum install openbabel `
        - makes avo work
    - MD is not working

### environmental modules

- gettext&#9;&#9;&#9;&#9;&#9;&#9;cf. centos
    - autopoint is a program in gettext package
    - [https://centos.pkgs.org/5/centos-x86\_64/gettext-0.17-1.el5.x86\_64.rpm.html](<https://centos.pkgs.org/5/centos-x86_64/gettext-0.17-1.el5.x86_64.rpm.html>)

### Visual Packages: vmd, jmol, molden, iqmol, vesta, p4vasp,

- vmd
    - vmd 1.9.4
        - download
            - [로그인 정보 삭제]
            - [로그인 정보 삭제]
        - modify configure
            - install at home
                - install\_bin\_dir=/home/joonho/.local/bin
                - install\_library\_dir=/home/joonho/.local/lib/$install\_name(=vmd)
        - ` ./configure LINUXAMD64 `
        - ` cd src `
        - ` make install `
- Jmol
    - install
        - gunzip Jmol-14.4.1\_2015.12.15-binary.tar.gz
        - ` tar xvf Jmol-14.4.1_2015.12.15-binary.tar `
        - ` cd jmol-14.4.1_2015.12.15 `
        - ./jmol.sh
    - link in /home/$USER/bin
        - ` ln –s $home_dir/jmol $USER/bin/jmol `
        - ` ln –s $home_dir/Jmol.jar	$USER/bin/Jmol.jar `
    - [how to use](<file:///C:\Users\root\AppData\Roaming\Microsoft\Word\visual_program.docx>)
- molden (gmolden error)
    - web
        - [http://www.cmbi.ru.nl/molden](<http://www.cmbi.ru.nl/molden>) \> how to get a copy of Molden
    - install
        - register ?
        - ftp [ftp.cmbi.umcn.nl](<ftp://ftp.cmbi.umcn.nl>)
            - user anonymous email
            - ` cd pub/molgraph/molden `
            - binary&#9;&#9;! change to binary mode
            - passive&#9;&#9;! change to passive mode
            - get molden5.8.tar.gz
            - quit
        - gunzip molden5.8.tar.gz
        - ` tar –xvf `
        - ` cd mol.. `
            - make
                - gmolden error
        - makefile
            - ` LIBS = -L/usr/X11R6/lib64 -lX11 –lm `
                - there is no directory of /usr/X11R6, but it runs with many warnings
        - make
            - show many warnings
            - makes molden, gmolden
        - install commander,
            - sudo install -t /usr/local/bin -m 755 molden gmolden
    - [how to use](<file:///C:\Users\root\AppData\Roaming\Microsoft\Word\visual_program.docx>)
- IQmol
    - download .rpm
        - [http://iqmol.org/downloads.html](<http://iqmol.org/downloads.html>)
    - ` sudo yum –nogpgcheck localinstall iqmol..centos….rpm `
        - installed at /usr/bin/iqmol
    - [how to use](<file:///C:\Users\root\AppData\Roaming\Microsoft\Word\visual_program.docx>)
- vesta (not)
    - download x86\_64
        - http://jp-minerals.org/vesta/en/download.html
            - cf. i686 is for 32 bit
    - “bzip2 –d” followed by tar xvf
    - it is run w.o. installation
    - error in new OS
        - libpng12.so.o is missing
    - to use vesta, go to [visual\_program.doc](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\visual_program.docx>)

### Graphic Package: modu, inkscape

- grace (xmgrace)
- inkscape
    - ` sudo yum install inkscape `
    - such as adobe illustrator
    - SVG: scalable vector graphics
    - W3C

### Science Package: anaconda, Q-Chem, VASP, LAMMPS, PACKMOL, Java-eclipse, intelij, QE, CP2K

- anaconda in Linux Common packages
    - python package under anaconda (ASE, AMP, TF, etc)
- Intel, Q-Chem  -- done up to here
- VASP ([gnu](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\vasp.docx>), [intel](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\vasp_qe.docx>))
    - web for gnu:
        - [http://www.ivofilot.nl/posts/view/28/How+to+build+VASP+5.3.5+using+the+ GNU +compiler+on+Linux+Ubuntu+14.04+LTS#step1](<http://www.ivofilot.nl/posts/view/28/How+to+build+VASP+5.3.5+using+the+%20GNU%20+compiler+on+Linux+Ubuntu+14.04+LTS>)
        - install vasp 5.3.5 using gnu complier on linux Ubuntu 14.04 lts
            - for Ubuntu 14, Debian 8
        - for intel go to [vasp.doc](<file:///C:\WinData\Res_EEWS\Docs\vasp.docx>)
    - 4 steps cf. [vasp.doc](<file:///C:\Users\root\AppData\Roaming\Microsoft\Word\vasp.docx>)
        - installing the necessary packages
        - install OpenMPI
            - building OpenBLAS
            - building ScaLAPACK
            - building VASP
                - [modify makefile](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\vasp_qe.docx>)
    - run
        - console
            - ` mpirun np -4 /home/joonho/bins/vasp & `
    - can run without license but can’t publish without license
- LAMMPS
- quantum espresso
    - install
        - ` aptitude install quantum-espresso `
        - download & install
- cp2k
    - ` aptitude search cp2k `
    - ` aptitude install cp2k `
    - site: https://www.cp2k.org/download
        - svn checkout http://svn.code.sf.net/p/cp2k/code/trunk cp2k
- packmol
    - whatitis
        - ` make box and fill it with molecules `
    - [http://m3g.iqm.unicamp.br/packmol/home.shtml](<http://m3g.iqm.unicamp.br/packmol/home.shtml>)

### PHP & SQL

- [https://blog.lael.be/post/1721](<https://blog.lael.be/post/1721>)
- install PHP
    - ` yum install PHP `
    - ` yum install php-gd	# for image treat `
    - ` yum install php-mbstring	# for foreign language `
    - ` yum search php-		# for more modules `
- MySQL
    - ` yum install mariadb `
    - ` yum install mariadb-server `
    - service mariadb start
    - /usr/bin/mysql\_secure\_installation
        - root passwd will be made for mysql
        - all the others are \[enter\]
    - ` yum install php-mysql	# correlation modules between php and mysql `
    - basic language set
        - ` vi /etc/my.cnf `
            - character-set-server = utf8mb4
            - collation-server = utf8mb4\_unicode\_ci
    - service mariadb restart

### Matlab

- requirement
    - login [https://kr.mathworks.com](<https://kr.mathworks.com>)
        - [로그인 정보 삭제]
        - [로그인 정보 삭제]
    - click association
    - input activation key
        - to get license file and key
    - download linux version
- installation
    - online installation
        - ` ./install `
        - install window
            - install with login id in mathworks: internet connection is required
                - download and install takes time
        - activation
            - input mathworks id and passwd
    - download license file and personal activation key
        - ` ./install with license file `
            - install done
        - activation before using
            - activation key is required
    - execution file = matlab
        - /usr/local/bin/matlab

### skype

- install
    - su –
    - ` apt-get update; apt-get upgrade `
    - downloading
        - ` wget -c http://download.skype.com/linux/skype-debian_4.3.0.37-1_i386.deb `
    - dpkg –i skype-debian\_4.3.0.37-1\_i386.deb
        - install fails
            - errors were encountered
        - need to install any required 32-bit packages
    - dpkg –add-architecture i386
    - ` apt-get update `
    - install again
        - dpkg –i skype-debian\_4.3.0.37-1\_i386.deb
            - error again
    - let the installer fix the dependencies by automatically installing any missing packages
        - ` apt-get –f install `

### bazaar

- a distributed version control system
- install
    - ` aptitude search bzr `
    - ` apt-get install bzr `
- user id
    - register id
        - bzr whoami “Joonho Park \<email\>”
    - id check
        - bzr whoami
- starting a new project
- Adding files
- Making changes to your files
- Viewing the revision log
- Publishing your branch on Lanchpad
- Creating your own copy of another branch
    - to work with someone else’s code, copy of their branch
    - e.g. Bazaar’s GTK interface
        - bzr init-repo ~/bzr-gtk
        - bzr branch lp:~bzr/bzr-gtk/trunk ~/bzr-gtk/john
    - e.g. thinkcspy
        - bzr init-repo bzr
        - ` cd bzr `
        - bzr branch lp:thinkcspy
- Updating your branch from the main branch

### hwp viewer, jaxodraw

- hwp viewer
    - web: [http://www.hancom.com/cs\_center/csDownload.do](<http://www.hancom.com/cs_center/csDownload.do>)
    - download: Linux(Fedora)-64 bit
    - sudo rpm -i han…rpm
    - icon appears Application/Office
    - open
        - hwp files are open automatically
        - change default program
- jaxodraw
    - for drawing like chemdraw
    - only linux versions are available

### backup/ crontab rsync ssh

- back up home directory using crontab
    - ` which crontab `
    - crontab –e
        - 0 12 \* \* \* rsync –avz –delete /home/joonho/  &#9;/Data/Backhome/joonho
    - for remote server, make key
        - ssh-copy-id –I ~/.ssh/id\_rsa.pub chi.kaist.ac.kr
            - answer passwd
        - then you can login without passwd
        - ` rsync –avz –e ssh /qcfs/joonho/bin	joonho@chi.kaist.ac.kr:/Data/BUkaist `
- back up to external hd
    - mount error for external hard in ntfs
        - ` yum install epel-release -y `
        - ` yum install ntfs-3g -y `

### rdesktop, remmina, realvnc

- remote login
    - properties
        - to use KVM vs rlogin
    - remmina is for debian
- remmina
    - property
        - best one
        - only for debian
    - install
        - ` apt-get remmina `
            - icon is automatically generated in Internet
    - direct connect
        - RDP
        - Put in IP and Connect
        - Open preferences dialog
            - RDP
                - Quality option: Best (slowest)
    - Save connection
        - New
        - Profile
            - Name: office window
            - Protocol: Remote Desktop Protocol
        - Basic
            - Server: ip
            - Username: id
            - Password: skip
            - Domain: kaist.ac.kr
            - Resulution
                - Fit to monitor
                - larger value shows larger Host window
            - Color: true color 24 or 32
        - Advanced
            - Quality: Best(slowest)
                - Shows Host wallpaper and mouse cursor properly
    - For host, adjust [windows 10](<file:///C:\Users\joonho\AppData\Roaming\Microsoft\Word\Window_Machine.docx>) performance
    - there are issues for cerius through mobaXterm
- Realvnc
    - install
        - guest
            - Download realvnc for debian of x64
            - ` tar x `
            - dpkg –I VNC-Viewer…deb
        - install and run realvnc server in host
    - not tested yet
- rdesktop
    - install
        - ` apt-get install rdesktop `
    - run
        - rdesktop –g size ip
            - e.g.: rdesktop –g 1910x1100 143.248.247.238
            - defect: wallpaper doesnot com
        - rdesktop –x I –g 1910x1100 143.248.247.238
            - wallpaper appears
            - defect: mouse cursor is not shown

### Material Studio

- History for background
    - Disk manage
        - Gdisk /dev/sdb
        - Fdis /dev/sdb
    - Mount
        - Fdisk /dev
        - ` cp –dpR /home/* /mnt `
        - Reboot
        - Dconf
        - Yum install dconf-editor
        - Dconf-editor
        - Yum install jre
        - Yum install jdk
        - Yum install java
        - Yum install jre.i386
        - Yum install openjdk
        - Yum install jre.i686
            - …. I386,    ….i586,
- Yum install java-1.7.0-openjdk-1.7.0.792.5.5.2.el7\_1.i686
    - …..i386
        - …..x86
            - …..i586
            - …..x86\_64
        - Yum install glibc.i686
        - Yum install compat-libstdc++-33
        - Yum install Redhat-lsb
        - ` ./install `
            - Rm –rf /opt/accelrys/\*
                - In case of “collision of files”

### Material Studio

- In CentOS as user
- ` ./install `
- Before install make /opt/accelrys as root authority
- Change ownership to joonho
- Chown –R joonho accelrys
- Then install as joonho
- Copy licence file from Window
- Licence file in Window and CentOS should be same
- For copy using editor, use gedit
- gedit /opt/accelrys/LicensePack/Licenses/MS60.lic
- /opt/accelrys/ is the install directory when you see during ./install
- ps -ef \| grep http
- you will see gateway during ./install
- gateway is for finding guest, CentOS is server and Window is guest
- rpm -qa \| grep hpmpi
- In window
- Run setup
- Include gateway during install
- Copy lic\_file\_included/MS60 install\_directory
- C:/Program Files (x86)/Accelrys/License pack/Licences

### OpenChemistry – Avogadro 2.0 (not now)

- prerequisite
    - C/C++, OpenGL, Qt 5.6, Cmake 3.3, python
        - python
            - use 2.7
            - python3 makes problem in using yum
        - opengl
            - ` yum install freeglut-devel `
        - qt5.9
            - ` yum install qt5-qtbase-devel `
        - ` cmake (cf. install using cmake) `
            - ` wget http://www.cmake.org/files/v3.6/cmake-3.6.1.tar.gz `
            - cd
            - ` ./bootstrap `
            - gmake&#9;&#9;! rather than make
            - ` sudo gmake install	! rather than make install `
                - makes error at this stage
                - ` which cmake `
                - /usr/local/bin/cmake
                - ` cmake –version `
                - Could not find CMAKE\_ROOT…
            - ` sudo cp ./bin/cmake, cpack, ctest /bin `
                - ` cmake –version `
                    - ` cmake version 3.6.1 `
                    - Cmake suite maintained and supported by Kitware (kitware.com/cmake)
        - Libxml2
            - ` yum install libxml2 libxml2-devel `
        - libXmu, libXmu-dev, libXi, libXi-devel
- openchemistry
    - git
        - ` git clone --recursive git://github.com/OpenChemistry/openchemistry.git `
        - cd
        - ` git pull `
        - ` git submodule update –init `
    - build out of source
        - during the install
            - install some packages
                - libXmu libXmu-devel libXi libXi-devel
            - download all the external files manually using wget
        - ` mkdir openchem-build `
        - cd
        - ` cmake ../openchemistry `
        - ` cmake –build . (–config Release for windows) `
    - not complete installation
        - atom manipulation
            - selecting – deleting is not working
            - no “online-database”
- fails in installing avogadro
    - run rpm
        - ` yum install avo..2…rpm `
            - GUI is not properly installed: many functions are deprecated
    - two files of lib and main
        - pre-requisite
            - eigen3
                - ` yum search eigen3 `
                - ` yum install eigen3-dev eigen3-doc `
            - spglib (no SPGLIB)
                - download spglib-1.9.7.tar.gz
                - ` cd spg… `
                - ` ./configure `
                - make
        - down lib and app files
            - ` cd lib `
            - ` mkdir build `
            - ` cd build `
            - ` cmake ../ `
                - error
                    - no Eigen3
                    - spglib

### relion

- surface image caring program
- install
    - ` git clone https://github.com/3dem/relion.git `
        - made dir of relion
    - ` cd relion `
    - ` git pull `
        - update in command line
    - ` mkdir build `
    - ` cd build `
    - ` cmake .. `
    - ` make –j <N> `
        - N is number of process, == 1
    - ` sudo make install `
- usage
    - go to upper directory of mrc files
    - $relion
