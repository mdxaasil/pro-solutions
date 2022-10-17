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
#define MAX LLONG_MAX
#define MIN LLONG_MIN
#define rep(i, a, b, inc) for(long long i = a; i < b; i += inc)
#define REP(i, n) rep(i, 0, n, 1)
#define all(x) (x).begin(), (x).end()
#define pb push_back
#define ff first
#define ss second
#define d1(x) cerr << #x<<" "<< x << endl;
#define d2(x, y) cerr << "## " << #x << " : " << x << " | " << #y << " : " << y << " ##\n";
 
 
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
