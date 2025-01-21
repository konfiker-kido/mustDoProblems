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

<img src="data:image/jpeg;base64,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"
     alt="Markdown Monster icon"
     style="float: left; margin-right: 10px;" />
