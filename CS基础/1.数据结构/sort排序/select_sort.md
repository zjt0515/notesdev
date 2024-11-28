# 选择排序

## 简单选择排序

- 不稳定
- 原址排序

## 复杂度分析

最好时间复杂度：$O()$
平均时间复杂度：$O(n^2)$
最差时间复杂度：$O(n^2)$

空间复杂度：$O(1)$
是否稳定：不稳定

## 算法代码

i = 0..n-2
j = i...n-1

一共n-1轮，每次比较 n-1-i+1次

#### c++

```c++
void SelectSort(int q[], int length)
{

    for (int i = 0; i < length - 1; i++)
    {
        int min = i;

        for (int j = i + 1; j < length; j++)
        {
            if (q[j] < q[min])
            {
                min = j;
            }
        }
        int tmp = q[i];
        q[i] = q[min];
        q[min] = tmp;
    }
}
```

#### python

```python
def select_sort(a):
    for i in range(0, len(a) - 1):
        min = i
        // 找到最小，之后交换操作，因此必须存储索引
        for j in range(i, len(a) - 1):
            if a[j] < a[min]:
                min = j
        a[i], a[min] = a[min], a[i]


if __name__ == '__main__':
    a = [1, 1, 4, 5, 1, 4]
    select_sort(a)
    print(a)
```



## 堆排序