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
## Subsets II(90.Leetcode): 

<P>
	Difficuty: Medium 

	Given an integer array nums that may contain duplicates, return all possible subsets (the power set).

The solution set must not contain duplicate subsets. Return the solution in any order.

 

Example 1:

Input: nums = [1,2,2]
Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]
Example 2:

Input: nums = [0]
Output: [[],[0]]
 

Constraints:

1 <= nums.length <= 10
-10 <= nums[i] <= 10
</P>

### Solution: 

```
class Solution {
public:
    void solve(vector<int> &nums, int index, vector<vector<int>> &ans, vector<int> &ds){
        ans.push_back(ds);
        for(int i = index;i<nums.size();i++){
            if(i>index && nums[i] == nums[i-1]){
                continue;
            }
            ds.push_back(nums[i]);
            solve(nums, i+1, ans, ds);
            ds.pop_back();
        }
    }
    vector<vector<int>> subsetsWithDup(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        vector<vector<int>> ans;
        vector<int> ds;
        solve(nums, 0, ans, ds);
        return ans;
    }
};
```

### Recursion Tree: 

<img width="1536" height="1024" alt="Subsets II Recursion Tree Infographic" src="https://github.com/user-attachments/assets/05792a00-03a0-4b3a-82fa-da4f6a787739" />

---

## Combination Sum III (216.Leetcode): 

<P>
	Difficulty: Medium 

	Find all valid combinations of k numbers that sum up to n such that the following conditions are true:

Only numbers 1 through 9 are used.
Each number is used at most once.
Return a list of all possible valid combinations. The list must not contain the same combination twice, and the combinations may be returned in any order.

 

Example 1:

Input: k = 3, n = 7
Output: [[1,2,4]]
Explanation:
1 + 2 + 4 = 7
There are no other valid combinations.
Example 2:

Input: k = 3, n = 9
Output: [[1,2,6],[1,3,5],[2,3,4]]
Explanation:
1 + 2 + 6 = 9
1 + 3 + 5 = 9
2 + 3 + 4 = 9
There are no other valid combinations.
Example 3:

Input: k = 4, n = 1
Output: []
Explanation: There are no valid combinations.
Using 4 different numbers in the range [1,9], the smallest sum we can get is 1+2+3+4 = 10 and since 10 > 1, there are no valid combination.
 

Constraints:

2 <= k <= 9
1 <= n <= 60
</P>

### Solution: 

```
class Solution {
public:
    vector<vector<int>> result;
    void solve(vector<int> &combination,int k, int n, int start){
        if( k ==  combination.size()){
            if(n==0){
                result.push_back(combination);
                return;
            }
        }
        for(int i = start; i <= 9;++i){
            combination.push_back(i);
            solve(combination, k, n-i, i+1);
            combination.pop_back();
        }
    }
    vector<vector<int>> combinationSum3(int k, int n) {
        vector<int> combination;
        solve(combination, k, n, 1);
        return result;
    }
};
```

#### Recursion Tree: 

<img width="1536" height="1024" alt="Combination Sum III Recursion Tree Infographic" src="https://github.com/user-attachments/assets/fb0a5b42-8685-439b-99a6-4985f8f86c9e" />

---
## Letter Combinations of a Phone Number: (17. Leetcode): 

<P>
	Difficulty: Medium 

	Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

<img width="1200" height="973" alt="image" src="https://github.com/user-attachments/assets/8168862e-15f1-4ecd-bf7c-e3d056fb7d5d" />

 

Example 1:

Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
Example 2:

Input: digits = "2"
Output: ["a","b","c"]
 

Constraints:

1 <= digits.length <= 4
digits[i] is a digit in the range ['2', '9']
</P>

### Solution: 

```
class Solution {
private:
   vector<string> answer;
   string digits;

   string getLetters(char digit){
    switch(digit){
        case'2':
            return "abc";
        case'3':
            return "def";
        case'4':
            return "ghi";
        case'5':
            return "jkl";
        case'6':
            return "mno";
        case'7':
            return "pqrs";
        case'8':
            return "tuv";
        case'9':
            return "wxyz";
    }
    return "";
   }

   void generateStrings(int i , string &current){
    if ( i == digits.length()){
        answer.push_back(current);
        return;
    }
    // place all possible letters to at this ith place
    string letters = getLetters(digits[i]);
    for(int j = 0; j<letters.length(); j++){
        current.push_back(letters[j]);
        generateStrings(i+1, current);
        current.pop_back();
    }
   }
public:
    vector<string> letterCombinations(string digits) {
        this->digits = digits;

        answer.clear();

        string current = "";
        generateStrings(0, current);

        return answer;
    }
};
```
---
