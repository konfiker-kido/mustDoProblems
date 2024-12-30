Given an integer array nums where every element appears three times except for one,
which appears exactly once. Find the single element and return it.

You must implement a solution with a linear runtime complexity and use only constant extra space.

 

#### Example 1
```text
Input:
nums = [2,2,3,2]
```
```
Output:
  3
```
#### Example 2

```text
Input: 
nums = [0,1,0,1,0,1,99]
```
```
Output:
 99
```

```cpp
class Solution {
public:
    int singleNumber(vector<int>& nums) {
          
        int n=nums.size();
        int ans=0;
        for(int i=0;i<32;i++){
               
               int bitSum=0;
              for(int j=0;j<n;j++){
                 if( ((nums[j]>>i) & 1)==1 ) bitSum++; 
                     bitSum%=3;      // it can be done after the this loop as well
                 
             }
             if(bitSum%3==1) ans |= bitSum<<i;  // bitSum << i => means i'm  doing 2 power i
        }

        return ans;
    }
};
```
