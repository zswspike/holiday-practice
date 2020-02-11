# 整数拆分
给定一个正整数 n，将其拆分为至少两个正整数的和，并使这些整数的乘积最大化。 返回你可以获得的最大乘积。
### 示例 1:
输入: 2
输出: 1

解释: 2 = 1 + 1, 1 × 1 = 1。

### 示例 2:
输入: 10

输出: 36

解释: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36。

说明: 你可以假设 n 不小于 2 且不大于 58。
## 代码：
```c
int integerBreak(int n){
    if(n<2)return 0;
    if(n==2)return 1;
    int dp[n+1];
    dp[1]=1;
    dp[2]=1;
    dp[3]=2;
    for(int i=4;i<=n;i++){
        dp[i]=0;
        for(int j=1;j<i;j++){
            int tem=fmax(dp[i-j],i-j)*fmax(dp[j],j);
            dp[i]=fmax(tem,dp[i]);
        }
    }
    return dp[n];
}
```
