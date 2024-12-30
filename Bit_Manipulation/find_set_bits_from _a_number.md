# Find Set Bit's From  A Number

```

N = 6
```
```
Output:
2
```
## Explanation
- Binary representation is '110' 
- So the count of the set bit is 2.


# C++ Code
```cpp
int countSetBits(int number){

   int count=0;

   while(number>0){

       if( 1 & number)  //checking if the last bit is set or not
          count++;

          number>>=1; // right shifting the number to trim down
   }
  return count;
}
```
