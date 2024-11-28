# I/O

> 计算机组成原理

cpu<->北桥芯片<->内存总线<->内存

北桥芯片<->南桥芯片<->ISA总线

硬盘文件 文件系统：NTFS、APFS、
网络信号通过网卡等设备翻译为二进制信号

## 文件字节流

```java
// 繁琐的写法
try{
    // 打开文件的时候可能打不开
    FileInputStream stream = new FileInputStream("C:\\Users\\Genshinya\\Desktop\\test.txt");
} catch (FileNotFoundException e) {
    e.printStackTrace
    
} finally {
    if(stream !=null){
        try {
            // 关闭文件的时候可能发生IO异常
            stream.close();
        } catch (IOException e){
            throw new RuntimeException(e);
        }
    }
    stream.close();
}
// 语法糖简化写法
try (FileInputStream stream = new FileInputStream("C:\\Users\\Genshinya\\Desktop\\test.txt");) {
    int i;
    while((i = stream.read()) != -1)
    //每次调用read方法，返回一个字节的内容，并且指针后移一个字节，如果读到底了，返回-1
    System.out.printl((char) i);

    byte[] bytes = new byte[100];
    while (stream.read(bytes) != -1) // 一次性将字节流读入固定大小的数组
        System.out.println(new String(bytes));

    byte[] string = new byte[stream.available]
    stream.read(string);
    System.out.println(new String(string));
} catch (IOException e) {
    e.printStackTrace();
}
```
