+++
title = "Programming Data Structures and algorithms"
author = ["John Doe"]
draft = false
weight = 1
toc = true
math = true
+++

## Analysis of Algorithms {#analysis-of-algorithms}


### Measuring Performance: {#measuring-performance}


### Input Size: {#input-size}


### Addition sum function {#addition-sum-function}


## Search {#search}


### Binary Search {#binary-search}


## Sorting {#sorting}

**Sorting** a list makes other computations easier. <br/>
ex: Binary Search, Finding Median, Checking for Duplicates, Building Frequency Tables of Values. <br/>


### Selection sort {#selection-sort}

-   Select the smallest element and swap it with the first element. <br/>
-   Select the next smallest element and swap it with the second element. <br/>
-   Repeat until the entire list is sorted. <br/>


#### Implementation {#implementation}

```python
def selectionSort(L):
    n = len(L)
    if n < 1:
        return L
    for i in range(n):
        mpos = i
        for j in range(i+1,n):
            if(L[j] < L[mpos]):
                mpos = j
        (L[i],L[mpos]) = (L[mpos],L[i])
    return L

```


#### Testing It Out {#testing-it-out}

```python
L1 = [12,1,43,32,23,3,42,14]
L2 = [3]
L3 = [1,3,5,6,9,13]
L4 = [23,15,13,9,7,3,1]

print(selectionSort(L1))
print(selectionSort(L2))
print(selectionSort(L3))
print(selectionSort(L4))
```

```text
[1, 3, 12, 14, 23, 32, 42, 43]
[3]
[1, 3, 5, 6, 9, 13]
[1, 3, 7, 9, 13, 15, 23]
```


#### Analysis of selection sort {#analysis-of-selection-sort}

-   Correctness follows from the invariant. <br/>
-   Efficiency: <br/>
    -   Outer loop iterates \\(n\\) times <br/>
    -   Inner loop \\(n-i\\) steps to find minimum <br/>
    -   \\(\displaystyle T( n) \ =\ n+n-1+\dotsc +1\\) <br/>
    -   \\(\displaystyle T( n) \ =\ \frac{n( n+1)}{2}\\) <br/>
-   Running time is insensitive to input. <br/>

<!--listend-->

-   \\(\displaystyle \boxed{\boldsymbol{Time\ Complexity} :\ O\left( n^{2}\right)}\\) <br/>


### Insertion sort {#insertion-sort}


#### Implementation (iterative) {#implementation--iterative}

```python
def insertionSort(L):
    n = len(L)
    if n < 1:
        return L
    for i in range(n):
        j=i
        while(j>0 and L[j]<L[j-1]):
            (L[j],L[j-1]) = (L[j-1],L[j])
            j = j-1
    return L
```


#### Testing It Out {#testing-it-out}

```python
L1 = [12,1,43,32,23,3,42,14]
L2 = [3]
L3 = [1,3,5,6,9,13]
L4 = [23,15,13,9,7,3,1]

print(insertionSort(L1))
print(insertionSort(L2))
print(insertionSort(L3))
print(insertionSort(L4))
```

```text
[1, 3, 12, 14, 23, 32, 42, 43]
[3]
[1, 3, 5, 6, 9, 13]
[1, 3, 7, 9, 13, 15, 23]
```


#### Implementation (recursive) {#implementation--recursive}

```python
def Insert(L,v):
    n = len(L)
    if n==0:
        return ([v])
    if v >= L[-1]:
        return (L+[v])
    else:
        return Insert(L[:-1],v)+L[-1:]

def Isort(L):
    n = len(L)
    if n < 1:
        return L
    L = Insert(Isort(L[:-1]),L[-1])
    return L
```


#### Testing It Out {#testing-it-out}

```python
L1 = [12,1,43,32,23,3,42,14]
L2 = [3]
L3 = [1,3,5,6,9,13]
L4 = [23,15,13,9,7,3,1]

print(Isort(L1))
print(Isort(L2))
print(Isort(L3))
print(Isort(L4))
```

```text
[1, 3, 12, 14, 23, 32, 42, 43]
[3]
[1, 3, 5, 6, 9, 13]
[1, 3, 7, 9, 13, 15, 23]
```


#### Analysis of insertion sort (iterative) {#analysis-of-insertion-sort--iterative}

-   Correctness follows from the invariant <br/>
-   Efficiency: <br/>
    -   Outer loop iterates \\(n\\) times <br/>
    -   Inner loop \\(i\\) steps to insert \\(L[i]\\) in \\(L[:i]\\) <br/>
    -   \\(\displaystyle T( n) \ =\ 0+1+\dotsc +(n-1)\\) <br/>
    -   \\(\displaystyle T( n) \ =\ \frac{n( n-1)}{2}\\) <br/>

-   \\(\displaystyle \boxed{\boldsymbol{Time\ Complexity} :\ O\left( n^{2}\right)}\\) <br/>


#### Analysis of insertion sort (recursive) {#analysis-of-insertion-sort--recursive}

-   For input size \\(n\\) <br/>
    -   \\(TI(n)\\) is time taken by **Insert** <br/>
    -   \\(TS(n)\\) is time taken by **Isort** <br/>
-   Time for Insert <br/>
    -   \\(TI(0)=1\\) <br/>
    -   \\(TI(n)=TI(n-1)+1\\) <br/>
    -   by unwinding we get \\(TI(n)=n\\) <br/>
-   Time for ISort <br/>
    -   \\(TS(0)=1\\) <br/>
    -   \\(TS(n)=TS(n-1)+TI(n-1)\\) <br/>
    -   by unwinding we get \\(1+2+\dotsc +n-1\\) <br/>

<!--listend-->

-   \\(\displaystyle \boxed{\boldsymbol{Time\ Complexity} :\ O\left( n^{2}\right)}\\) <br/>


### Merge sort {#merge-sort}

-   Divide the list into two halves and seperately sort the left and right halfes. <br/>
-   Combine the two sorted halfes to get a fully sorted list. <br/>
-   Combining two sorted lists A &amp; B to C: <br/>
    -   Compare first elements of A and B. <br/>
    -   Move the smaller of the two to C. <br/>
    -   If A is empty move B to C. <br/>
    -   If B is empty move A to C. <br/>
    -   Repeat till you exhaust A &amp; B. <br/>
-   Merge sort uses **Divide and Conquer** to sort a list. <br/>


#### Implementation {#implementation}

```python
def merge(A,B):
    (m,n) = (len(A),len(B))
    (C,i,j,k) = ([],0,0,0)
    while k < m+n:
        if i == m:
            C.extend(B[j:])
            k = k+(n-j)
        elif j == n:
            C.extend(A[i:])
            k = k+(m-i)
        elif A[i] < B[j]:
            C.append(A[i])
            i,k = (i+1,k+1)
        else:
            C.append(B[j])
            j,k = (j+1,k+1)
    return C

def mergeSort(A):
    n = len(A)
    if n <= 1:
        return A
    L = mergeSort(A[:n//2])
    R = mergeSort(A[n//2:])

    B = merge(L,R)
    return B
```


#### Testing It Out {#testing-it-out}

```python
L1 = [12,1,43,32,23,3,42,14]
L2 = [3]
L3 = [1,3,5,6,9,13]
L4 = [23,15,13,9,7,3,1]

print(mergeSort(L1))
print(mergeSort(L2))
print(mergeSort(L3))
print(mergeSort(L4))
```

```text
[1, 3, 12, 14, 23, 32, 42, 43]
[3]
[1, 3, 5, 6, 9, 13]
[1, 3, 7, 9, 13, 15, 23]
```


#### Analysis of merge function {#analysis-of-merge-function}

-   Merge **A** of length \\(m\\) and **B** of length \\(n\\).Ouput list **C** has length \\(m+n\\). <br/>
-   In each iteration we add atleast one element to **C**. <br/>
-   Hence merge take time \\(O(m+n)\\). <br/>
-   we know that \\(\displaystyle m+n\leqslant \ 2( max( m,n))\\). <br/>
-   if \\(\displaystyle m\approx n\\) merge takes time \\(O(n)\\). <br/>


#### Analysis of merge sort {#analysis-of-merge-sort}

-   Let \\(\displaystyle T( n)\\) be the time taken for input size \\(\displaystyle n\\). <br/>

-   \\(\displaystyle T( 0) \ =\ T( 1) \ =1\\) <br/>
    
    \\(\begin{aligned}
            T( n) \  & =\ 2T( n/2) +n\\\\
            & =\ 2[ 2T( n/4) +n/2] +n\ =\ 2^{2} T\left( n/2^{2}\right) +2n\\\\
            & =\ 2^{2}\left[ 2T\left( n/2^{3}\right) +n/2^{3}\right] +2n\ =\ 2^{3} T\left( n/2^{3}\right) +3n\\\\
            & \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \vdots \\\\
            & =\ \ 2^{k} T\left( n/2^{k}\right) +kn
            \end{aligned}\\) <br/>

-   When \\(\displaystyle k\ =\log n,T\left( n/2^{k}\right) \ =\ T( 1) \ =\ 1\\) <br/>

-   \\(\displaystyle T( n) \ =\ 2^{\log n} T( 1) +(\log n) n=n+n\ \log n\\) <br/>

-   \\(\displaystyle \boxed{\boldsymbol{Time\ Complexity} :\ O( n\ \log n)}\\) <br/>


### Quick Sort {#quick-sort}

-   Select a pivot element (Generally first element of list). <br/>
-   Partition the list into lower and upper parts with respect to pivot. <br/>
    -   Scan the list from left to right. <br/>
    -   Assume the list is divided into four segments: **pivot**, **lower**, **upper**, **unclassified**. <br/>
    -   Examine the first unclassified element. <br/>
        -   if it is larger than the pivot extend upper segment to include this element. <br/>
        -   if it is smaller than the pivot, exchange with first element in upper.This extends lower and shifts upper by one position. <br/>
-   Move the pivot in between the lower and upper partitions. <br/>
-   Recursively sort the lower and upper half. <br/>


#### Short Commings of Merge Sort {#short-commings-of-merge-sort}

-   A additional list needs to be created while holding the merged elements. <br/>
    -   No obivious way of merging. <br/>
    -   Extra Storage can be costly. <br/>
-   Inherently recursive <br/>
    -   Recursive calls and return are expensive. <br/>


#### Implementation {#implementation}

```python
# Sort L[l:r]
def quickSort(L,l,r):
    if (r-l <= 1):
        return

    # Set pivot to first element and upper and lower segments markers to second element.
    (pivot,lower,upper) = (L[l],l+1,l+1)

    for i in range(l+1,r):
        if L[i] > pivot:
            # Extend Upper Segment
            upper = upper + 1

        else:
            # Exchange L[i] with start of upper segment
            (L[i],L[lower]) = (L[lower],L[i])

            # Shift both segments
            (lower,upper) = (lower+1,upper+1)

    # Move pivot between lower and upper
    (L[l],L[lower-1]) = (L[lower-1],L[l])
    lower = lower-1

    # Recursive Calls
    quickSort(L,l,lower)
    quickSort(L,lower+1,upper)
    return L

```


#### Testing It Out {#testing-it-out}

```python
# Unsorted Lists
L1 = [80, 45, 65, 12, 83, 51, 38, 90, 92, 36]
L2 = [32, 70, 42, 78, 23, 37, 4, 26, 11, 16]
L3 = [76, 17, 90, 89, 82, 35, 91, 6, 23, 5]
L4 = [11, 55, 78, 92, 20, 79, 84, 49, 4, 87]
L5 = [78, 56, 45, 87, 90, 30, 93, 73, 7, 11]

# Length of Lists
l1 = len(L1)
l2 = len(L2)
l3 = len(L3)
l4 = len(L4)
l5 = len(L5)

# Calling Quick Sort
print(quickSort(L1,0,l1))
print(quickSort(L2,0,l2))
print(quickSort(L3,0,l3))
print(quickSort(L4,0,l4))
print(quickSort(L5,0,l5))
```

```text
[12, 36, 38, 45, 51, 65, 80, 83, 90, 92]
[4, 11, 16, 23, 26, 32, 37, 42, 70, 78]
[5, 6, 17, 23, 35, 76, 82, 89, 90, 91]
[4, 11, 20, 49, 55, 78, 79, 84, 87, 92]
[7, 11, 30, 45, 56, 73, 78, 87, 90, 93]
```


#### Analysis of Quick Sort {#analysis-of-quick-sort}

-   Partitioning with respect to pivot takes \\(O(n)\\). <br/>

<!--listend-->

-   If the pivot is the median. <br/>
    -   \\(\displaystyle T( n) =2T( n/2) +n\\)\\( \\) <br/>
    -   \\(\displaystyle T( n) \ =\ O( n\ \log n)\\) <br/>

<!--listend-->

-   Worst case pivot is maximum or minimum <br/>
    -   Partition areof size \\(0,\ n-1\\) <br/>
    -   \\(\displaystyle T( n) =\ T( n-1) +n\\)\\( \\) <br/>
    -   \\(\displaystyle T( n) \ =\ n+( n-1) +\dotsc +1\\) <br/>
    -   \\(\displaystyle T( n) \ =\ O\left( n^{2}\right)\\) <br/>

<!--listend-->

-   However **average** case is \\(\displaystyle O( n\log n)\\) <br/>

<!--listend-->

-   Randomization <br/>
    -   Any fixed position of pivot allows us to construct worst case. <br/>
    -   Instead pivot position is choosen randomly. <br/>
    -   Expected running time is \\(\displaystyle O( n\log n)\\) <br/>


#### Summary {#summary}

-   To avoid worst case randomly choose the pivot. <br/>
-   Quicksort works inplace and can work iteratively. <br/>
-   Very fast in practise and often used for built-in sorting functions. <br/>
-   \\(\displaystyle \boxed{\boldsymbol{Worst\ Case\ Time\ Complexity} :\ O\left( n^{2}\right)}\\) <br/>

-   \\(\displaystyle \boxed{\boldsymbol{Average\ Time\ Complexity} :\ O( n\log n)}\\) <br/>

