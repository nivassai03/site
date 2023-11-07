+++
title = "Simple Linux Commands"
author = ["John Doe"]
draft = false
toc = true
math = true
+++

## Simple Commands in linux {#simple-commands-in-linux}

-   **date** command <br/>
    
    Shows current date and timestamps. <br/>
    ```bash
    date
    ```
    
    ```text
    Monday 06 November 2023 07:55:08 AM IST
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
    Mem:            15Gi       5.5Gi       5.7Gi       136Mi       4.8Gi        10Gi
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
    total 12
    -rw-r--r-- 1 nivaspvs nivaspvs 3975 Nov  6 07:36 sc.org
    -rw-r--r-- 1 nivaspvs nivaspvs 1936 Nov  6 07:55 simple_linux_commands.org
    drwxr-xr-x 3 nivaspvs nivaspvs 4096 Nov  5 16:48 static
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

<!--listend-->

-   **chmod** command <br/>

-   **file** command <br/>

