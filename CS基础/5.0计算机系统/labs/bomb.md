## phase_4

[csapp-bomblab 详解 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/410409223)

? 4

```shell
b explode_bomb
b phase_4
b func4
r ans.txt
```



```shell
x/s ($rsp)
\003
```

第一个数<=e

<img src="./images/image-20240519133318005.png" alt="image-20240519133318005" style="zoom: 67%;" />

rsi存储第2个数、rcx存储第二个数

```asp
00000000004017a2 <phase_4>:
  4017a2:       f3 0f 1e fa             endbr64
  4017a6:       48 83 ec 18             sub    $0x18,%rsp
  4017aa:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  4017b1:       00 00
  4017b3:       48 89 44 24 08          mov    %rax,0x8(%rsp)
  4017b8:       31 c0                   xor    %eax,%eax
  4017ba:       48 8d 4c 24 04          lea    0x4(%rsp),%rcx
  4017bf:       48 89 e2                mov    %rsp,%rdx
  4017c2:       48 8d 35 4c 1c 00 00    lea    0x1c4c(%rip),%rsi        # 403415 <array.0+0x235>
  4017c9:       e8 52 fb ff ff          call   401320 <__isoc99_sscanf@plt>
  # 检查输入参数是否为2个
  4017ce:       83 f8 02                cmp    $0x2,%eax
  4017d1:       75 06                   jne    4017d9 <phase_4+0x37>
  # 检查什么？
  4017d3:       83 3c 24 0e             cmpl   $0xe,(%rsp)
  4017d7:       76 05                   jbe    4017de <phase_4+0x3c>
  4017d9:       e8 74 06 00 00          call   401e52 <explode_bomb>
  4017de:       ba 0e 00 00 00          mov    $0xe,%edx
  4017e3:       be 00 00 00 00          mov    $0x0,%esi
  4017e8:       8b 3c 24                mov    (%rsp),%edi
  4017eb:       e8 71 ff ff ff          call   401761 <func4>
  # 检查eax不等于4或者非零？
  4017f0:       83 f8 04                cmp    $0x4,%eax
  4017f3:       75 07                   jne    4017fc <phase_4+0x5a>
  
  4017f5:       83 7c 24 04 04          cmpl   $0x4,0x4(%rsp)
  4017fa:       74 05                   je     401801 <phase_4+0x5f>
  4017fc:       e8 51 06 00 00          call   401e52 <explode_bomb>
  401801:       48 8b 44 24 08          mov    0x8(%rsp),%rax
  401806:       64 48 2b 04 25 28 00    sub    %fs:0x28,%rax
  40180d:       00 00
  40180f:       75 05                   jne    401816 <phase_4+0x74>
  401811:       48 83 c4 18             add    $0x18,%rsp
  401815:       c3                      ret
  401816:       e8 55 fa ff ff          call   401270 <__stack_chk_fail@plt>
```

### 可读性

```asp
00000000004017a2 <phase_4>:
  4017a2:       f3 0f 1e fa             endbr64
  4017a6:       48 83 ec 18             sub    $0x18,%rsp
  4017aa:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  4017b1:       00 00
  4017b3:       48 89 44 24 08          mov    %rax,0x8(%rsp)
  4017b8:       31 c0                   xor    %eax,%eax
  4017ba:       48 8d 4c 24 04          lea    0x4(%rsp),%rcx
  4017bf:       48 89 e2                mov    %rsp,%rdx
  4017c2:       48 8d 35 4c 1c 00 00    lea    0x1c4c(%rip),%rsi        # 403415 <array.0+0x235>
  4017c9:       e8 52 fb ff ff          call   401320 <__isoc99_sscanf@plt>
  # 检查输入参数是否为2个
  4017ce:       83 f8 02                cmp    $0x2,%eax
  4017d1:       75 06                   jne    4017d9 <phase_4+0x37>
  # 检查
  4017d3:       83 3c 24 0e             cmpl   $0xe,(%rsp)
  4017d7:       76 05                   jbe    4017de <phase_4+0x3c>
  4017d9:       e8 74 06 00 00          call   401e52 <explode_bomb>
  4017de:       ba 0e 00 00 00          mov    $0xe,%edx
  4017e3:       be 00 00 00 00          mov    $0x0,%esi
  4017e8:       8b 3c 24                mov    (%rsp),%edi
  4017eb:       e8 71 ff ff ff          call   401761 <func4>
  # 检查eax不等于4
  4017f0:       83 f8 04                cmp    $0x4,%eax
  4017f3:       75 07                   jne    4017fc <phase_4+0x5a>
  
  4017f5:       83 7c 24 04 04          cmpl   $0x4,0x4(%rsp)
  4017fa:       74 05                   je     401801 <phase_4+0x5f>
  4017fc:       e8 51 06 00 00          call   401e52 <explode_bomb>
  401801:       48 8b 44 24 08          mov    0x8(%rsp),%rax
  401806:       64 48 2b 04 25 28 00    sub    %fs:0x28,%rax
  40180d:       00 00
  40180f:       75 05                   jne    401816 <phase_4+0x74>
  401811:       48 83 c4 18             add    $0x18,%rsp
  401815:       c3                      ret
  401816:       e8 55 fa ff ff          call   401270 <__stack_chk_fail@plt>
```

### func4

![image-20240519133229001](./images/image-20240519133229001.png)

```c
func4(edx = 14, esi = 0, edi = rsp(第一个数字7)){
  eax=edx=14;!!!!!!
  //eax-=esi;!!!!!!
  ecx=eax=14;
  
  ecx>>31; // ecx = 0;
  ecx+=eax;// ecx = 14;
  ecx/=2;  // ecx = 7;
+34:
  ecx+=esi;// ecx = 7
  if(edi > ecx){// 如果第一个数字大于7
    goto +39
  }
  if(edi < ecx){
    goto +51
  } 
  if(edi == ecx){
    return
  }
+39:
  edx = rcx - 1;
  func4(edx,esi,edi);
  eax+=eax;!!!!!
  jmp +34;
+51:
  esi = rcx+1;
  func4(edx,esi,edi);
  eax=rax...;
  goto +34;
  
}
```



```asp
0000000000401761 <func4>:
  4017de:       ba 0e 00 00 00          mov    $0xe,%edx
  4017e3:       be 00 00 00 00          mov    $0x0,%esi
  4017e8:       8b 3c 24                mov    (%rsp),%edi
  401761:       f3 0f 1e fa             endbr64
  401765:       48 83 ec 08             sub    $0x8,%rsp  ; rsp=8-rsp
  401769:       89 d0                   mov    %edx,%eax  ; eax = edx
  40176b:       29 f0                   sub    %esi,%eax  ; eax=esi-eax
  40176d:       89 c1                   mov    %eax,%ecx  ; ecx = eax
  40176f:       c1 e9 1f                shr    $0x1f,%ecx ; ecx/=2
  401772:       01 c1                   add    %eax,%ecx  ; ecx+=eax
  401774:       d1 f9                   sar    %ecx       ; ecx/=2???
  401776:       01 f1                   add    %esi,%ecx  ; ecx+=esi
  401778:       39 f9                   cmp    %edi,%ecx
  ; if(edi>ecx)
  40177a:       7f 0c                   jg     401788 <func4+0x27> #edi>ecx
  40177c:       b8 00 00 00 00          mov    $0x0,%eax # eax=0
  ; if(edi<ecx)
  401781:       7c 11                   jl     401794 <func4+0x33>
  401783:       48 83 c4 08             add    $0x8,%rsp
  401787:       c3                      ret
  401788:<func4+0x27>       8d 51 ff                lea    -0x1(%rcx),%edx
  40178b:       e8 d1 ff ff ff          call   401761 <func4>
  401790:       01 c0                   add    %eax,%eax
  401792:       eb ef                   jmp    401783 <func4+0x22>
  401794:       8d 71 01                lea    0x1(%rcx),%esi
  401797:       e8 c5 ff ff ff          call   401761 <func4>
  40179c:       8d 44 00 01             lea    0x1(%rax,%rax,1),%eax
  4017a0:       eb e1                   jmp    401783 <func4+0x22>
```

```c
int func4(int edi, int esi, int edx)
{
    int eax = edx - esi;
    if (eax < 0)
      eax -= 1;
    eax /= 2;

    int ecx = eax + esi;
    if (ecx > edi)
        return func4(edi, esi, ecx - 1) * 2;
    else if (ecx < edi)
        return func4(edi, ecx + 1, edx) * 2 + 1;
    else
        return 0;
}
```







## phase_5

sabres

7 1 13 6 5 7

gamfeg

https://blog.csdn.net/Wangzhyy/article/details/78720514

```asp

000000000040181b <phase_5>:
  40181b:       f3 0f 1e fa             endbr64
  40181f:       53                      push   %rbx
  401820:       48 83 ec 10             sub    $0x10,%rsp
  401824:       48 89 fb                mov    %rdi,%rbx
  401827:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  40182e:       00 00
  401830:       48 89 44 24 08          mov    %rax,0x8(%rsp)
  401835:       31 c0                   xor    %eax,%eax
  401837:       e8 06 03 00 00          call   401b42 <string_length>
  40183c:       83 f8 06                cmp    $0x6,%eax
  40183f:       75 55                   jne    401896 <phase_5+0x7b>
  401841:       b8 00 00 00 00          mov    $0x0,%eax
  401846:       48 8d 0d 93 19 00 00    lea    0x1993(%rip),%rcx        # 4031e0 <array.0>
  40184d:       0f b6 14 03             movzbl (%rbx,%rax,1),%edx
  401851:       83 e2 0f                and    $0xf,%edx
  401854:       0f b6 14 11             movzbl (%rcx,%rdx,1),%edx
  401858:       88 54 04 01             mov    %dl,0x1(%rsp,%rax,1)
  40185c:       48 83 c0 01             add    $0x1,%rax
  401860:       48 83 f8 06             cmp    $0x6,%rax
  401864:       75 e7                   jne    40184d <phase_5+0x32>
  401866:       c6 44 24 07 00          movb   $0x0,0x7(%rsp)
  40186b:       48 8d 7c 24 01          lea    0x1(%rsp),%rdi
  401870:       48 8d 35 3f 19 00 00    lea    0x193f(%rip),%rsi        # 4031b6 <_IO_stdin_used+0x1b6>
  401877:       e8 e7 02 00 00          call   401b63 <strings_not_equal>
  40187c:       85 c0                   test   %eax,%eax
  40187e:       75 1d                   jne    40189d <phase_5+0x82>
  401880:       48 8b 44 24 08          mov    0x8(%rsp),%rax
  401885:       64 48 2b 04 25 28 00    sub    %fs:0x28,%rax
  40188c:       00 00
  40188e:       75 14                   jne    4018a4 <phase_5+0x89>
  401890:       48 83 c4 10             add    $0x10,%rsp
  401894:       5b                      pop    %rbx
  401895:       c3                      ret
  401896:       e8 b7 05 00 00          call   401e52 <explode_bomb>
  40189b:       eb a4                   jmp    401841 <phase_5+0x26>
  40189d:       e8 b0 05 00 00          call   401e52 <explode_bomb>
  4018a2:       eb dc                   jmp    401880 <phase_5+0x65>
  4018a4:       e8 c7 f9 ff ff          call   401270 <__stack_chk_fail@plt>
```

## phase_6

6 3 4 5 1 2

1 4 3 2 6 5
