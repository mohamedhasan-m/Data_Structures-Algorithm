# Math Basics
---
## Number of Digits (Coding Ninjas)

<P>Difficulty : Easy</P>

<P>Ninja want to add coding to his skill set so he started learning it. On the first day, he stuck to a problem in which he has given a long integer ‘X’ and had to count the number of digits in it.

Ninja called you for help as you are his only friend. Help him to solve the problem.

</p>

### EXAMPLE:
<p>
Input: 'X' = 2

Output: 1

As only one digit is ‘2’ present in ‘X’ so answer is ‘1’.
</P>

### Constraints :
<P>
1 <= 'T' <= 1000
1 <= ‘X’ <= 10^18
Time Limit: 1 sec
</p>

```
Sample Input 1 :
2
89
870
Sample Output 1 :
2
3
Explanation Of Sample Input 1 :
In test case ‘1’. There are ‘2’ digits present in ‘89’ that is ‘8’ and ‘9’. So the answer is ‘2’.
In test case ‘2’. There are ‘3’ digits present in ‘870’ that is ‘8’, ‘7’ and ‘0’. So the answer is ‘3’.
Sample Input 2 :
2
240
1
Sample Output 2 :
3
1
```

### Solution: 

```
#include <bits/stdc++.h> 
int countDigit(long long x) {
    // Write your code here.
    int count = 0;
    while (x>0)
    {
        count = count + 1;
        x = x/10;
    }
    return count;
}
```
---
## 7. Reverse Integer (Leetcode)

<P>Difficulty: Medium</P>

<P>
    Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

Assume the environment does not allow you to store 64-bit integers (signed or unsigned).

 

Example 1:

Input: x = 123
Output: 321
Example 2:

Input: x = -123
Output: -321
Example 3:

Input: x = 120
Output: 21
 

Constraints:

-231 <= x <= 231 - 1
</P>

### Solution: 

```
class Solution {
public:
    int reverse(int x) {
        int ReverseNumber = 0;
        while (x!=0)
        {
            int LastDigit = x %10;
            if (ReverseNumber > INT_MAX / 10 || 
               (ReverseNumber == INT_MAX / 10 && LastDigit > 7))
                return 0;

            if (ReverseNumber < INT_MIN / 10 || 
               (ReverseNumber == INT_MIN / 10 && LastDigit < -8))
                return 0;
            ReverseNumber = (ReverseNumber * 10) + LastDigit;
            x = x/10;
        }
        return ReverseNumber;
    }
};

```
---
## 9.Palindrome Number (LeetCode)

<P>Difficulty : Easy</P>

<P>
Given an integer x, return true if x is a palindrome, and false otherwise.

 

Example 1:

Input: x = 121
Output: true
Explanation: 121 reads as 121 from left to right and from right to left.
Example 2:

Input: x = -121
Output: false
Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
Example 3:

Input: x = 10
Output: false
Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
 

Constraints:

-231 <= x <= 231 - 1
</P>

### Solution: 

```
class Solution {
public:
    bool isPalindrome(int x) {
        int duplicate = x;
        int ReverseNumber = 0; 
        while (x > 0)
        {
            int LastDigit = x%10;
            if (ReverseNumber > INT_MAX / 10 ||
               (ReverseNumber == INT_MAX/10 && LastDigit >7))
            return 0;
            if (ReverseNumber < INT_MIN/10 ||
                (ReverseNumber == INT_MIN/10 && LastDigit < -8))
            return 0; 
            ReverseNumber = (ReverseNumber * 10) + LastDigit;         
            x = x/10;   
        }
        if (ReverseNumber == duplicate)
        {
            return true;
        } 
        else if (duplicate < 0)
        {
            return false;
        }  
        else
        { 
            return false;
        }
    }
};

```

---

##  Armstrong Number (Coding Ninjas)

<P>Difficulty: Easy</P>

<P>
Problem statement
You are given an integer ‘NUM’ . Your task is to find out whether this number is an Armstrong number or not.

A k-digit number ‘NUM’ is an Armstrong number if and only if the k-th power of each digit sums to ‘NUM’.

Example
153 = 1^3 + 5^3 + 3^3.

Therefore 153 is an Armstrong number.

Constraints:
1 <= ‘T’ <= 100
1 <= ‘N’ <= 10^9

Time Limit: 1 sec
</P>

```
Sample Input 1:
1
13
Sample Output 1:
NO
Explanation For Sample Input 1:
As 1^2 + 3^2 = 10 which is not equal to 13.So we can say it is not an Armstrong number.
Sample Input 2:
1
371
Sample Output 2:
YES
```
### Solution: 

```
#include <bits/stdc++.h> 
bool isArmstrong(int num) {
    // Write your code here
    int duplicate = num;
    int digits = 0;
    int temp = num;
    while (temp != 0)
    {
        digits++;
        temp /=10;
    }
    int sum = 0;
    temp = num; 
    while (temp != 0)
    {
        int LastDigit = temp%10;
        sum += pow(LastDigit,digits);
        temp /=10;
    }
    return sum == duplicate;
}
```
---
## Print All Divisors (Coding Ninjas)

<P>Difficulty: Easy</P>

<P>
Problem statement
Given an integer ‘N’, your task is to write a program that returns all the divisors of ‘N’ in ascending order.



For example:
'N' = 5.
The divisors of 5 are 1, 5.
</P>

```
Sample Input 1 :
10
Sample Output 1 :
1 2 5 10
Explanation of Sample Input 1:
The divisors of 10 are 1,2,5,10.
Sample Input 2 :
6
Sample Output 2 :
1 2 3 6
Explanation of Sample Input 2:
The divisors of 6 are 1, 2, 3, and 6.
Constraints :
1 <= 'N' <= 10^5
```

### Solution: 

```
#include <bits/stdc++.h>
using namespace std;

int* printDivisors(int n, int &size) {
    vector<int> ls;

    for (int i = 1; i * i <= n; i++) {
        if (n % i == 0) {
            ls.push_back(i);
            if ((n / i) != i)
                ls.push_back(n / i);
        }
    }

    sort(ls.begin(), ls.end());

    size = ls.size();          

    int* arr = new int[size]; 

    for (int i = 0; i < size; i++) {
        arr[i] = ls[i];      
    }

    return arr;             
}

```
---

## Check Prime (Code Ninjas)

<P>Difficulty: Easy</P>

<P>
    Given an integer, check if it is prime or not. 
</P>

```
Sample Input 1 :
7
Sample Output 1 :
 True
Sample Input 2 :
15
Sample Output 2 :
 False
```

### Solution: 

```
#include<iostream>
using namespace std;

int main() {
	// Write your code here
	int n; 
	cin>>n;
	int count = 0; 
	for (int i=1; i*i<=n; i++)
	{
		if(n % i == 0)
		{
			count++;
			if ((n/i) != i)
			{
				count++;
			}
		}
	}
	if (count == 2)
	{
		cout<<true;
	}
	else 
	{
		cout<<"false";
	}
}

```
---

##  GCD or HCF (Code Ninjas)

<P>
	Difficulty: Moderate 
</P>

<P>
	Problem statement
You are given two integers 'n', and 'm'.



Calculate 'gcd(n,m)', without using library functions.



Note:
The greatest common divisor (gcd) of two numbers 'n' and 'm' is the largest positive number that divides both 'n' and 'm' without leaving a remainder.


Example:
Input: 'n' = 6, 'm' = 4

Output: 2

Explanation:
Here, gcd(4,6) = 2, because 2 is the largest positive integer that divides both 4 and 6.
</P>

### Solution: 

```
int calcGCD(int n, int m){
    // Write your code here.
    while ((n>0 && m>0))
    {
        if ( n>m )
        {
            n = n % m;
        }
        else 
        {
            m = m % n;
        }
    }
    if (n == 0)
    {
        return m;
    }
    else
    {
        return n;
    }
}

```
---
## Count Number of odd Digits in a Integer (TUF): 

<P>
	Difficulty: Easy 

	You are given an integer n. You need to return the number of odd digits present in the number.

The number will have no leading zeroes, except when the number is 0 itself.

Example 1:
Input: n = 5

Output: 1

Explanation: 5 is an odd digit.

Example 2:
Input: n = 25

Output: 1

Explanation: The only odd digit in 25 is 5.
</P>

### Solution: 

```
class Solution {
public:
    int countOddDigit(int n) {
        int oddCount = 0;

        while (n != 0){
            int lastDigit = n%10;

            if(lastDigit % 2 != 0){
                oddCount++;
            }

            n = n/10;
        }

        return oddCount;
    }
};
```
---
## return the Largest Digit in a Number (TUF): 

<P>
	Difficulty : Easy 

	You are given an integer n. Return the largest digit present in the number.

Example 1:
Input: n = 25

Output: 5

Explanation: The largest digit in 25 is 5.

Example 2:
Input: n = 99

Output: 9

Explanation: The largest digit in 99 is 9.
</P>

### Solution: 

```
class Solution {
public:
    int largestDigit(int n) {
        int maxDigit = 0;

        while (n>0){
            int digit = n%10;
            
            if(digit > maxDigit){
                maxDigit = digit;
            }

            n = n/10;
        }

        return maxDigit;
    }
};
```
---
## Perfect Numbers (Geeks For Geeks): 

<P>
	Difficulty: Easy

	Given a number n, check if the number is perfect or not. A number is said to be perfect if sum of all its factors excluding the number itself is equal to the number.

Examples:

Input: n = 6
Output: true 
Explanation: Factors of 6 are 1, 2, 3 and 6. Excluding 6 their sum is 6 which is equal to n itself. So, it's a Perfect Number.
Input: n = 10
Output: false
Explanation: Factors of 10 are 1, 2, 5 and 10. Excluding 10 their sum is 8 which is not equal to n itself. So, it's not a Perfect Number.
Input: n = 15
Output: false
Explanation: Factors of 15 are 1, 3, 5, 15. Excluding 15 their sum is 9 which is not equal to n itself. So, it's not a Perfect Number.
Constraints:

1 ≤ n ≤ 109

</P>

### Solution: 

```

class Solution {
  public:
    bool isPerfect(int n) {
        if (n <= 1) return false;

        int sum = 1;

        for (int i = 2; i <= n / i; i++) {
            if (n % i == 0) {
                sum += i;

                if (i != n / i) {
                    sum += n / i;
                }
            }
        }

        return sum == n;
    }
};

```
---

## Count of Prime Numbers Till N(TUF): 

<P>

	Difficulty : Easy 

	
	You are given an integer n. You need to find out the number of prime numbers in the range [1, n] (inclusive). Return the number of prime numbers in the range.

A prime number is a number which has no divisors except, 1 and itself.

Example 1:
Input: n = 6

Output: 3

Explanation: Prime numbers in the range [1, 6] are 2, 3, 5.

Example 2:
Input: n = 10

Output: 4

Explanation: Prime numbers in the range [1, 10] are 2, 3, 5, 7.
</P>

### Solution: 

```

class Solution {
public:
    int primeUptoN(int n) {
        int count = 0;

        for (int n1 = 2; n1 <= n; n1++) {
            bool isPrime = true;

            for (int i = 2; i <= n1 / i; i++) {
                if (n1 % i == 0) {
                    isPrime = false;
                    break;
                }
            }

            if (isPrime) {
                count++;
            }
        }

        return count;
    }
};

```
---
