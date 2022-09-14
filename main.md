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
