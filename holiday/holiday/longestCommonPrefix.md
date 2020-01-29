# 最长公共前缀
###
编写一个函数来查找字符串数组中的最长公共前缀。
如果不存在公共前缀，返回空字符串 ""。
### 示例 1:

输入: ["flower","flow","flight"]

输出: "fl"
### 示例 2:
输入: ["dog","racecar","car"]

输出: ""

解释: 输入不存在公共前缀。
### 解答：
```c
char * longestCommonPrefix(char ** strs, int strsSize){
    if(strsSize==0)return "";
    if(strsSize==1)return strs[0];
    for(int i=0;;i++){
        int flag=1;
        for(int j=1;j<strsSize;j++){
            if(strs[0][i]!=strs[j][i]||strs[j][i]=='\0'){
                flag=0;
                strs[0][i]='\0';
                break;
            }
        }
        if(flag==0)break;
    }
    return strs[0];
}
```
