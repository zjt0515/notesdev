# search

关键字：唯一不重复

静态查找表：只关注查找速度

动态查找表：还要关注增删速度

ASL：average serach length，反映了算法时间复杂度

## 顺序查找

查找成功/失败时间复杂度：O(n) 

优化：当顺序表有序存放时，找到一定时就不找

## 二分查找(对半搜索)

 仅适用于有序顺序表 

1. 比较mid和key，小于返回前一位，大于返回后一位
2. 直到 i 大于 j

```c++
// 基于升序排列
int BinarySearch(int q[],int n, int key) {
	int i = 0, j = n - 1, mid;
    while(i <= j){
        mid = (i + j) / 2;
        if(q[mid] == key)
            return mid;
        else if(mid > key)
            j = mid - 1;
        else
            i = mid + 1;
    }
    return - 1;
}
```

查找效率分析与查找判定树

### 复杂度分析

查找判定树一定是平衡二叉树、二叉排序树，判定树只有最下面一层是不满的，树高$h = ⌈log_2(n+1)⌉$

查找效率ASL <= h，时间复杂度 = $O(lgn)$

## 分块查找

块内无序，块间有序

在索引表中确定待查记录所属的分块(顺序、二分)
在块内顺序查找