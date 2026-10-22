# Basic Arrays Problem: 

---

## Sum of Array elements: 

<P>
  Difficulty : Easy 

  Given an integer array arr[], return the sum of all elements of arr.

Examples:

Input: arr[] = [1, 2, 3, 4]
Output: 10
Explanation: 1 + 2 + 3 + 4 = 10.
Input: arr[] = [1, 3, 3]
Output: 7
Explanation: 1 + 3 + 3 = 7.
Constraints:

0 ≤ arr.size() ≤ 105
0 ≤ arr[i] ≤ 104
</P>

### Solution: 

```
class Solution {
  public:
    int arraySum(vector<int>& arr) {
        // code here
        int sum = 0;
        for(int i = 0; i<arr.size(); i++){
            sum = sum + arr[i];
        }
        return sum;
    }
};
```
---

## Count odd Numbers in an Array (TUF): 

<P>
  Difficulty: Easy

  Given an array of n elements. The task is to return the count of the number of odd numbers in the array.

Example 1:
Input: n=5, array = [1,2,3,4,5]

Output: 3

Explanation: The three odd elements are (1,3,5).

Example 2:
Input: n=6, array = [1,2,1,1,5,1]

Output: 5

Explanation: The five odd elements are one 5 and four 1's.
</P>

### Solution: 

```
class Solution{
    public int countOdd(int[] arr, int n) {
        int count = 0;
       for(int i = 0; i<n;i++){
        if(arr[i] % 2 != 0){
            count++;
        }
       }
       return count;
    }
}
```
---
