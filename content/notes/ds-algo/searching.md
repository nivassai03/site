+++
title = "Searching"
author = ["John Doe"]
draft = false
toc = true
math = true
+++

## Searching {#searching}


### Binary Search {#binary-search}

```cpp
#include <iostream>
#include <vector>

int search(std::vector<int> &nums,int target){
    auto n = nums.size(); // size() gives std::vector<int>::size_type
    int start = 0;
    int end = n-1;
    while(start <= end){
        int mid = start+(end-start)/2;
        if(target == nums[mid]){
            return mid;
        }
        else if(target > nums[mid]){
            start = mid+1;
        }
        else{
            end = mid-1;
        }
    }
    return -1;
}
```

