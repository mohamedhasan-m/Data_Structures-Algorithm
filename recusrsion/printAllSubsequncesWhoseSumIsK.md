# Print All Subsequnces Whose Sum is K: 

---

```
#include <bits/stdc++.h>
using namespace std;

void printSubsequences(int ind, vector<int> &ds, int arr[], int n, int sum, int k) {

    // Base case
    if(ind == n) {
        if(sum == k) {
            for(auto it : ds) {
                cout << it << " ";
            }
            cout << endl;
        }
        return;
    }

    // PICK
    ds.push_back(arr[ind]);
    printSubsequences(ind + 1, ds, arr, n, sum + arr[ind], k);
    ds.pop_back();

    // NOT PICK
    printSubsequences(ind + 1, ds, arr, n, sum, k);
}

int main() {

    int arr[] = {1, 2, 1};
    int n = 3;
    int k = 2;

    vector<int> ds;

    printSubsequences(0, ds, arr, n, 0, k);

    return 0;
}
```
---

<img width="1672" height="941" alt="Neon Recursion Tree for Sum K" src="https://github.com/user-attachments/assets/d9259331-db6b-46d9-b94f-5039629d6f15" />
