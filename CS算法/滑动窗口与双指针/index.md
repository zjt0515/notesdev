# 滑动窗口

1. 确定窗口是定长还是变长
    1. 定长，只需要确定一个端点就可以`r, l = r - k + 1, out `

https://leetcode.cn/circle/discuss/0viNMK/

## 基础题

按照整体顺序

1. 元素不断进入窗口，直到窗口被元素填满
2. 更新答案
3. 元素出口

```js
// 模板
double res = Integer.MIN_VALUE;
double current = 0;
for (int i = 0; i < nums.length; i++) {
    in();
    if (i + 1 < k) continue;
    res = Math.max(res, current);
    out();
}
return res;
```

1. 注意更新答案的位置：一般是在满足最佳答案操作之后立即执行
2. 元素进入一般是一个一个进入，出去一般是一个或多个出去

## 求Min

### [209. 长度最小的子数组](https://leetcode.cn/problems/minimum-size-subarray-sum/)

> 初始化的角度：[0,r] 恰好满足条件
>
> 右端点先动，左端点后动，[l,r]总是满足条件
>
> 在左端点移动后，更新答案求最小

```java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int n = nums.length;
        int res = n + 1;
        for (int r = 0, l = 0, sum = 0; r < n; r++) {
            // 右端点向右移动，直到满足条件：sum >= target
            sum += nums[r];
            if (sum < target) continue;
            // 左端点向右移动，直到 sum
            while (l < r) {
                if (sum - nums[l] >= target) {
                    sum -= nums[l++];
                } else {
                    break;
                }
            }
            if (sum >= target) {
                res = Math.min(res, r - l + 1);
            }
        }
        return res <= n ? res : 0;
    }
}
```

### [1234. 替换子串得到平衡字符串](https://leetcode.cn/problems/replace-the-substring-for-balanced-string/)

```java
class Solution {
    public int balancedString(String s) {
        Map<Character, Integer> map = new HashMap<>();
        map.put('Q', 0);
        map.put('W', 0);
        map.put('R', 0);
        map.put('E', 0);
        char[] ss = s.toCharArray();
        int res = Integer.MAX_VALUE;
        int n = ss.length;
        int m = n / 4;
        for (char c : ss) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        if(map.get('Q') == m && map.get('W') == m && map.get('E') == m && map.get('R') == m) return 0;
        for (int r = 0, l = 0; r < ss.length; r++) {
            // 寻找子串：子串之外的元素个数不超过n/4
            map.put(ss[r], map.get(ss[r]) - 1);
            // 缩短子串，如果当前元素都<=m，就尝试缩短
            // 此时，更新答案必须在缩短之前进行，因为缩短后不一定符合条件
            while(map.get('Q') <= m && map.get('W') <= m && map.get('R') <= m && map.get('E') <= m){
                res = Math.min(res, r-l+1);
                map.put(ss[l], map.get(ss[l]) + 1);
                l++;
            }
        }
        return res;
    }
}
```

## 求和Sum

### [713. 乘积小于 K 的子数组](https://leetcode.cn/problems/subarray-product-less-than-k/)

```java
class Solution {
    public int numSubarrayProductLessThanK(int[] nums, int k) {
        int n = nums.length;
        int res = 0;
        if (k <= 1) return 0;
        for (int r = 0, l = 0, sum = 1; r < n; r++) {
            // 右端点向右移动，右端点枚举保证了答案不会少
            sum *= nums[r];
            // 不满足条件，左指针移动
            if (sum >= k) {
                while (l < r) {
                    sum /= nums[l++];
                    if (sum < k) {
                        break;
                    }
                }
            }
            // 满足条件， 更新答案
            // 这行代码是每次右端点移动后，无论左端点是否移动，都要执行的
            if (sum < k)
                res += r - l + 1;
        }
        return res;
    }
}
```

## 求Max

### [3. 无重复字符的最长子串](https://leetcode.cn/problems/longest-substring-without-repeating-characters/)

思路

1. 移入元素
    1. 判断是否窗口内是否已经存在重复元素
        1. 存在，窗口缩小，直到不存在重复元素
        2. 重新将移入元素添加到窗口
    2. 更新答案值

```java
class Solution {
    public int lengthOfLongestSubstring(String S) {
        Set<Character> set  = new HashSet<>();
        char[] s = S.toCharArray();
        int n = s.length;
        int res = 0;
        for(int r = 0, l = 0; r < n; r++){
            while(set.contains(s[r])){
                set.remove(s[l++]);
            }
            set.add(s[r]);
            res = Math.max(res, r-l+1);
        }
        return res;
    }
}
```





