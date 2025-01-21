# Sliding Window Maximum

#### Problem Statement: 
Given an array of integers arr, there is a sliding window of size k which is moving from the very left of the array to the very right. 
You can only see the k numbers in the window. Each time the sliding window moves right by one position. Return the max sliding window.

```Example

Example 1:

Input: arr = [4,0,-1,3,5,3,6,8], k = 3

Output: [4,3,5,5,6,8]

Explanation: 

Window position                   Max
------------------------         -----
[4  0  -1] 3  5  3  6  8           4
 4 [0  -1  3] 5  3  6  8           3
 4  0 [-1  3  5] 3  6  8           5
 4  0  -1 [3  5  3] 6  8           5
 4  0  -1  3 [5  3  6] 8           6
 4  0  -1  3  5 [3  6  8]          8

For each window of size k=3, we find the maximum element in the window and add it to our output array.

Example 2:

Input: arr= [20,25], k = 2

Output: [25]

Explanation: There’s just one window is size 2 that is possible and the maximum of the two elements is our answer.

```


#### Approach

- We address this problem with the help of a data structure that keeps checking whether the incoming element is larger than the already present elements.
- This could be implemented with the help of a de-queue. When shifting our window, we push the new element in from the rear of our de-queue.
- Every time before entering a new element, we first need to check whether the element present at the front is out of bounds of our present window size.
- If so, we need to pop that out. Also, we need to check from the rear that the element present is smaller than the incoming element.
- If yes, there’s no point storing them and hence we pop them out. Finally, the element present at the front would be our largest element.



#### Code ( C++ )
```cpp
class Solution {
public:
   
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        
         deque<int> windowIndex;
         vector<int> ans;
        int n=nums.size();
         for(int i=0;i<n;i++){
            
              if(!windowIndex.empty() and windowIndex.front()<=(i-k))
                  windowIndex.pop_front();

                  while( ! windowIndex.empty() and nums[i]>nums[windowIndex.back()]){
                         windowIndex.pop_back();
                  }
                  windowIndex.push_back(i);
                  if(i>=(k-1)){
                      ans.push_back(nums[windowIndex.front()]);
                  }
         }

         return ans;

    }
   };
  
  ```

#### Output:
```
Maximum element in every 3 window
4 3 5 5 6 8
```

##### Time Complexity: O(N)

##### Space Complexity: O(K)
