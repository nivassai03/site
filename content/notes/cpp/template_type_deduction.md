+++
title = "Template Type Deduction"
author = ["John Doe"]
draft = false
toc = true
math = true
+++

## Template Type Deduction {#template-type-deduction}

Lets say we have template of the form follwing. <br/>

```cpp
template<typename T>
void func(pa_type param);

func(expr);
```

During compilation compilers will deduce type for T and pa_type (different types). <br/>

Template type deduction can be divided into three cases for the above. <br/>

1.  if **pa_type** is of reference or pointer. <br/>
2.  if **pa_type** is of universal reference; <br/>
3.  **pa_type** is of neither pointer or reference. <br/>


## pa_type is a Reference or Pointer. {#pa-type-is-a-reference-or-pointer-dot}


### Reference {#reference}

```cpp
template<typename T>
void func(T& param);

func(expr);
```

-   if expr is of reference type remove the reference part. <br/>
-   pattern match the expr type with pa_type to get type of T. <br/>

Lets say we have the following variables and their respective function calls. <br/>

```cpp
int v = 10;
const int cv = v;
const int& crv = v;

func(v);    // expr type is int

func(cv);   // expr type is const int

func(crv);  // expr type is const int&
```

The deduced type of T and pa_type will be the following. <br/>

```cpp
func(v)       - T will be of type int.
              - pa_type will be of type int&.

func(cv)      - T will be of type const int.
              - pa_type will be of type const int&.

func(crv)     - T will be of type const int.
              - pa_type will be of type const int&.
```

-   Passing const object to template taking a T&amp; is safe as const becomes part of type deduced for T. <br/>


### Const Reference {#const-reference}

Suppose we change pa_type from T&amp; to const T&amp;. <br/>

```cpp
template<typename T>
void func(const T& param);

func(expr);
```

For the above considered variables v,cv,crv the deduced type of T and pa_type will be the following. <br/>

```cpp
func(v)       - T will be of type int.
              - pa_type will be of type const int&.

func(cv)      - T will be of type int.
              - pa_type will be of type const int&.

func(crv)     - T will be of type int.
              - pa_type will be of type const int&.
```

-   Because pa_type is of const here, there is no need for T to be deduced as const. <br/>

Things are essentially similar if pa_type is pointer. <br/>

```cpp
template<typename T>
void func(T* param);

func(expr);
```

```cpp
int v = 10;
const int* cpv = v;

func(v);    // expr type is int

func(cpv);  // expr type is const int*
```

The deduced type of T and pa_type will be the following. <br/>

```cpp
func(&v)      - T will be of type int.
              - pa_type will be of type int*.

func(crv)     - T will be of type const int.
              - pa_type will be of type const int*.
```


## pa_type is a Universal Reference {#pa-type-is-a-universal-reference}

```cpp
template<typename T>
void func(T&& param);

func(expr);
```

Type deduction for universal reference works in following ways. <br/>

1.  if expr is an **lvalue**,both T and pa_type are deduced as lvalue references.(only situation in template type deduction where T is deduced to be reference). <br/>
2.  if expr is an **rvalue** type deduction works similar to above case.(pa_type being reference). <br/>

<!--listend-->

```cpp
int v = 10;
const int cv = v;
const int& crv = v;

func(v);    // v is lvalue

func(cv);   // cv is lvalue

func(crv);  // crv is lvalue reference

func(100);  // expr type is rvalue
```

The deduced type of T and pa_type will be the following. <br/>

```cpp
func(v)       - T will be of type int&.
              - pa_type will be of type int&.

func(cv)      - T will be of type const int&.
              - pa_type will be of type const int&.

func(crv)     - T will be of type const int&.
              - pa_type will be of type const int&.

func(100)     - T will be of type int.
              - pa_type will be of type int&&.
```

we can think of these in the following ways <br/>

-   Universal reference gives a best possible reference according to the type you provide. <br/>
-   A lvalue and a lvalue reference can only be bound to lvalue reference.So for lvalues it gives lvalue reference. <br/>
-   A rvalue and a rvalue reference can only be bound to rvalue reference.So for rvalues it gives rvalue reference. <br/>


### Collapsing Rules {#collapsing-rules}

Below are the collapsing rules in c++. <br/>

```nil
 Type&  &   becomes  Type&
 Type&  &&  becomes  Type&
 Type&& &   becomes  Type&
 Type&& &&  becomes  Type&&
```

Above type deduction works as follows using collapsing rules. <br/>

| expr is: | T is:               | pa_type is:                                    |
|----------|---------------------|------------------------------------------------|
| lvalue   | int&amp;(v)         | int&amp; &amp;&amp;       =&gt; int&amp;       |
| lvalue   | const int&amp;(crv) | const int&amp; &amp;&amp; =&gt; const int&amp; |
| rvalue   | int(100)            | int&amp;&amp;         =&gt; int&amp;&amp;      |


## pa_type is Neither a Pointer nor Universal Reference {#pa-type-is-neither-a-pointer-nor-universal-reference}

```cpp
template<typename T>
void func(T param);

func(expr);
```

In the above code we are dealing with pass by value.That means param will be a copy of object passed. <br/>

Type deduction for pass by value work in following ways. <br/>

1.  if expr type is a reference , ignore the reference part. <br/>
2.  if after ignoring reference part,expr is const or volatile ignore both. <br/>

<!--listend-->

```cpp
int v = 10;
const int cv = v;
const int& crv = v;

func(v);    // expr type is int

func(cv);   // expr type is const int

func(crv);  // expr type is const int&
```

The deduced type of T and pa_type will be the following. <br/>

```cpp
func(v)       - T will be of type int.
              - pa_type will be of type int.

func(cv)      - T will be of type int.
              - pa_type will be of type int.

func(crv)     - T will be of type int.
              - pa_type will be of type int.
```

-   As param is a copy, it is independent of v,cv,crv.So it doesn't matter whether they are const or non-const we can do anything with the copy. <br/>


### Const Pointer to Const Object {#const-pointer-to-const-object}

```cpp
const char* const ptr = "Pointer";

```

if the expression is of type const pointer to const object the deduction will work as follows. <br/>

```cpp
func(ptr)     - T will be of type int.
              - pa_type will be of type const *.
```

-   The const to the left of \* says that we can't modify what pointer is pointing to through this pointer. <br/>
-   The const to the right of \* says that we can't reassign the pointer. <br/>
-   ptr will be passed by value. According to type deduction rules for by value parameters , the constness of ptr will be ignored. <br/>
-   But the constness of what the pointer points to is preserved. <br/>


## Examining Compiler Deduced Types. {#examining-compiler-deduced-types-dot}

we can see the type deduced by the compiler using type_index of boost library. <br/>


### Case 1: Reference Type or Pointer {#case-1-reference-type-or-pointer}

```cpp
#include <iostream>
#include <boost/type_index.hpp>
using std::cout;
using boost::typeindex::type_id_with_cvr;

// param type is reference or Pointer
template<typename T>
void func(T& param){
    cout << "T type: " << type_id_with_cvr<T>().pretty_name() << "\n";
    cout << "Param type: " << type_id_with_cvr<decltype(param)>().pretty_name() << "\n";
}


int main(){
    int x = 10;
    const int cx = x;
    const int& crx = cx;
    const int* cpx = &x;
    const int* const cpcx = &x;
    std::cout <<"expr type: "  << type_id_with_cvr<decltype(x)>().pretty_name() << "\n";
    func(x);
    std::cout << "---------\n";
    std::cout <<"expr type: " <<  type_id_with_cvr<decltype(cx)>().pretty_name() << "\n";
    func(cx);
    std::cout << "---------\n";
    std::cout <<"expr type: " << type_id_with_cvr<decltype(crx)>().pretty_name() << "\n";
    func(crx);
    std::cout << "---------\n";
    std::cout <<"expr type: " << type_id_with_cvr<decltype(cpx)>().pretty_name() << "\n";
    func(cpx);
    std::cout << "---------\n";
    std::cout <<"expr type: " << type_id_with_cvr<decltype(cpcx)>().pretty_name() << "\n";
    func(cpcx);
}
```

```cpp
// ouput
expr type: int
T type: int
Param type: int&
---------
expr type: int const
T type: int const
Param type: int const&
---------
expr type: int const&
T type: int const
Param type: int const&
---------
expr type: int const*
T type: int const*
Param type: int const*&
---------
expr type: int const* const
T type: int const* const
Param type: int const* const&
```


### Case 2: Universal Reference {#case-2-universal-reference}

```cpp
#include <iostream>
#include <boost/type_index.hpp>

using std::cout;
using boost::typeindex::type_id_with_cvr;

 std::string dummyString(){
    return "Hello";
}

template<typename T>
void funcU(T&& param){
    cout << "T type: " << type_id_with_cvr<T>().pretty_name() << "\n";
    cout << "Param type: " << type_id_with_cvr<decltype(param)>().pretty_name() << "\n";
}

int main(){
    int x = 10;
    const int cx = x;
    const int& crx = cx;
    const int* cpx = &x;
    const int* const cpcx = &x;
    std::cout <<"expr type: "  << type_id_with_cvr<decltype(x)>().pretty_name() << "\n";
    funcU(x);
    std::cout << "---------\n";
    std::cout <<"expr type: " <<  type_id_with_cvr<decltype(cx)>().pretty_name() << "\n";
    funcU(cx);
    std::cout << "---------\n";
    std::cout <<"expr type: " << type_id_with_cvr<decltype(crx)>().pretty_name() << "\n";
    funcU(crx);
    std::cout << "---------\n";
    std::cout <<"expr type: " << type_id_with_cvr<decltype(cpx)>().pretty_name() << "\n";
    funcU(cpx);
    std::cout << "---------\n";
    std::cout <<"expr type: " << type_id_with_cvr<decltype(23)>().pretty_name() << "\n";
    funcU(23);
    std::cout << "---------\n";
    std::cout <<"expr type: " << type_id_with_cvr<decltype(dummyString())>().pretty_name() << "\n";
    funcU(dummyString());
    std::cout << "---------\n";
    std::cout <<"expr type: " << type_id_with_cvr<decltype(cpcx)>().pretty_name() << "\n";
    funcU(cpcx);
    std::cout <<"expr type: " << type_id_with_cvr<decltype(dummyString())>().pretty_name() << "\n";
}
```

```cpp
// output

expr type: int
T type: int&
Param type: int&
---------
expr type: int const
T type: int const&
Param type: int const&
---------
expr type: int const&
T type: int const&
Param type: int const&
---------
expr type: int const*
T type: int const*&
Param type: int const*&
---------
expr type: int
T type: int
Param type: int&&
---------
expr type: std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >
T type: std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >
Param type: std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&&
---------
expr type: int const* const
T type: int const* const&
Param type: int const* const&

```


### Case 3: Niether Pointer or Reference {#case-3-niether-pointer-or-reference}

```cpp
#include <iostream>
#include <boost/type_index.hpp>

using std::cout;
using boost::typeindex::type_id_with_cvr;

std::string dummyString(){
    return "Hello";
}
template<typename T>
void funcV(T param){
    cout << "T type: " << type_id_with_cvr<T>().pretty_name() << "\n";
    cout << "Param type: " << type_id_with_cvr<decltype(param)>().pretty_name() << "\n";
}

int main(){
    int x = 10;
    const int cx = x;
    const int& crx = cx;
    const int* cpx = &x;
    const int* const cpcx = &x;
    std::cout <<"expr type: "  << type_id_with_cvr<decltype(x)>().pretty_name() << "\n";
    funcV(x);
    std::cout << "---------\n";
    std::cout <<"expr type: " <<  type_id_with_cvr<decltype(cx)>().pretty_name() << "\n";
    funcV(cx);
    std::cout << "---------\n";
    std::cout <<"expr type: " << type_id_with_cvr<decltype(crx)>().pretty_name() << "\n";
    funcV(crx);
    std::cout << "---------\n";
    std::cout <<"expr type: " << type_id_with_cvr<decltype(cpx)>().pretty_name() << "\n";
    funcV(cpx);
    std::cout << "---------\n";
    std::cout <<"expr type: " << type_id_with_cvr<decltype(cpcx)>().pretty_name() << "\n";
    funcV(cpcx);

}

```

```cpp
// output

expr type: int
T type: int
Param type: int
---------
expr type: int const
T type: int
Param type: int
---------
expr type: int const&
T type: int
Param type: int
---------
expr type: int const*
T type: int const*
Param type: int const*
---------
expr type: int const* const
T type: int const*
Param type: int const*
```

