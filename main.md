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
# 4. Count numbers up to N having Kth bit set -  O(1)

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

# 5. Sum of all divisors from 1 to n

```cpp
int divisorSum(int n)
{
    int sum = 0;
    for (int i = 1; i <= n; ++i)
        sum += (n / i) * i;
    return sum;
}
```
## Explanation:
Let n = 6,
=> F(1) + F(2) + F(3) + F(4) + F(5) + F(6)
=> 1 will occurs 6 times in F(1), F(2),
   F(3), F(4), F(5) and F(6)
=> 2 will occurs 3 times in F(2), F(4) and
   F(6)
=> 3 will occur 2 times in F(3) and F(6)
=> 4 will occur 1 times in F(4)
=> 5 will occur 1 times in F(5)
=> 6 will occur 1 times in F(6)

# 6.SPOJ ABC PATH
https://www.spoj.com/problems/ABCPATH/
```cpp
#include "bits/stdc++.h"
using namespace std;

typedef long long ll;
typedef long double ld;


char mat[51][51];
int r, c, dis[51][51];
#define in_range(x, y, r, c) (x < r && y < c && x >= 0 && y >= 0)

int dx[] = { -1, -1, -1,  0,  0, 1, 1, +1};
int dy[] = { -1,  0, +1, -1, +1, -1, 0, +1};

void dfs(int i, int j, int dist) {
	int x, y;
	dis[i][j] = dist + 1;

	for (int loop = 0; loop < 8; loop++) {
		x = i + dx[loop];
		y = j + dy[loop];
		if (in_range(x, y, r, c) && mat[x][y] == mat[i][j] + 1 && dis[x][y] < dis[i][j] + 1) {
			dfs(x, y, dis[i][j]);
		}
	}



}

int main() {

	int max, tc = 0;

	while (true) {
		scanf("%d%d", &r, &c);
		if (!r && !c)
			break;
		tc++;
		for (int i = 0; i < r; i++) {
			scanf("%s", mat[i]);
			for (int j = 0; j < c; j++)
				dis[i][j] = 0;
		}
		for (int i = 0; i < r; i++) {
			for (int j = 0; j < c; j++) {
				if (mat[i][j] == 'A' && dis[i][j] == 0)
					dfs(i, j, 0);
			}
		}
		max = dis[0][0];
		for (int i = 0; i < r; i++) {
			for (int j = 0; j < c; j++)
				if (max < dis[i][j])
					max = dis[i][j];
		}
		printf("Case %d: %d\n", tc, max);
	}
	return 0;
}
```
