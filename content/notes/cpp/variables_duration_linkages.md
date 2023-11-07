+++
title = "Variables Duration And Linkages"
author = ["John Doe"]
draft = false
toc = true
math = true
+++

## Variables {#variables}

Variables provide us with name storage spaces that our programs can maipulate. <br/>


### Declaration {#declaration}

**Declaration** makes name known to the program. <br/>


### Definition {#definition}

**Definition** creates the associated entry. <br/>


### Initialization {#initialization}


### Local variables {#local-variables}

-   local variables have block scope. <br/>
-   local variables have automatic [storage duration](#storage-duration). <br/>
-   local variables have no linkage.(each declaraion referes to unique object.) <br/>


### Global variables. {#global-variables-dot}

-   By default non-const global variables have [external linkage](#external-linkage). <br/>
-   Global variables with [internal linkage](#internal-linkage) are sometimes called **internal variables**. <br/>
-   To make non-const global variables internal use **static** keyword. <br/>
-   **const** and **constexpr** global varibles have internal linkage by default. <br/>


### Top Level and Low Level Constants {#top-level-and-low-level-constants}

-   **Top level** constant indicates that an object itself is const. <br/>
-   Top level constant can appear in any object type.(arithmetic types,class types,pointer type) <br/>
-   When an object can point to a const object that const is refered as **low level** constant. <br/>
-   Low-level const appears int the base type of compound types such as pointers and references. <br/>
    ```cpp
    int i = 10;
    int *const a = &i;        // we cannot change value of a const is toplevel.
    const int b = 42;         // we cannot change b const is toplevel.
    const int *c = &b;        // we can change b const is low-level(c point to const int).
    const int &r = b;         // const in references is always low-level.
    const int *const e = c;   // right most const is top level, left most is not.
    ```


## Linkage {#linkage}

An Identifier's linkage determines whether other declarations of that name refer to the same object or not. <br/>

There are two types of linkages <br/>

-   Internal Linkage <br/>
-   External Linkage <br/>


### Internal Linkage {#internal-linkage}

An identifier of internal linkage can be seen and used with in a single [translational unit]({{< relref "translation_unit" >}}) but it is not accessible from other translational units.(not exposed to linker.) <br/>


### External Linkage {#external-linkage}

An identifier of external linkage can be seen and used both from the file in which it is defined, and from the other code files.(using forward declaration) <br/>


## Storage duration {#storage-duration}

