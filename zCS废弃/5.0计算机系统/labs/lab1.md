判断一个二进制数是否和另一个二进制数相等：`!(x^y)`

## bitAnd

```c
int bitAnd(int x, int y)
{
   // 德摩根定律
   return ~(~x | ~y);
}
```

![image-20240408135228028](./images/image-20240408135228028.png)

## tmin

```c
int tmin(void)
{
   // 最小的二进制补码数是1000....0000
   return 0x01 << 31;
}
```

## isZero

```c
int isZero(int x)
{
   // 直接取逻辑反
   return !x;
}
```



## isTmin

> 
>


```c

```

~0+1 -> 0
其他数按位取反+1，符号位必然不同

利用了补码中+0和-0的表示方式相同

## allOddBits

```c
int allOddBits(int x)
{
   int allOdd1_16 = 0xAA + (0xAA << 8);
   int allOdd1_32 = allOdd1_16 + (allOdd1_16 << 16);
   int OddBits_x = allOdd1_32 & x;
   return !(OddBits_x ^ allOdd1_32);
}
```



## negate

```c
int negate(int x)
{
   return ~x + 1;
}
```



## isNotEqual

```c
int isNotEqual(int x, int y)
{
   return !!(x ^ y);
}
```



## isAsciiDigit

```c
int isAsciiDigit(int x)
{
   int is3 = !((x >> 4) ^ 0x3);
   int last4 = x & 0xf;
   int from0to9 = !((0x9 + (~last4 + 1)) >> 31);
   return is3 & from0to9;
}
```



## conditional

```c
int conditional(int x, int y, int z)
{
   x = ~(!x) + 1;             // 如果x为0，x就为0xff，反之则为0x00
   return (y & ~x) | (za & x); // x为0，用0xff & z取出z的值，用0x00 & y使|另一边全为0
}
```



## bitMask

```c
int bitMask(int highbit, int lowbit)
{
   int x = ~0;
   int high = x << highbit << 1;
   int low = x << lowbit;
   return (high ^ low) & low;
}
```



## logicalNeg

> 
>
> **示例 1:**
>
> 输入: 114514
> 输出: 0
> 解释: 只要x不为0，!x的结果为0
>
> **示例 2:**
>
> 输入: 0
> 输出: 1
> 解释: !0，结果为1

```c
int logicalNeg(int x)
{
   return (((~x + 1) | x) >> 31) + 1;
}
```



原理：0取反+1是1，1000取反+1

## bitParity

```c
int bitParity(int x)
{
   x ^= x >> 16;
   x ^= x >> 8;
   x ^= x >> 4;
   x ^= x >> 2;
   x ^= x >> 1;
   return x & 1;
}
```



含有奇数个0，返回1
含有偶数个0，返回0

解析：若有奇数个0，那么1的个数也是奇数个，这里称含有奇数个0/1称为二进制奇数，含有偶数个0/1称为二进制偶数，^不改变一个数的奇偶性

^：相同返回0，不同返回1

0x10101010

## absVal

```c
int absVal(int x)
{
   int isNeg = x >> 31;
   isNeg = ~(!isNeg) + 1;
   return ((~x + 1) & ~isNeg) | (x & isNeg);
}
```



## floatScale2

## floatFloat2Int

## floatPower2