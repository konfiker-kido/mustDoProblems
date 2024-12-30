# 852. Peak Index in a Mountain Array

You are given an integer mountain array arr of length n where the values increase to a peak element and then decrease.

Return the index of the peak element.

Your task is to solve it in O(log(n)) time complexity.

### Example 1
```
Input:
arr = [0,1,0]

Output: 1
```


### Example 2
```
Input:
arr = [0,2,1,0]

Output: 1
```
### Example 3
```

Input: 
arr = [0,10,5,2]

Output: 1
```

## C++ Code  Using Binary Search 
```cpp
class Solution {
public:
    int peakIndexInMountainArray(vector<int>& arr) {
        int start=0,end=arr.size()-1;
        int mid=start+(end-start)/2;
        while(start<end){  // we have to traverse all the elements till start!=end
            if(arr[mid]<arr[mid+1]){ // tracking the peak
                start=mid+1;
            }
            else{
                end=mid; // mid can be peak as well that's why not doing e=mid+1
            }
             mid=start+(end-start)/2;
        }
        return start; // returning the index of peak element, can be return the end as well bcz both on the peak
    }
};


```
