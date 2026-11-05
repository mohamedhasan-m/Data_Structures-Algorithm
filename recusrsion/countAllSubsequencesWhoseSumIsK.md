# Count All Subsequences Whose sum is K: 

---
```
#include <bits/stdc++.h>
using namespace std;

int countSubsequences(int ind, int arr[], int n, int sum, int k) {

    // Base case
    if(ind == n) {

        // YOUR CODE
        if( sum == k){
            return 1;
        }
        
        else return 0;
    }


    // PICK

    sum += arr[ind];

    int left = countSubsequences(ind + 1, arr, n, sum , k);

    sum -= arr[ind];

    // NOT PICK
    int right = countSubsequences(ind + 1,  arr, n ,sum, k);


    // RETURN COUNT
    return left + right;
}

int main() {

    int arr[] = {1, 2, 1};
    int n = 3;
    int k = 2;

    int ans = countSubsequences(0,arr, n, 0, k);

    cout << ans << endl;

    return 0;
}
```
---
<img width="1536" height="1024" alt="Recursion Tree_ Subsequences Summing to K" src="https://github.com/user-attachments/assets/157db96d-7a7b-4b79-b263-459713f06eef" />
