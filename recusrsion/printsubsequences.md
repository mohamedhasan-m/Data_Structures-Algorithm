# Print Subsequnces: 

---
## Solution: 

```
#include <bits/stdc++.h>
using namespace std;

void printSubsequences(int ind, vector<int> &ds, int arr[], int n) {

    // BASE CASE
    if(ind == n) {
        for(auto it : ds) {
            cout << it << " ";
        }

        if(ds.size() == 0) {
            cout << "{}";
        }

        cout << endl;
        return;
    }

    // PICK
    ds.push_back(arr[ind]);
    printSubsequences(ind + 1, ds, arr, n);
    ds.pop_back();

    // NOT PICK
    printSubsequences(ind + 1, ds, arr, n);
}

int main() {

    int arr[] = {1, 2, 3};
    int n = 3;

    vector<int> ds;

    printSubsequences(0, ds, arr, n);

    return 0;
}
```
---

<img width="1536" height="1024" alt="Printing Subsequences_ Pick or Skip" src="https://github.com/user-attachments/assets/9bde7c2f-1d5f-4f8c-98e0-995f656c2653" />
