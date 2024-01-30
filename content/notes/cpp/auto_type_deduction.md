+++
title = "Auto Type Deduction"
author = ["John Doe"]
draft = false
toc = true
math = true
+++

## Auto Type Deduction {#auto-type-deduction}

**Auto type deduction is essentially template type deduction (with one exception).** <br/>

Lets map auto type deduction to template type deduction.We have template of the form follwing. <br/>

```cpp
template<typename T>
void func(pa_type param);

func(expr);
```

-   Compilers using expr type deduce T and pa_type.When a variable is declared auto, **auto acts as T** in template and the **type speicifier acts as pa_type**. <br/>

<!--listend-->

```cpp
auto v = 100;              // type specifier is auto
const auto cv = v;         // type specifier is const auto
const auto& crv = v;       // type sepcifier is const auto&
```

Similar to template type deduction , auto type deduction can be divided into 3 cases. <br/>


## Type specifier is a Pointer or Reference. {#type-specifier-is-a-pointer-or-reference-dot}

```cpp
int v = 100
const auto& crv = v;       // v is of type int
```

The deduced auto type will be of following. <br/>

```cpp
auto is deduced to int(T) and type specifier is const auto&(pa_type)
```


## Type specifier is a Universal Reference. {#type-specifier-is-a-universal-reference-dot}

```cpp
int v = 100;
const int cv = v;


auto&& urv = v;           // v is int and lvalue.

auto&& urcv = cv;         // cv is const int and rvalue.

auto&& urrv = 30;         // 30 is int and rvalue.
```

The deduced auto types will be of following. <br/>

```cpp
urv       - is of type int&.

urcv      - is of type const int&.

urrv      - is of type int&&
```


## Type specifier is Niether Pointer Nor a Reference. {#type-specifier-is-niether-pointer-nor-a-reference-dot}

```cpp
auto v = 100;              // type specifier is auto

const auto cv = v;         // type specifier is const auto
```

The deduced auto types will be of following. <br/>

```cpp
v         - is of type int.

cv        - is of type const int.
```


## Examining Compiler Deduced Types. {#examining-compiler-deduced-types-dot}

Similary to template type deduction we can see the types deduced by the compiler using type_index of boost library. <br/>


### Case 1: Reference Type or Pointer {#case-1-reference-type-or-pointer}

```cpp
#include <iostream>
#include <boost/type_index.hpp>

using std::cout;
using boost::typeindex::type_id_with_cvr;

int main(){

    int v = 100;
    auto& rv = v;
    const auto& crv = v;
    const auto* cpv = &v;
    cout << "v type: " << type_id_with_cvr<decltype(v)>().pretty_name() << "\n";
    cout << "rv type: " << type_id_with_cvr<decltype(rv)>().pretty_name() << "\n";
    cout << "crv type: " << type_id_with_cvr<decltype(crv)>().pretty_name() << "\n";
    cout << "cpv type: " << type_id_with_cvr<decltype(cpv)>().pretty_name() << "\n";
}
```

```cpp
// output
v type: int
rv type: int&
crv type: int const&
cpv type: int const*
```


### Case 2: Universal Reference {#case-2-universal-reference}

```cpp
#include <iostream>
#include <boost/type_index.hpp>

using std::cout;
using boost::typeindex::type_id_with_cvr;

int main(){

    int v = 100;
    const int cv = v;

    auto&& urv = v;
    auto&& urcv = cv;
    auto&& urrv = 30;

    cout << "v type: " << type_id_with_cvr<decltype(v)>().pretty_name() << "\n";
    cout << "cv type: " << type_id_with_cvr<decltype(cv)>().pretty_name() << "\n";
    cout << "urv type: " << type_id_with_cvr<decltype(urv)>().pretty_name() << "\n";
    cout << "urcv type: " << type_id_with_cvr<decltype(urcv)>().pretty_name() << "\n";
    cout << "urrv type: " << type_id_with_cvr<decltype(urrv)>().pretty_name() << "\n";
}
```

```cpp
v type: int
cv type: int const
urv type: int&
urcv type: int const&
urrv type: int&&
```


### Case 3: Niether Pointer or Reference {#case-3-niether-pointer-or-reference}

```cpp
#include <iostream>
#include <boost/type_index.hpp>

using std::cout;
using boost::typeindex::type_id_with_cvr;

int main(){

    auto v = 100;
    const auto cv = v;

    cout << "v type: " << type_id_with_cvr<decltype(v)>().pretty_name() << "\n";
    cout << "cv type: " << type_id_with_cvr<decltype(cv)>().pretty_name() << "\n";
}

```

```cpp
v type: int
cv type: int const
```


## Difference from template type deduction {#difference-from-template-type-deduction}

-   auto deduces initializer in enclose braces as std::initializer_list. If it can deduce initializer_list type code will be rejected. <br/>
-   There are two type of type deduction happening here one for auto variable and another one for T of std::initializer_list&lt;T&gt;. <br/>

<!--listend-->

```cpp
auto v = 10;     - type is int.

auto u{10};      - type is int.

auto t = {27};   - type is std::initializer_list<int>

auto x{27};      - same as above

```

```cpp
auto s = {1,2,3.0}   - can't deduce T for std::initializer_list<T>.
```

```cpp
using std::cout;
using boost::typeindex::type_id_with_cvr;

int main(){

    auto v = {1};

    cout << "v type: " << type_id_with_cvr<decltype(v)>().pretty_name() << "\n";

}
```

```cpp
v type: std::initializer_list<int>
```


## Auto function return type {#auto-function-return-type}

-   C++14 permits auto as function return types.And also lambdas can use auto in paramerter declarations. <br/>
-   However in case of function return types **auto employs template type deduction,not auto type declaration.** <br/>
-   So function that returns initializer_list and have auto return type won't compile. <br/>

