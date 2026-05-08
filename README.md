# Reordering Numbers (Divisibility Split)

## Idea

We split numbers into 3 groups based on divisibility:

* **only2** → divisible by 2 but NOT 3
* **only3** → divisible by 3 but NOT 2
* **rest** → everything else (both or neither)

Then we print them in a fixed order:

👉 `only2 → rest → only3`

### Why this works?

Think of 2 and 3 as two “forces” pulling numbers in different directions.
We separate them first so their effects don’t clash, then place the neutral/both ones in the middle like a buffer zone ⚖️.

---

## Complexity

* **Time:** `O(n)` per test case
* **Space:** `O(n)`

---

## C++ Solution

```cpp id="div2_3_reorder"
#include <bits/stdc++.h>
using namespace std;

bool has2(long long x){
    return x % 2 == 0;
}

bool has3(long long x){
    return x % 3 == 0;
}

int main() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);

    int t;
    cin >> t;

    while (t--) {
        int n;
        cin >> n;

        vector<long long> a(n);
        vector<long long> only2, only3, rest;

        for (auto &x : a) {
            cin >> x;

            bool c2 = has2(x);
            bool c3 = has3(x);

            if (c2 && !c3)
                only2.push_back(x);
            else if (c3 && !c2)
                only3.push_back(x);
            else
                rest.push_back(x);
        }

        vector<long long> ans;

        for (auto x : only2) ans.push_back(x);
        for (auto x : rest) ans.push_back(x);
        for (auto x : only3) ans.push_back(x);

        for (auto x : ans)
            cout << x << " ";

        cout << "\n";
    }

    return 0;
}
```
