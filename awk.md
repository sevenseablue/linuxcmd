##<a name="index"/>目录
* [基本](#基本)
* [函数](#函数)
* [坑](#坑)
* [经典](#经典)

###<a name="基本"/>基本
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



###<a name="函数"/>函数

```shell

awk -F' ' 'function fun(arr){return arr[1]+arr[2];}BEGIN{}{print $2;}END{}' file1
1
2

```


###<a name="坑"/>坑
1. 没有not的语法 所以  if (i not in array) 是错误的，可以用 if(!(i in array))来替代


###<a name="经典"/>经典
```

awk -F'\t' -v f1=$file1 -v f2=$file2 -v f3=$file3 -v f4=$file4 -v f41=$file41 -v f42=$file42 -v f43=$file43 '
function fileDict(fd_file,fd_delim,fd_ki,fd_vi,fd_u){
  while(getline fd_x<fd_file>0){split(fd_x,fd_a,fd_delim);fd_u[fd_a[fd_ki]]=fd_a[fd_vi];};
}
function dic_get(dictmp1, keytmp1, default_v_1){if(keytmp1 in dictmp1) return dictmp1[keytmp1];else return default_v_1;}
BEGIN{
  fileDict(f1,"\t",1,2,dic1);fileDict(f2,"\t",1,2,dic2);
  fileDict(f3,"\t",1,2,dic3);fileDict(f4,"\t",1,2,dic4);
  fileDict(f41,"\t",1,2,dic41);fileDict(f42,"\t",1,2,dic42);fileDict(f43,"\t",1,2,dic43);
  for(i in dic1){
    CONVFMT="%0.2f";
    num3=dic_get(dic3, i, 0);
    num4=dic_get(dic4, i, 0);
    print i,dic1[i],dic2[i],num3,num3/dic2[i]*100"%",num4,num4/dic2[i]*100"%",dic_get(dic41,i,0),dic_get(dic42,i,0),dic_get(dic43,i,0);
  }
}
'

```
