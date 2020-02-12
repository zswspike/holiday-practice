# 删除与获得点数
给定一个整数数组 nums ，你可以对它进行一些操作。

每次操作中，选择任意一个 nums[i] ，删除它并获得 nums[i] 的点数。之后，你必须删除每个等于 nums[i] - 1 或 nums[i] + 1 的元素。

开始你拥有 0 个点数。返回你能通过这些操作获得的最大点数。
### 示例 1:
输入: nums = [3, 4, 2]

输出: 6

解释: 

删除 4 来获得 4 个点数，因此 3 也被删除。

之后，删除 2 来获得 2 个点数。总共获得 6 个点数。
### 示例 2:
输入: nums = [2, 2, 3, 3, 3, 4]

输出: 9

解释: 

删除 3 来获得 3 个点数，接着要删除两个 2 和 4 。

之后，再次删除 3 获得 3 个点数，再次删除 3 获得 3 个点数。

总共获得 9 个点数。
```c
int deleteAndEarn(int* nums, int numsSize){
    if(numsSize==0)return 0;
    if(numsSize==1)return nums[0];
    int max=0;
    for(int i=0;i<numsSize;i++){
        if(max<nums[i])max=nums[i];
    }
    int all[max+1];
    for(int i=0;i<=max;i++){
        all[i]=0;
    }
    for(int i=0;i<numsSize;i++){
        all[nums[i]]++;
    }
    for(int i=1;i<=max;i++){
        all[i]*=i;
    }
    int dp[max+1];
    dp[0]=0;
    dp[1]=all[1];
    dp[2]=fmax(all[2],dp[1]);
    for(int i=3;i<=max;i++){
        dp[i]=all[i]+fmax(dp[i-2],dp[i-3]);
    }
    return fmax(dp[max],dp[max-1]);
}
```
