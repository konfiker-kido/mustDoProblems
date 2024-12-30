# 2553. Separate the Digits in an Array

#### Input:
```
nums = [13,25,83,77]
```
#### Output: 
```
[1,3,2,5,8,3,7,7]
```
#### Input 2: 
```
nums = [7,1,3,9]
```
# Output:
```
[7,1,3,9]
```
C++ Code
```cpp
class Solution {
public:
    vector<int> separateDigits(vector<int>& nums) {
        vector<int> ans;

        for(int i=nums.size()-1;i>=0;i--){
           int val=nums[i];
            
            while(val>0){
                ans.push_back(val%10);
                val/=10;
            }
        }
        reverse(ans.begin(),ans.end());
        return ans;

        // Second Method Using string 
            //     for(int i=0; i<nums.size(); i++) {
            // string num = to_string(nums[i]);
            // for(int j=0; j<num.size(); j++) {
            //     res.push_back(num[j]-'0');
            // }    
            // } 
    }
};

```
