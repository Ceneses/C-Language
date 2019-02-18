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
```
指针的*号
在指针声明的时候：*号所声明的变量是指针
在指针使用的过程中：*号是读取内存空间的值
```
```
//another file
char *p="HelloWorld";
//test.c
extern char p[];
printf("%s\n",(char*)(*((unsigned int*)p)));
```
## 专题五-内存管理的艺术[转自知乎链接](https://zhuanlan.zhihu.com/p/55241632)
![C语言内存模型图](https://github.com/Ceneses/C-language/blob/master/C%E8%AF%AD%E8%A8%80%E5%86%85%E5%AD%98%E6%A8%A1%E5%9E%8B.jpg)
### 5.1 C语言运行区域
- 内存大致分为四个数据区：常量区,全局数据区(静态区),堆区，栈区
- **常量区**
> 存储了未被作为初始化使用的字符串常量和const修饰的全局变量,特点是只能读不能写,受到操作系统运行时保护，强行修改会导致 segmentation fault，生命周期同程序运行过程。
```
/* 字符串 "hello world" 存在字符串常量区, 
 指针 str 本身存储在全局数据区或者栈上(函数内) */
char *str = "hello world";
```
- **全局数据区**
> 存储了全部的全局变量，和所有被 static 修饰的变量（包括全局和局部），其特点是生命周期很长（为一次程序的运行过程）并且只被初始化一次。
```
int global = 2;   // 存在全局数据区   
int main(int argc, char *argv[]){ 
      static int static_global = 1; // 静态局部变量也是存在全局数据区    
      int local = 2;                //  存在栈上，见下   
      return 0;
}
```
- **栈区**
> 存储了所有自动存储（不加任何存储类型关键字( static 等)修饰或被 auto 修饰）的局部变量，其特点是生命周期很短，仅仅是该变量所在函数的一次调用过程, 函数被调用时被自动分配并在函数返回后回收
```
// num 和 localnum都是分配在栈上   
int func(int num){      
     int localnum = -1;     
     return localnum * num;   
} 
```
> 很多 C/C++ 初学者容易犯的一个错误就是返回局部变量的指针或者指针，但是这个指针所指向的局部变量在函数返回后就会被自动回收(退栈)。所以当对返回的局部变量的指针被dereference时也会发生无法预料的错误。
- **堆区**
> 是由操作系统负责维护的大片内存池，使用时需手动申请, 一般是调用 malloc 家族函数进行动态内存分配，但使用完毕后需要使用 free 手动释放，否则会造成严重的内存泄漏。所有分配的内存当该进程退出后就会被操作系统回收，但是对于需要长期运行的服务器程序来说，就必须保证内存泄漏尽量少(完全没有基本不可能，除非程序很简单)。
```
int *p = (int*)malloc(100 * sizeof(int));   
for(int i = 0; i < 100; i++){ 
        p[i] = i;      
}  
free(p);
p = NULL;
```
## 专题六-函数
## 专题七-C库说明
> **stdlib.h**
```
定义基本输入/输出函数
```
> **string.h**
```
定义字符串处理函数
```
> **float.h**
```
定义浮点数处理函数
```
> **stdlib.h**
```
定义杂项函数及内存分配处理函数
```
> **math.h**
```
定义基本数学处理函数
```
> **ctype.h**
```
定义对字符的处理函数
```
## 专题八-优先级问题
```
！ > 算术运算符 > 关系运算符 > && > || > 赋值运算符
```
