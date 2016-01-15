##<a name="index">目录
* [基本](#基本)


###<a name="基本">基本
```
  grep -iEv "a.*b" file1
```
找出不区分大小写，正则匹配，不匹配的行

```
  grep -AB 5 "a.*b" file1
```
前后5行
