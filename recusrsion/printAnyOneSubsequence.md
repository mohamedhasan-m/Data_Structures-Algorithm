## Print Any One Subsequences Whose Sum is K: 

--- 

```
#include <bits/stdc++.h>
using namespace std;

bool printAnySubsequence(int ind, vector<int> &ds, int arr[], int n, int sum, int k) {

    // Base case
    if(ind == n) {
        if(sum == k){
            for(auto it : ds){
                cout<< it << " ";
            }
            cout<<endl;
            return true;
        }
        else return false;
    }


    // PICK
    ds.push_back(arr[ind]);
    if(printAnySubsequence(ind + 1, ds, arr, n, sum + arr[ind], k) == true){
        return true;
    } 
    ds.pop_back();

    // NOT PICK
    if(printAnySubsequence(ind + 1, ds, arr, n, sum, k) == true){
        return true;
    }

    return false;
}

int main() {

    int arr[] = {1, 2, 1};
    int n = 3;
    int k = 2;

    vector<int> ds;

    printAnySubsequence(0, ds, arr, n, 0, k);

    return 0;
}
```
---

<img width="1536" height="1024" alt="Subsequence Sum K_ Pick, Prune, Print" src="https://github.com/user-attachments/assets/afeaa1c9-dba0-453c-bd10-182c765e4c7b" />
