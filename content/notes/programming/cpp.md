+++
title = "Cpp"
author = ["John Doe"]
draft = false
toc = true
math = true
+++

## Preprocessor {#preprocessor}


### Translational Unit {#translational-unit}

When the processing of code file is completed by the preprocessor, the result is called **translational unit**. <br/>

-   Translational units contain source code we write as well as the processed code from #include files. <br/>

-   The translational unit is what compiled by the compiler. <br/>

<!--listend-->

```cpp
// add.h
int add(int x, int y)
```

```cpp
// add.cpp
#include "add.h"

int add(int x,int y){
    return x+y;
}
```

In the above code blocks we have two files one contain function delcaration(add.h) and other contain function definitions(add.c).This two files make one translational unit.we compile it in the following way. <br/>

```bash
g++ -c add.cpp
```

```cpp
// main.cpp

#include <iostream>

int main(int argc, char *argv[]) {
    int x = 10;
    int y = 20;
    std::cout << "Addition of x and y: " << add(x,y);
    return 0;
}

```


## Variables {#variables}

Variables provide us with name storage spaces that our programs can maipulate. <br/>


### Declaration {#declaration}

**Declaration** makes name known to the program. <br/>


### Definition {#definition}

**Definition** creates the associated entry. <br/>


### Initialization {#initialization}


### Linkage {#linkage}

An Identifier's linkage determines whether other declarations of that name refer to the same object or not. <br/>

There are two types of linkages <br/>

-   Internal Linkage <br/>
-   External Linkage <br/>


#### Internal Linkage {#internal-linkage}

An identifier of internal linkage can be seen and used with in a single [translational unit](#translational-unit) but it is not accessible from other translational units.(not exposed to linker.) <br/>


#### External Linkage {#external-linkage}

An identifier of external linkage can be seen and used both from the file in which it is defined, and from the other code files.(using forward declaration) <br/>


### Storage duration {#storage-duration}


### Local variables {#local-variables}

-   local variables have block scope. <br/>
-   local variables have automatic [storage duration](#storage-duration). <br/>
-   local variables have no linkage.(each declaraion referes to unique object.) <br/>


### Global variables. {#global-variables-dot}

-   By default non-const global variables have [external linkage](#external-linkage). <br/>
-   Global variables with [internal linkage](#internal-linkage) are sometimes called **internal variables**. <br/>
-   To make non-const global variables internal use **static** keyword. <br/>
-   **const** and **constexpr** global varibles have internal linkage by default. <br/>

