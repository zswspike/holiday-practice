# 主要元素
如果数组中多一半的数都是同一个，则称之为主要元素。给定一个整数数组，找到它的主要元素。若没有，返回-1。

### 示例 1：
输入：[1,2,5,9,5,9,5,5,5]

输出：5
 
### 示例 2：
输入：[3,2]

输出：-1

### 示例 3：
输入：[2,2,1,1,1,2,2]

输出：2
## 代码：
```c
int majorityElement(int* nums, int numsSize){
    int k=nums[0],js=1;
    for(int i=1;i<numsSize;i++){
        if(nums[i]!=k)js--;
        else js++;
        if(js==0){k=nums[i];js++;}
    }
    if(js==0)return -1;
    return k;
}
```
