# 给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素最多出现两次，返回移除后数组的新长度。
不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。

### 示例 1:
给定 nums = [1,1,1,2,2,3],

函数应返回新长度 length = 5, 并且原数组的前五个元素被修改为 1, 1, 2, 2, 3 。

你不需要考虑数组中超出新长度后面的元素。
### 示例 2:
给定 nums = [0,0,1,1,1,1,2,3,3],

函数应返回新长度 length = 7, 并且原数组的前五个元素被修改为 0, 0, 1, 1, 2, 3, 3 。

你不需要考虑数组中超出新长度后面的元素。
## 解答：
```c
int removeDuplicates(int* nums, int numsSize){
    int js=1;
    for(int i=0;i<numsSize-1;i++){
        if(nums[i]==nums[i+1])js++;
        else{
            if(js<=2){
                js=1;
                continue;
            }
            int tem=js-2;
            int cs=i+1-tem;
            numsSize-=tem;
            for(int j=cs;j<numsSize;j++){
                nums[j]=nums[j+tem];
            }
            i=cs-1;
            js=1;
        }
    }
    if(js>=2)numsSize-=js-2;
    return numsSize;
}
```
