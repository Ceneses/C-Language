# C-language
C-Note-Summary
## 专题一-关键字的秘密
### 1.1数据类型&变量
```
* 数据类型可以理解为固定内存大小的别名
* 数据类型是创建类型的模子
```
```
* 变量是一段实际连续存储空间的别名
* 程序中通过变量来申请命名存储空间
* 通过变量的名字可以使用存储空间
```
* 自定义类型
* 自己创建变量
```
自定义数据类型 typedef 模子 TYPE 
创建变量      TYPE varName
验证结论       printf
```
![进程结构](https://github.com/Ceneses/C-language/blob/master/linux%E7%9A%84%E8%BF%9B%E7%A8%8B%E7%BB%93%E6%9E%84.png)
### 1.2 auto/static/register属性关键字
- auto 表明变量是在栈上分配空间的
- 全局变量是在程序静态区分配空间的
- static修饰的局部变量存储在程序静态区，生命是程序的运行期。
- static的另一个意义是文件作用域标示符，用static表示的变量和函数只作用在定义该变量或函数的文件中，其他文件不能用extern访问该变量。 
- static修饰的全局变量作用域只是声明的文件中。
- static修饰的函数作用域只是声明的文件中。
- register修饰的是寄存器的值
### 1.3 分支语句if/switch
- if 语句中bool型变量应该直接出现于条件中，不要进行比较
- 普通变量和0值比较时，0值应该出现在比较符号左边
- float型变量不能直接进行0值比较，需要定义精度
```
bool b =TRUE
if(b)
{
  //statement 1
}
else
{
  //statement 2
}

int i =1;
if(0==i)
{
  //statement 1
}
else
{
  //statement 2
}
#define EPSINON 0.00001
float f=0.0;
if((-EPSION<=f)&&(f<=EPISON))
{
//statement 1
}
else
{
//statement 2
}
```
## 专题二-符号的技巧
## 专题三-编译预处理
## 专题四-指针和数组
## 专题五-内存管理的艺术
## 专题六-函数
