# 1. Fibonacci number
https://leetcode.com/problems/fibonacci-number/


```cpp
int fib(int N) 
{
	int dp[2] = {0, 1};

	for (int i = 2; i <= N; i++)
	   dp[i % 2] = dp[0] + dp[1];

	return dp[N % 2];
}
```

# 2. Meeting on the Line
https://codeforces.com/contest/1730/problem/B

```cpp
#include <bits/stdc++.h>
 
using namespace std;
 
void solve() {
    int n;
    cin >> n;
 
    vector<int> x(n), t(n);
    for(int i = 0; i < n; i++)
        cin >> x[i];
 
    for(int i = 0; i < n; i++)
        cin >> t[i];
 
    vector<int> a;
    for(int i = 0; i < n; i++) {
        a.push_back(x[i] + t[i]);
        a.push_back(x[i] - t[i]);
    }
 
    int mn = a[0], mx = a[0];
    for(int val : a) {
        mn = min(mn, val);
        mx = max(mx, val);
    }
 
    int sum = mn + mx;
    cout << sum / 2;
    if(sum % 2 != 0)
        cout << ".5";
    cout << '\n';
}
 
int main() {
    int t;
    cin >> t;
 
    while(t--)
        solve();
}
```
# 3. Rebellion
https://codeforces.com/contest/1746/problem/B

```cpp
#include "bits/stdc++.h"
 
using namespace std;
 
#define endl '\n'

 
typedef long long ll;
typedef long double ld;
 
void init_code()
{ 
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);
}

ll solve(ll n)
{
    vector<ll> a(n);
    cin>>a;
    ll o = count(all(a), 0);
    ll ans = 0;
    for(ll i = 0;i<o;i++)
        if(a[i]!=0) ans++;
    return ans;
}

int main()
{
    init_code();

    ll T=1, n, c;
    cin >> T;
    while (T--)
    {
        cin >> n;
        c = solve(n);
        cout << c << endl; //(c?"YES":"NO")
    }
    return 0;
}
```
# 3. Count numbers up to N having Kth bit set -  O(1)

```cpp

// Function to return the count
// of number of 1's at ith bit
// in a range [1, n - 1]
long long getcount(long long n, int k)
{
	// Store count till nearest
	// power of 2 less than N
	long long res = (n >> (k + 1)) << k;

	// If K-th bit is set in N
	if ((n >> k) & 1)

		// Add to result the nearest
		// power of 2 less than N
		res += n & ((1ll << k) - 1);

	// Return result
	return res;
}

// Driver Code
int main()
{

	long long int N = 14;
	int K = 2;

	// Function Call
	cout << getcount(N + 1, K) << endl;

	return 0;
}

```
