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
## Combination Sum 1 (39. Leetcode): 

<P>
	Difficulty: Medium 

	Given an array of distinct integers candidates and a target integer target, return a list of all unique combinations of candidates where the chosen numbers sum to target. You may return the combinations in any order.

The same number may be chosen from candidates an unlimited number of times. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

The test cases are generated such that the number of unique combinations that sum up to target is less than 150 combinations for the given input.

 

Example 1:

Input: candidates = [2,3,6,7], target = 7
Output: [[2,2,3],[7]]
Explanation:
2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
7 is a candidate, and 7 = 7.
These are the only two combinations.
Example 2:

Input: candidates = [2,3,5], target = 8
Output: [[2,2,2,2],[2,3,3],[3,5]]
Example 3:

Input: candidates = [2], target = 1
Output: []
 

Constraints:

1 <= candidates.length <= 30
2 <= candidates[i] <= 40
All elements of candidates are distinct.
1 <= target <= 40
</P>

### Solution: 

```
class Solution {
public:
    void findCombination(int ind, int target, vector<int> &arr, vector<vector<int>> &ans, vector<int> &ds){
        if(ind == arr.size()){
            if(target == 0){
                ans.push_back(ds);
            }
            return;
        }
        // pick up the element
        if(arr[ind] <= target){
            ds.push_back(arr[ind]);
            findCombination(ind, target - arr[ind], arr, ans, ds);
            ds.pop_back();
        }
        findCombination(ind+1, target, arr, ans, ds);
    }
    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        vector<vector<int>>ans;
        vector<int> ds;
        findCombination(0, target, candidates, ans, ds);
        return ans;
    }
};
```

#### Recusrsion Tree:

<img width="1536" height="1024" alt="Combination Sum I Recursion Tree Infographic" src="https://github.com/user-attachments/assets/fa2e13a1-373b-45fb-a963-05ffcdfbae9d" />

---
## Combinaition Sum II (40. Leetcode): 

<P>
	Difficulty: Medium 

	Given a collection of candidate numbers (candidates) and a target number (target), find all unique combinations in candidates where the candidate numbers sum to target.

Each number in candidates may only be used once in the combination.

Note: The solution set must not contain duplicate combinations.

 

Example 1:

Input: candidates = [10,1,2,7,6,1,5], target = 8
Output: 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]
Example 2:

Input: candidates = [2,5,2,1,2], target = 5
Output: 
[
[1,2,2],
[5]
]
 

Constraints:

1 <= candidates.length <= 100
1 <= candidates[i] <= 50
1 <= target <= 30
</P>

### Solution: 

```
class Solution {
public:
    void findCombination(int ind, int target,vector<int> &arr, vector<vector<int>> &ans, vector<int> &ds){
        if(target == 0){
            ans.push_back(ds);
            return;
        }
        for(int i = ind; i<arr.size();i++){
            if(i>ind && arr[i] == arr[i-1]) continue;
            if(arr[i] > target) break;
            ds.push_back(arr[i]);
            findCombination(i+1, target - arr[i], arr, ans, ds);
            ds.pop_back();
        }
    }
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        sort(candidates.begin(), candidates.end());
        vector<vector<int>> ans;
        vector<int> ds;
        findCombination(0, target, candidates, ans, ds);
        return ans;
    }
};
```

#### Recursion Tree: 

<img width="1536" height="1024" alt="Combination Sum II Recursion Tree Infographic" src="https://github.com/user-attachments/assets/f3438fd0-ff85-44b8-b9c6-70ac1a7865e6" />

---
## Subsets (78.Leetcode): 

<P>
	Difficulty: Medium 

	Given an integer array nums of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

 

Example 1:

Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
Example 2:

Input: nums = [0]
Output: [[],[0]]
 

Constraints:

1 <= nums.length <= 10
-10 <= nums[i] <= 10
All the numbers of nums are unique.
</P>

### Solution: 

```
class Solution {
public:
    void solve(int ind, int n, vector<int> &nums, vector<vector<int>> &ans, vector<int> &ds){
        if(ind == n){
            ans.push_back(ds);
            return;
        }
        solve(ind+1, n, nums, ans, ds);
        ds.push_back(nums[ind]);
        solve(ind+1,n,nums,ans,ds);
        ds.pop_back();
    }
    vector<vector<int>> subsets(vector<int>& nums) {
        int n = nums.size();
        vector<vector<int>> ans;
        vector<int> ds;
        solve(0, n,nums, ans, ds);
        return ans;
    }
};
```
#### Recursion Tree: 

<img width="1536" height="1024" alt="Subset Recursion Tree Infographic" src="https://github.com/user-attachments/assets/d385b285-3dc2-4cb6-b7d0-f98648fc9826" />


---
