# Frequentely Asked Questions (Medium): 

---

## Count Subsets With Sum K (Code 360): 

<P>
  Difficulty: Medium 

  Problem statement
You are given an array 'arr' of size 'n' containing positive integers and a target sum 'k'.



Find the number of ways of selecting the elements from the array such that the sum of chosen elements is equal to the target 'k'.



Since the number of ways can be very large, print it modulo 10 ^ 9 + 7.



Example:
Input: 'arr' = [1, 1, 4, 5]

Output: 3

Explanation: The possible ways are:
[1, 4]
[1, 4]
[5]
Hence the output will be 3. Please note that both 1 present in 'arr' are treated differently.
Detailed explanation ( Input/output format, Notes, Images )
Sample Input 1 :
4 5
1 4 4 5


Sample Output 1 :
 3


Explanation For Sample Output 1:
The possible ways are:
[1, 4]
[1, 4]
[5]
Hence the output will be 3. Please note that both 1 present in 'arr' are treated differently.


Sample Input 2 :
3 2
1 1 1


Sample Output 2 :
3


Explanation For Sample Output 1:
There are three 1 present in the array. Answer is the number of ways to choose any two of them.


Sample Input 3 :
3 40
2 34 5


Sample Output 3 :
0


Expected time complexity :
The expected time complexity is O('n' * 'k').


Constraints:
1 <= 'n' <= 100
0 <= 'arr[i]' <= 1000
1 <= 'k' <= 1000

Time limit: 1 sec
</P>

### Solution: 

```
int solve(int ind, vector<int>& nums, int sum, int k) {

    if(ind == nums.size()) {
    if(sum == k)
        return 1;
        return 0;
    }

    // PICK
	int left = solve(ind + 1, nums, sum + nums[ind], k);

    // NOT PICK
    int right = solve(ind + 1, nums, sum, k);

    return left + right;
}


int findWays(vector<int>& arr, int k)
{
	// Write your code here.
	return solve(0, arr, 0, k);

}
```
---
