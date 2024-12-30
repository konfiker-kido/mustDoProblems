# Shortest Job first
(GFG)
#### Problem Statement
Geek is a software engineer. He is assigned with the task of calculating average waiting time of all the processes by following shortest job first policy.
The shortest job first (SJF) or shortest job next, is a scheduling policy that selects the waiting process with the smallest execution time to execute next.

Given an array of integers bt of size n. Array bt denotes the burst time of each process. 
Calculate the average waiting time of all the processes and return the nearest integer which is smaller or equal to the output.

Note: Consider all process are available at time 0.

### Example 1
```
Input:
n = 5
bt = [4,3,7,1,2]

Output: 4
```
##### Explanation: After sorting burst times by shortest job policy, calculated average waiting time is 4.


### Example 2
```
Input:
n = 4
arr = [1,2,3,4]

Output: 2
```
##### Explanation: After sorting burst times by shortest job policy, calculated average waiting time is 2.

## Intution 

1. to get the sortest burst time , **sort all the array**
now [1, 2, 3, 4, 7]

waiting=0, ans=0;

```
to complete = waiting time + time (where time is arr[i] )
to complete arr[0]  will take   arr[i]+waiting time,       1 sec
to complete arr[1]  will take   arr[i]+waiting time,       3 sec
to complete arr[2]  will take   arr[i]+waiting time,       6 sec
to complete arr[3]  will take   arr[i]+waiting time,       10 sec
to complete arr[4]  will take   arr[i]+waiting time,       task completed



so total is ans=20 
return 20/ size of arr

```


## C++ solution   
```cpp
class Solution {
  public:
    long long solve(vector<int>& bt) {
        // code here
        
        long long waiting=0;
        long long ans=0;
       
        
        sort(bt.begin(),bt.end());
        
        for(int i=0;i<bt.size()-1;i++){
           
            waiting+=bt[i];
            ans+=waiting;
        }
        
        return ans/(bt.size());
    }
};

```



