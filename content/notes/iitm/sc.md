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
    Wednesday 26 July 2023 08:54:32 PM IST
    ```

-   **free** command <br/>
    
    Shows current free memory(ram) in the system. <br/>
    
    flags: <br/>
    -h for human readable for format <br/>
    ```bash
    free -h
    ```
    
    ```text
    total        used        free      shared  buff/cache   available
    Mem:            15Gi       7.5Gi       4.8Gi       262Mi       3.7Gi       8.0Gi
    Swap:           14Gi          0B        14Gi
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

-   **ls** command <br/>
    List the files in the directory. <br/>
    ```bash
    ls -l
    ```
    
    ```text
    total 4
    -rw-r--r-- 1 nivaspvs nivaspvs 30 Jul 11 09:53 sample.txt
    ```
    
    -   **flags**: <br/>
        -l  :   long list format <br/>
        
        {{< figure src="/img/_20230726_203540screenshot.png" >}} <br/>
        
        | Symbol | File type      |
        |--------|----------------|
        | -      | Regular file   |
        | d      | Directory      |
        | l      | Symbolic link  |
        | c      | Character file |
        | b      | Block file     |
        | s      | Socket file    |
        | p      | Named pipe     |
    -   **Permission String** <br/>
        ![](/img/_20230726_204614screenshot.png) <br/>
    
    -   **inode** <br/>
        
        An entry in the filesystem table about the location in storage media. <br/>
        
        command: <br/>
        ls -i &lt;name&gt; <br/>
        ```bash
        ls -i sample.txt
        ```
        
        ```text
        14811390 sample.txt
        ```

<!--listend-->

-   **file** command <br/>

