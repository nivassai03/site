+++
title = "Variables"
author = ["John Doe"]
draft = false
toc = true
math = true
+++

## Variables and Constants {#variables-and-constants}


### Enumerated Types {#enumerated-types}

Sometimes a varible should only hold restricted set of values. <br/>

ex: clothes has sizes small,Medium,Large,Extra Large. <br/>

An **enumerated type** has finite number of named values. <br/>

```java
enum size { SMALL , MEDIUM , LARGE , EXTRA_LARGE };

// declare varible of this type

Size s = Size.SMALL;
```

A variable of enumerated type can hold one of the values listed int the type declaration or null. <br/>

