# Basic Strings: 

---

## Reverse String (344. Leetcode): 

<P>
  Difficulty: Easy

  Write a function that reverses a string. The input string is given as an array of characters s.

You must do this by modifying the input array in-place with O(1) extra memory.

 

Example 1:

Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
Example 2:

Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
 

Constraints:

1 <= s.length <= 105
s[i] is a printable ascii character.
</P>

### Solution: 

```
class Solution {
public:
    void reverseString(vector<char>& s) {
        int left = 0;
        int right = s.size() - 1;
        while(left < right){
            char tmp = s[left];
            s[left] = s[right];
            s[right] = tmp;
            left++;
            right--;
        }
    }
};
```

---

## Valid Palindrome: 

<P>
  Difficulty: Easy

  A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.

 

Example 1:

Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
Example 2:

Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
Example 3:

Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
 

Constraints:

1 <= s.length <= 2 * 105
s consists only of printable ASCII characters.

</P>

### Solution:

```
class Solution {
private:
    // returns the string containing only alphanumeric numbers
    string clean(string s){
        string cleanedS = "";
        for(int i = 0; i<s.length();i++){
            char ch = s[i];
            ch = tolower(ch);
            // append this ch to cleanedS if this is alphanumeric
            if(ch>='a' && ch<='z' || (ch>='0' && ch<='9')){
                cleanedS.push_back(ch);
            }
        }
        return cleanedS;
    }

    bool isPalindromeHelper(string s){
        for(int i = 0; i<s.length()/2;i++){
            if(s[i] != s[s.length()-i-1]){
                return false;
            }
        }
        return true;
    }
public:
    bool isPalindrome(string s) {
        return isPalindromeHelper(clean(s));
    }
};
```
---
