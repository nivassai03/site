+++
title = "Search"
author = ["John Doe"]
draft = false
weight = 1
toc = true
math = true
+++

## Search {#search}


### Binary Search {#binary-search}

```python

def binary_search(L,x):
    list_size = len(L)
    start = 0
    end = list_size - 1
    mid = 0
    while(start <= end):
        mid = (start+end) // 2

        if x == L[mid]:
            return mid

        elif x > L[mid]:
            start = mid+1
        else:
            end = mid-1

    return -1




```

