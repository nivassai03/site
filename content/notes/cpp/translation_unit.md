+++
title = "Translation Unit"
author = ["John Doe"]
draft = false
toc = true
math = true
+++

## Translational Unit {#translational-unit}

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

