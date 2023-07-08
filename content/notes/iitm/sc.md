+++
title = "System Commands"
author = ["John Doe"]
draft = false
toc = true
math = true
+++

## Introduction {#introduction}

| Directory | Contains                                      |
|-----------|-----------------------------------------------|
| /bin      | Essential command binaries                    |
| /boot     | Static files of the boot loader               |
| /dev      | Device files                                  |
| /etc      | Host specific system configuration            |
| /lib      | Essential shared libraries and kernel modules |
| /media    | Mount points for removable devices            |
| /mnt      | Mount Points                                  |
| /opt      | Add on application software packages          |
| /run      | Data relevant to running processes            |
| /sbin     | Essential system binaries                     |
| /srv      | Data for services                             |
| /tmp      | Temporary files                               |
| /usr      | Secondary hierarchy                           |
| /var      | Variable data                                 |


### /usr hierarchy {#usr-hierarchy}

| Directory    | Contains                            |
|--------------|-------------------------------------|
| /usr/bin     | User Commands                       |
| /usr/lib     | Libraries                           |
| /usr/local   | Local hierarchy                     |
| /usr/sbin    | Non-vital system binaries           |
| /usr/share   | Architecture dependent data         |
| /usr/include | Header files included by C programs |
| /usr/src     | Source Code                         |


### /var hierarchy {#var-hierarchy}

| Directory  | Contains                                  |
|------------|-------------------------------------------|
| /var/cache | Application cache data                    |
| /var/lib   | Variable state information                |
| /var/local | Variable data for /usr/local              |
| /var/lock  | Lock files                                |
| /var/log   | Log files and directories                 |
| /var/run   | Data relevant to running processes        |
| /var/tump  | Temporary files preserved between reboots |


## Simple Commands in linux {#simple-commands-in-linux}

-   **date** command <br/>
    
    Shows current date and timestamps. <br/>
    ```bash
    date
    ```
    
    ```text
    Saturday 08 July 2023 08:32:20 PM IST
    ```

-   **free** command <br/>
    
    Shows current free memory(ram) in the system. <br/>
    ```bash
    free
    ```
    
    ```text
    shared  buff/cache   available
    Mem:        16281300     4997972     8266492       77048     3433292    11283328
    Swap:       15136764           0    15136764
    ```

<!--listend-->

-   **groups** command <br/>
    
    Shows groups to which user belong. <br/>
    ```bash
    groups
    ```
    
    ```text
    nivaspvs cdrom floppy audio dip video plugdev netdev bluetooth lpadmin scanner
    ```

