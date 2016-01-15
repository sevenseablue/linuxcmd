# linuxcmd

[TOC]

- **awk 基本**
- **awk 函数**
- **awk 坑**

## awk 基本
```shell
cat file1
a 1
c 2

awk -F' ' 'BEGIN{}{print $2;}END{}' file1
1
2

```
格式     | 意义
-------- | ---
-F' '    | 读取file1文件，每读一行，使用-F' ' 设定空格为分隔符。
BEGIN{} | 括号内的代码在每次读文件之前执行
{}      | 括号内的代码在读文件的每一行执行一次
END{}   | 括号内的代码在处理完文件之后执行
