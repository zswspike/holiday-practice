# holiday-practice
每日一练2020寒假
题目：
给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。
不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。
解答：
int removeDuplicates(int* nums, int numsSize){
    int i = 0,j = 0;
    for (; i < numsSize; i++)
    {
        if (nums[j] != nums[i])
        {   
            // j += 1;
            nums[++j] = nums[i];
        }
        
    }
    return ++j;
}
