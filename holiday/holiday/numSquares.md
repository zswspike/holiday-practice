# 完全平方数
给定正整数 n，找到若干个完全平方数（比如 1, 4, 9, 16, ...）使得它们的和等于 n。你需要让组成和的完全平方数的个数最少。
### 示例 1:
输入: n = 12

输出: 3 

解释: 12 = 4 + 4 + 4.
### 示例 2:
输入: n = 13

输出: 2

解释: 13 = 4 + 9.
## 代码：
```c
int numSquares(int n){
    if(n==0)return 0;
    if(n==1)return 1;
    int dp[n+1];
    dp[0]=0;
    dp[1]=1;
    int i;
    for(int i=2;i<=n;i++){
        dp[i]=dp[i-1]+1;
        for(int t=2;t*t<=i;t++){
            dp[i]=fmin(dp[i-t*t]+1,dp[i]);
        }
    }
    return dp[n];
}
```
