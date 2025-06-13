# quick_sort

- 分治
- 原址排序

````c++
void QuickSort(int q[], int l, int r){
    if(l >= r) return;
    int i = l , j = r ;
	// 基准数=左端点
    int x = q[l];
    while (i < j) {
        //交换方式：单个指针运动，交换
        
        while( i < j && q[j] >= x)
            j--;
        swap(a[i],a[j]);
        while( i < j && q[i] <= x)
            i--;
        swap(a[i],a[j]);
    }
    quick_sort(q, l, i - 1);quick_sort(q, i + 1, r);
}
````

不同代码区别：

- 基准选取
- 基准是否参与中途排序
    - 如果不参与，最后应该放到哪里
- 划分类型，小于等于和大于，小于和大于等于
- 划分区间
- 基准最后位置与递归关系

## 复杂度分析

最好时间复杂度：$O()$
平均时间复杂度：$O(nlogn)$
最差时间复杂度：$O(n^2)$

空间复杂度：$O(nlogn)$
是否稳定：不稳定

## 双指针交换

小于等于基准、基准、大于等于基准

1. 一个指针从左开始找到一个大于pivot的值，另一个指针从右开始找一个小于pivot的值，然后交换。
2. 重复上述过程，直到左右指针相遇
3. 将相遇点的元素与pivot值交换

```c++
void quick_sort(vector<int>& nums, int l, int r) {
    if (l >= r) return;
    
    int i = l, j = r;
    while (i < j) {
        while (i < j && nums[j] >= nums[l]) j--;
        while (i < j && nums[i] <= nums[l]) i++;
        swap(nums[i], nums[j]);
    }
    swap(nums[i], nums[l]);
    
    int i = partition(nums, l, r);
    quickSort(nums, l, i - 1);
    quickSort(nums, i + 1, r);
}
```

```c++
// acwing
void quick_sort(int q[], int l, int r)
{
    //递归的终止情况
    if(l >= r) return;

    //第一步：分成子问题
    int i = l - 1, j = r + 1, x = q[l + r >> 1];
    while(i < j)
    {
        do i++; while(q[i] < x);
        do j--; while(q[j] > x);
        if(i < j) swap(q[i], q[j]);
    }

    //第二步：递归处理子问题
    quick_sort(q, l, j), quick_sort(q, j + 1, r);

    //第三步：子问题合并.快排这一步不需要操作，但归并排序的核心在这一步骤
}
```



## 填坑

双指针，但是不同时移动

1. 保存枢纽值，例如最左，此时基准的位置为一个空的坑位
2. j指针找到一个小于基准的元素放到坑位中
3. i指针找到一个大于基准的元素放到坑位中
4. 直到左右指针相遇，将基准放入指针相遇的地方中

```c++
int partition(int q[], int l, int r)
{
    int x = q[l];
    int i = l, j = r;
    while (i < j)
    {
        while (i < j && q[j] >= x)
        {
            j--;
        }
        q[i] = q[j];
        while (i < j && q[i] <= x)
        {
            i++;
        }
        q[j] = q[i];
    }
    q[i] = x;
    return i;
}

void quick_sort(int q[], int l, int r)
{
    if (l >= r)
        return;
    int p = partition(q, l, r);
    quick_sort(q, l, p - 1);
    quick_sort(q, p + 1, r);
}
```

```c++
int Partition(int q[], int l, int r) {
    int i = l, j = r;
    int pivot = q[l];
    while (i < j) {
        /* 如果没有 i < j的限制, j遇到i之后，由于i之前保存的是大于等于基准数的值，
        循环继续，而i左边的数都是小于基准数的值, 不能再去修改这些已经归好位的值，因此必须加上i < j
        也就是说：小循环体内是会出现i >= j的情况的，虽然只会出现一次
        */
        while (q[j] >= pivot && i < j) {
            j++;
        }
        q[i] = q[j];
        while (q[i] < pivot && i < j) {
            i--;
        }
        q[j] = q[i];
    }
    q[i] = pivot;
    return i;
}

void QuickSort(int q[], int l, int r) {
    if (l >= r)
        return;
    int p = Partition(q, l, r);
    QuickSort(q, l, p - 1);
    QuickSort(q, p + 1, r);
}
```



## 算法导论

小于等于基准，基准，大于基准

循环不变量：

1. 若p <= k <= i,则A[k] <= x。
2. 若i+l <= k <= j-1,则A[k ]> x。
3. 若k=r,则A[k]=x。

> 循环不变量在第一轮迭代之前是成立的，并且在每一轮迭代后仍然都成立。在循环结束时，该循环不变量还可以为证明正确性提供有用的性质。
> 最坏情况
>
> 划分产生的两个子问题分别包含了n-l个元素和0个元素时

```c++
void quick_sort(int q[], int l, int r){
    if(l>=r) return;
    int i = l - 1, j = l;
    int x = q[r];
    for(j = l; j < r; j++){
        if(a[j] <= x){
            swap(a[++i], a[j]);
        }
    }
    // 将末尾基准数和第一个大于基准数的数字交换 即 i+1和r
    // 最终基准数落在 i+1 上，向两边分治
    swap(q[i+1], q[r])
    quick_sort(q, l, i);quick_sort(q, i+2, r);
}
```

````python
def quick_sort(a, l, r):
    if l >= r: return
    q = partition(a, l, r)
    quick_sort(a, l, q - 1)
    quick_sort(a, q + 1, r)


def partition(a, l, r):
    x = a[r]
    i = l - 1
    for j in range(l, r):
        if a[j] <= x:
            i += 1
            a[i], a[j] = a[j], a[i]
    a[i + 1], a[r] = a[r], a[i + 1]
    return i + 1
````



## tag1

确定基准，如 l
从l, r开始设立两个i, j指针
两个指针不同时移动，过程中保证一个指针指向空的位置，另一个指针指向待移动的位置
指针相遇时，所指向的位置为空???，将基准数放入





# todo

有大量重复元素的情况

边界问题可视化