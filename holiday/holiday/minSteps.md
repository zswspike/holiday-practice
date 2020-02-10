# 只有两个键的键盘
最初在一个记事本上只有一个字符 'A'。你每次可以对这个记事本进行两种操作：

Copy All (复制全部) : 你可以复制这个记事本中的所有字符(部分的复制是不允许的)。

Paste (粘贴) : 你可以粘贴你上一次复制的字符。

给定一个数字 n 。你需要使用最少的操作次数，在记事本中打印出恰好 n 个 'A'。输出能够打印出 n 个 'A' 的最少操作次数。

### 示例 1:
输入: 3

输出: 3

解释:

最初, 我们只有一个字符 'A'。

第 1 步, 我们使用 Copy All 操作。

第 2 步, 我们使用 Paste 操作来获得 'AA'。

第 3 步, 我们使用 Paste 操作来获得 'AAA'。

说明:

n 的取值范围是 [1, 1000] 。
## 代码：
```c
int minSteps(int n){
    if(n==1)return 0;
    if(n<4)return n;
    int dp[n+1];
    dp[1]=0;
    dp[2]=2;
    dp[3]=3;
    for(int i=4;i<=n;i++){
        if(i%2==0)dp[i]=dp[i/2]+2;
        else{
            dp[i]=1000;
            for(int k=3;k<=i;k+=2){
                if(i==k)dp[i]=fmin(k,dp[i]);
                else if(i!=k&&i%k==0){
                    int tem=i/k;
                    if(dp[i]>dp[k]+tem)dp[i]=dp[k]+tem;
                }
            }
        }
    }
    return dp[n];
}
```
