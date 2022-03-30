# 【C语言】笔记

## 1.计算机和编程语言

### 1.1第一个C程序

1、程序框架

```c
#include <stdio.h>

int main()
{
    return 0;
}
```

2、输出

- printf("Hello World!\n");
- ""里面的东西是字符串，printf会把其中的内容原封不动输出
- \n表示在输出结果后面换一行

3、程序中的错误

编译器会给出提示

4、不用中文输入
5、可移植 C/C++（C标准除文件操作外没有操作系统硬件资源接口，Windows Linux接口不一样）
   跨平台 Java python

### 1.2 关于那个0

0与o不一样，0中间有斜杠

### 1.3 Mac OS X如何在命令行编辑、编译、运行C程序

```c
gcc hello.c       //编译C程序
ls -l             //显示编译过程
./a.out           //运行，./是Linux中的一种安全命令
```

### 1.4 计算

```c
#include <stdio.h>

int main()
{
    printf("%d\n",23+43)           //%d说明后面有一个整数要输出在这个位置上
    printf("23+43=%d\n",23+43)    
    return 0;
}
```

### 1.5 四则运算

| 四则运算 | C符号 |
| --- | --- |
| + | + |
| - | — |
| x | * |
| ➗ | / |
| （） | （） |

%表示取两个数相除以后的余数

### 1.6 main()的样子

- return主要是为了告诉电脑程序运行结束，不返回给用户。
- void main()表示主函数没有返回值，可以不加return；加了return，表示程序结束不继续往下执行；return 0会报错。所有标准均不认可该写法
- int main()表示主函数返回值为整型，返回一个值看是否为0来判断程序是否正常退出（返回值整型有取值范围，过大会导致程序报错），该种写法在C99和C11标准中不被允许。
- int main(void)为标准写法

### 1.7 VS使用、及编译
1、system("pause");    让窗口停留
2、程序变为exe经过两步，一步是编译，一步链接


## 2.数据类型、运算符与表达式

### 2.1 数据类型
（1） 
 - 基本类型：整型int、字符型char、实型（浮点型）可分为单精度和双精度
 - 构造类型：数组【】、结构型struct、联合union、枚举enum
 - 指针类型*
 - 空类型void
  
(2) C语言的关键字
[C语言中的关键字](https://zhuanlan.zhihu.com/p/37908790)
    
[C语言的关键字](https://blog.csdn.net/21aspnet/article/details/1539252?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0.opensearchhbase&spm=1001.2101.3001.4242.1)
    
### 2.2 常量
- 整型        1
- 实型        3.12
- 字符型       ‘2’
- 字符串型     “”是个空串

### 2.3 变量
（1）需要：

- 有地方放输入的数字
- 有办法输入数字
- 输入的数字参与计算

（2）change.c

```c
change.c

#include <stdio.h>
int main()
{
int price = 0;                       //这一行定义了一个变量，变量名是price，类型是int，初始值是0。
printf("请输入金额（元）：");
scanf ("%d",&price);               //输入是以行为单位进行的，行的结束标志是你按下了回车键。在你按下回车键之前，你的程序不会读到任何东西。
int change = 100 - price;
printf("找您%d元。\n",change);
return 0;
}
```

变量的作用：变量是一个保存数据的地方，保存了数据，才能参加到后面的计算中

（3）变量定义的一般形式       <变量类型> <变量名称>；

int price；int amount；int price，amount；

（4）标识符

构造基本原则：只能由字母、数字和下划线组成，数字不可以出现在第一个位置上，C语言关键字（保留字）不可以用作标识符

- C语言的保留字
    
    [C语言中32个关键字详解](https://zhuanlan.zhihu.com/p/37908790)
    
    [C语言的关键字](https://blog.csdn.net/21aspnet/article/details/1539252?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0.opensearchhbase&spm=1001.2101.3001.4242.1)
    
（5）C语言区分大小写的，变量先定义后使用、见名知意

### 2.4 整型数据
#### 2.4.1 符号常量
```c
#include <stdio.h>
#define PI 3    //PI就是符号常量
int main()
{
    int a=3;
    a=5;
    //PI=4;    //符号常量不可赋值
    printf("%d\n",PI)
}
```

#### 2.4.2 整型常量的不同进制
  [进制转换](http://c.biancheng.net/view/1725.html)
- 二进制与八进制的转换
 将二进制数每三位转换为一位八进制数，最后在前面加一个0
- 二进制与十进制的转换
 把二进制字符串从最高位（左边第一位）开始用商乘以2再加余数（该位的数字），如此循环，左边第一位的商肯定是0；
 把十进制除2取余数，并把所有的余数倒排，不够八位在前面加0。
- 二进制与十六进制的转换
  四位计算，高位不足补0
内存使用十六进制 （x86架构是小端存储，低位在前，高位在后）
```c
#include <stdio.h>
int main()
{
    //int i=123;
    int i=0x7b;
    printf("%d\n",i);       //%d表示以十进制方式输出某一个整型数
}
```
1 位 1 bit
1字节 1 byte = 8 bit
1Kb = 1024 字节
1Mb = 1024Kb
地址是4个字节
int i 是4个字节 

使用scanf时一定要用取地址符&

### 2.5 浮点型数据
#### 2.5.1 浮点型常量float
- 小数形式 0.123
- 指数形式 3e-3（e之前必须有数字，e后面的指数只能为整数）
```c
#include<stdio.h>
int main()
{
    float f = 1.234;    //e代表10的幂次
    printf("%f\n",f);   //%f就是以浮点形式输出对应数据
}
```

#### 2.5.2 浮点型变量
- 通过float f 来定义浮点变量，f占用4个字节的空间

### 2.6 字符型数据
#### 2.6.1 字符型常量
- 用单引号扩起来的一个字符，且只能包含一个字符！   例：'a' '1' ' '
- 以\开头的特殊字符称为转义字符 \n换行   \b退格   \\\反斜杠

#### 2.6.2 字符数据在内存中的存储形式及其使用方法
```c
#include<stdio.h>
int main()
{
    float f = 1.234;    //e代表10的幂次
    printf("%f\n",f);   //%f就是以浮点形式输出对应数据
    char c = 'a';
    printf("%c\n",c);
}
```
ASCII码表
![](https://picgo-1302188000.cos.ap-nanjing.myqcloud.com/img/ascii码.png)

```c
#include<stdio.h>
int main()
{
    char c = 'a';
    c = c-32;         //把小a变成大A
    printf("%c\n",c);
}
```

### 2.7 字符串型常量
- 字符串型常量是由一对双引号括起来的字符序列
- ‘a'和“a”不一样
- 不可将字符串型常量赋值给字符型变量，如:
  ```c
  char c;   c = "China";
  ```
- C语言中没有定义字符串型常量的关键字，用字符数组存放字符串
- C语言规定以字符'\0'作为字符串结束标志，以便系统判断
- "CHINA"在内存中占用六个内存单元，而不是五个，由于\0的存在
- ‘\0' == 0



### 2.8 混合运算
#### 2.8.1 类型强制转换
```c
#include<stdio.h>
int main()
{
    int i = 5;
    float j = i /2;       // i/2是整型计算，得到2，float f =2.0
    float k = （float）i/2;     //float()i将它变成浮点型运算
    printf("j=%f,k=%f\n",j,k);
}
```




### 2.9 常用的数据输入/输出函数
#### 2.9.1 scanf函数的原理
- C语言通过函数库读取标准输入
```c
 #include <stdio.h>
  int scanf( const char *format,...);    //format 是一个字符， ...是一个可变参数，参数的数目与format中%的数目保持一致
  format里面可以有%d %f %c，不限制出现次数
  ```

#### 2.9.2 scanf函数的循环读取
 ```c
#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
//清空缓冲区，VS2012 fflush(stdin),VS2017- VS2019rewind是新接口取代fflush
//stdin是标准输入
int main()
{
    int i,ret;
    while(rewind(stdin),(ret=scanf("%d",&i))!= EOF)     //while实现循环，后面要有小括号
    {
        printf("i=%d\n",i);
    }
    return 0;
}
```
- scanf循环读取发生错误时，返回EOF
- #define EOF    (-1)
- 出错的情况：在行首输入ctrl+z回车，连续三次就出错了，退出控制框, Mac结束循环按一次command+d

```c
#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
int main()
{
    char c;
    while(scanf("%c",&c)!= EOF)     //while实现循环，后面要有小括号
    {
        if (c!= '\n')
        {
            printf("%c",c-32);
        }
        else {
            printf("\n");
        }
    }
    return 0;
}
```


#### 2.9.3 多种数据类型混合输入
```c
#include<stdio.h>
int main()
//一个scanf读多种类型的数据
//混合输入时，每次在%c前面加入一个空格
{
    int i;
    float f;
    char c;
    scanf("%d %c%f",&i,&c,&f);
    printf("i=%d,c=%c,f=%f\n",i,c,f);
    return 0;
}
```
#### 2.9.4 printf函数介绍
- 原理与scanf差不多
```c
#include<stdio.h>
//printf控制输出格式
int main()
{
    printf("name=%s,age=%3d,sex=%c,score=%4.1f\n","moovgen",34,'m',98.5);
}
```
#### 2.9.5 getchar函数
#### 2.9.6 putchar函数



### 2.10 运算符与表达式
#### 2.10.1 运算符分类
- 单目运算符
- 双目运算符
#### 2.10.2 算术运算符及表达式
先乘除、取模，后加减
```c
#include<stdio.h>
int main()
{
int a =1234;

    while(a!=0)
    {
        printf("%d",a%10);
        // printf("%c",a+48);数字变字符
        a=a/10;
    }
    printf("\n");
    return 0;
}
```
#### 2.10.3 关系运算符与关系表达式
关系表达式的值只有真和假，C语言没有布尔类型，真就是1，假就是0；
```c
#include<stdio.h>
int main()
{
    int a = 2;
    if(a>3 && a<10)
    {
        printf("a is right");
    }
    else{
        printf("a is wrong");
    }
    return 0;
}
```
```c
//判断两个浮点数是否相等
#include<stdio.h>
int main()
{
    float f=234.56;
   // if(f==234.56)      //无法判断,必须用下面的方法
   if(f-234.56 > -0.0001 && f-234.56 < 0.0001)
    {
        printf("f is equal to 234.56\n");
    }
    else{
        printf("f is not equal to 234.56\n");
    }
}
```
#### 2.10.4 逻辑运算符与逻辑表达式
- ！ 逻辑非，如果原来是真，取非就是假，如果是假，取非就是真
- && 逻辑与，任何一个为假，就是假，都为真，才是真
- || 逻辑或，一个为真即为真，二者皆假，才是假
- 短路运算：对0取非为一，对非0值取非，值为0
#### 2.10.5 赋值运算符
- 等号左边必须是变量
a=a/3    a/=3
#### 2.10.6 条件运算符与逗号运算符
```c
逗号表达式
while(rewind(stdin),(ret=scanf("%d",&i))!=EOF)
\\先运行前面的，后运行后面的，整体表达式的值为逗号后面的值，后面的为真，整体则为真
```
#### 2.10.7 自增、自减运算符及求字节运算符
```c
#include<stdio.h>
int main()
{
    int i = -1;
    int j;
    i++;  //代表的是i=i+1;
    j=i++>-1;     //拆解成两步 j=i>-1;i++
    j=++i>-1;     //++i直接按优先级进行正常运算
    printf("i=%d,j=%d\n",i,j);
    printf("i的字节数=%d\n",sizeof(i));
    return 0;
}
```


## 3.选择与循环
### 3.1 选择结构程序设计
#### 3.1.1 关系表达式与逻辑表达式
- 算术运算符的优先级高于关系运算符，关系运算符的优先级高于逻辑与和逻辑或运算符

#### 3.1.2 if语句
- if里边99%是放关系表达式、逻辑表达式，剩余的1%的情况，直接放入一个值
- if括号后面不可以分号，若加了分号，下面的语句体就与if无关了，无论表达式真假，都会走下面的语句体；
- else不能单独出现，else子句从属于最靠近它的不完整的if语句

### 3.2 循环结构程序设计
#### 3.2.1 while循环
```c
#include<stdio.h>
int main()
{
    int i = 1;
    int total = 0;
    while(i<=100)        //while语句括号后面不能加分号，语句内要有趋近条件，否则会死循环
    {
        total = total + i;
        i++;
    }
    printf("1到100的和为%d",total);
    return 0;
}
```
#### 3.2.2 for循环
```for(表达式1；表达式2；表达式3)语句```
- （1）先求解表达式1
- （2）求解表达式2，若为真，执行内嵌语句，求解表达式3，执行（3）；若为假，跳出循环
- （3）回到（2）继续执行
 ```c
#include<stdio.h>
int main()
{
    int i,total;
    for(i=1,total=0;i<=100;i++)  //for语句一定要有两个分号
    {
        total=total+i;
    }
    printf("total=%d",total);
    return 0;
}
```

#### 3.2.3 continue语句
- 提前结束本轮循环
```c
#include<stdio.h>
int main()
{
    for(i=1,total=0;i<=100;i++)
    {
        if(i%2==0)     //如果i是偶数
        {
            continue;  //提前结束本轮循环，直接回到i++
        }
        total=total+i;
    }
    printf("total=%d\n",total);
    return 0;
}
 ```
#### 3.2.4 break语句
- 直接终止循环
 ```c
#include<stdio.h>
int main()
{
    int i,total;
    for(i=1,total=0;i<=100;i++)
    {
        if(total>2000)
        {
            break;
        }
        total =total+i;
    }
    printf("total=%d",total);
    return 0;
}
 ```




## 4.一维数组与字符数组
### 4.1 一维数组
#### 4.1.1 数组的定义
- 整型、浮点型数据占4个字节；字符型占1个字节
- 一组具有相同数据类型的数据的有序集合就是数组
- 数组名的命名规则和变量名相同，方括号中的常量表示数组中元素的个数，即数组长度
- 常量表达式中有可能是常量，也有可能是符号常量,但不能是变量，C语言不允许对数组的大小做动态定义，即数组不依赖于程序运行过程中变量的值
- 定义数组的一瞬间，数组占据的空间大小就确定下来了
- 数组可以只对部分元素赋值，未赋值的元素都是0
定义格式：``` int a[10];   类型说明符 数组名[常量表达式]```
 ```c
#include<stdio.h>
#define N 5
int main()
{
    int a[5]={1,3,5,7,9};
    //int i=5;
    //int a[i];不可用
    int b[N]={2,4,6,8,0};
}
```


#### 4.1.2 一维数组在内存中的存储
语句 ```int mark[100]``` 定义的每个元素都是整型数据，占用4个字节，访问数组 mark中元素的方式是mark[0]、mark[1]···mark[99],每个数据元素占用的字节，就是基类型的字节数
访问越界
```c
#include<stdio.h>

//打印数组里的每个元素,数组在传递时，元素个数传递不过去
void print(int b[],int len)     //b和len是形参
{
    int i;
    for(i=0;i<len;i++)
    {
        printf("b[%d]=%d\n",i,b[i]);
    }
    b[4]=20;    //在子函数中修改数组元素的值
    printf("sizeof(b)=%d\n",sizeof(b));    //数组作为参数传递时，退化为指针，32位下用数组名的sizeof是4个字节，64位是8个字节
}
int main()
{
    int j = 10;
    int a[5]={1,2,3,4,5};
    int i = 3;
    //a[5]=20;     //访问越界会覆盖掉前面的变量，访问了不属于自己的空间
    //a[6]=21;
    //a[7]=22;     //该步改变了j的值
    printf("j=%d\n",j);
    printf("sizeof=%d\n",sizeof(a));
    print(a,4);     //a是实参
    printf("a[4]=%d",a[4]);    //实际程序中的值也被修改了
}
```

### 4.2 字符数组
#### 4.2.1 字符数组的定义及初始化
字符数组格式 ```char c[10]``` ,用来存字符串的
```c
#include<stdio.h>
int main()
{
    //char c[5]={'h','e','l','l','o'};//这样写在32位系统下打印会有烫烫烫等乱码，因为后面没有\0终止
    char c[6]={'h','e','l','l','o'};//数组长度改为6时，最后一个会自动赋值0，可以终止
    char d[10]={"hello"};
    char e[5]="how";
    printf("%s----%s\n",c,e);   //printf的%s，对应后面要写的是字符数组名，或者是字符串
    char f[20],g[20];
    scanf("%s%s",f,g);
    printf("%s---%s",f,g);

}
```
- C语言规定字符串的结束标志时'\0'，要人为的在字符数组中添加'\0',所以字符数组存储的字符串长度必须比字符数组少一字节，例如char c[10]最多存储9个字符


#### 4.2.2 字符数组的传递
```c
#include<stdio.h>
void print(char d[])
{
    int i = 0;
    while(d[i]!='\0')
    {
        printf("%c",d[i]);
        i++;
    }
    printf("\n");
    d[0]=d[0]-32;
}
int main()
{
    char c[10]="hello";
    print(c);
    printf("%s",c);
    return 0;
}
```

#### 4.2.3 gets函数和puts函数
- scanf通过%s读取字符串时，当遇到空格以后，就会匹配结束，无法将一行带有空格的字符串存入到一个字符数组，此时我们需要gets来实现
- puts只能输出字符串，printf能输出各种类型数据
- 格式 ```char *gets(char *str)```    ```int puts(char *str)```
```c
#include<stdio.h>
int main()
{
    char c[20];   //字符数组的数组名里存的就是字符数组的起始地址，&c[0]==c，类型是字符指针,c是一个字符数组，但是编译器给c内部存了一个值（字符指针）
    gets(c);    //当一次读取一行时，使用gets
    puts(c);    //等价于("%s\n",c)
}
```

#### 4.2.4 str系列字符串操作函数
```c
#include<stdio.h>
#include<string.h>
int main()
{
    char c[20]="wangdao";
    printf("数组c内字符串的长度=%d\n",strlen(c));
    char d[20];
    //char *strcpy(char* to,const char* from) 有const修饰代表这个地方可以放一个字符串常量
    strcpy(d,c);    
    char e[20];
    strcpy(e,"study");
    puts(d);
    puts(e);
    //strcmp  char *strcmp(const char* str1,const char* str2)两个字符串比较，是比较对应字符位置的ascii码值
    printf("两个字符串比较后的结果=%d\n",strcmp(c,d));
    //strcat char *strcat(char* str1,const char* str2)拼接两个字符串
    strcat(c,e);   //将e放到c中，要求c+e<=c定义的的大小
    puts(c);
    return 0;
}
```

## 5.指针
### 5.1 指针的本质
#### 5.1.1 指针的定义
- 如果在一个程序中定义了一个变量，那么在对程序进行编译时，系统会给这个变量分配内存单元
- 按变量地址存取变量值的方式称为“直接访问”，如：printf、scanf等
- 另一种存取变量值的方式称为“间接访问”，即将变量i的地址存放到另一个变量中
- C语言中，指针变量用来存放变量地址
格式 ```int *i_pointer;```
```c
#include<stdio.h>
int main()
{
    int i = 5;
    //指针变量的初始化一定是某个变量取地址
    int *i_pointer=&i;
}
```

#### 5.1.2 取地址操作符与取值操作符
- 取地址操作符是&，也叫引用,通过该操作符，我们可以获取一个变量的地址；取值操作符为*，也称解引用，通过该操作符我们可以得到一个地址对应的数据
>
```c
#include<stdio.h>
int main()
{
    int i=5;
    int *p=&i;
    printf("i=%d\n",i);  //直接访问
    printf("*p=%d\n",*p);//间接访问
    return 0;
}
```
### 5.2 指针的使用场景
#### 5.2.1 指针的传递
**函数调用原理**
```c
#include<stdio.h>
#include<stdlib.h>
//void change(int &j)       加上取地址符后第二句打印出来就是5
void change(int j){
    j=5;
}
int main(){
    int i = 10;           //i是局部变量
    printf("before change is %d\n",i);
    change(i);            //（C值传递）函数调用时，把i叫做实参，赋值给j，改变j的值，i不受影响
    printf("after change is %d\n",i);
    return 0;
}
```
```c
#include<stdio.h>
#include<stdlib.h>
//void change(int &j)       
void change(int *j){
    *j=5;                 //指针的间接传递
}
int main(){
    int i = 10;           //i是局部变量
    printf("before change is %d\n",i);
    change(&i);            
    printf("after change is %d\n",i);
    return 0;
}
```


#### 5.2.2 指针的偏移
- 指针的偏移就是对地址进行加减
```c
#include<stdio.h>
int main()
{
    int a[5]={1,2,3,4,5};  //数组名a类型是一个数组，a里边存了一个值，是地址值，是数组的起始地址
    int* p;   //对一个指针变量进行取值，得到的类型是其基类型
    p=a;
    printf("*p=%d\n",*p);
    for(int i=0;i<5;i++)
    {
        printf("%d\n",*(p+i));
    }
    return 0;
}
```

#### 5.2.3 指针与自增、自减运算符
```c
#include<stdio.h>
int main()
{
    int a[3]={2,7,8};
    int *p;
    int j;
    p=a;  //让指针变量p指向数组的开头
    j=*p++;  //j=*p;p++,任何时候都是把后加加去掉，然后看另外一个运算符优先级是否高于加加
    //j=(*p++);此时值为3 2 3
    printf("a[0]=%d,j=%d,*p=%d\n",a[0],j,*p);
    j=p[0]++;
    printf("a[0]=%d,j=%d,*p=%d\n",a[0],j,*p);  //2 7 8
}
```
#### 5.2.4 指针与一维数组
```c
#include<stdio.h>
//数组名作为实参传递给子函数时，是弱化为指针的
void change(char *d)
{
    *d='H';
    d[1]='E';
    *(d+2)='L';
}
int main()
{
    char c[10]="hello";
    change(c);
    puts(c);
}
```
#### 5.2.5 指针与动态内存申请
- 数组一开始定义好就确定下来了，是存放在栈空间中的
程序是放在磁盘上的有序的指令集合，程序启动起来才叫进程
我们定义的整型变量i，指针变量p都在main函数的栈空间中，通过malloc申请的空间会返回一个堆空间的首地址，我们把首地址存入变量p，通过strcpy函数往对应的空间存储字符数据
>栈是计算机系统提供的数据结构，计算机会在底层对栈提供支持：分配专门的寄存器存放栈的地址，压栈操作、出栈操作都有专门的指令执行，这就决定了栈的效率比较高；

>堆则是C/C++函数库提供的数据结构，他的机制很复杂，例如为了分配一块内存，库函数会按照一定的算法在堆内存中搜索可用的足够大小的内存空间，如果没有足够的，就会调用系统功能去增加程序数据段的内存空间，这样就有机会分到足够大小的内存，然后返回，效率比栈空间低很多。

void什么都不需要返回
void*
**动态内存申请**
```c
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
int main()
{
    int i;      //申请多大的空间
    scanf("%d",&i);
    char *p;
    p=(char*)malloc(i);   //malloc申请空间的单位是字节，(char*是为了强制类型转换，不进行转换会有警告)
    strcpy(p,"malloc success");
    puts(p);
    free(p);   //释放空间,p的值必须和最初malloc返回的值一致
    p=NULL;    //u如果不把p值设为NULL，把p称为野指针
}
```

**堆空间与栈空间的区别**
```c
#include<stdio.h>
char *print_stack()
{
    char c[]="i am print_stack";
    puts(c);
    return c;
}
char *print_malloc(){
    char *d=(char*)malloc(30);
    strcpy(d,"i am print_malloc");
    puts(d);
    return d;
}
int main(){
    char *p,*p1;
    p=print_stack();//栈空间会随着函数的执行结束而释放
    puts(p);     //打印出来的是乱码，因为上面print_stack的栈空间被释放了
    p1=print_malloc()； //堆空间不会随子函数的结束而释放
    puts(p1)
    return 0;
}
```

#### 5.2.6 字符指针与字符数组的初始化
>用一个字符指针变量指向一个字符串时，只可读，不可写

```c
#include<stdio.h>
#include<string.h>
int main(){
    char *p="hello";      //字符串全部存储在字符串常量区（数据区），只可读不可写
    char c[10]="hello";   //等价于strcpy(c,"hello")，将hello字符串都存放到了自己的栈空间内
    //c[0]='H';     
    printf("c[0]=%c\n",c[0]);
    printf("p[0]=%c\n",p[0]);
    p="world";     //将字符串world的地址赋值给p，p是一个字符指针，是一个可改变的地址
    c="world";     //非法，c是数组名，存放的是最开始字符数组的初始地址，已经定义好了，不可改，相当于是一个常量
    return 0;
}
```
### 5.3 二级指针
>一级指针的使用场景是传递与偏移，服务于整型变量、浮点型变量、字符型变量等。（修改主函数中变量，使用一级指针）。二级指针只服务于一级指针的传递与偏移。
二级指针初始化一定是某个一级指针的取地址
int *p1;
p2=&p1;
#### 5.3.1 二级指针的传递
```c
#include<stdio.h>
void change(int **pi,int *pj){
    *pi=pj;
}
int main(){
    int i=10;
    int j=5;
    int *pi;
    int *pj;
    pi=&i;
    pj=&j;
    printf("i=%d,j=%d,*pi=%d,*pj=%d",i,j,*pi,*pj);
    change(&pi,pj);
    printf("i=%d,j=%d,*pi=%d,*pj=%d",i,j,*pi,*pj);
}
```

## 6.函数
### 6.1 函数的声明、定义与调用
#### 6.1.1 函数的声明与定义
>函数的定义：指对函数功能的确立，包括指定函数名、函数值类型、形参及其类型、函数体等，它是一个完整的、独立的函数单位。
函数的声明：把函数的名字、函数类型及形参的类型、个数和顺序，通知编译系统，以便在调用该函数时，编译系统能正确识别函数并检查调用是否合法。

#### 6.1.2 函数的分类
- 无参函数：用来执行指定的一组操作，主调函数不向被调用函数传递数据
- 有参函数：主调函数通过参数向被调用函数传递数据
在不同函数之间传递数据时，可以使用以下的方法：
（1）参数：通过形式参数和实际参数
（2）返回值：用return语句返回计算结果。
（3）全局变量：外部变量，存放在数据区的，若与局部变量同名，则采取就近原则
```c
#include<stdio.h>
    int i=10; //全局变量，
    void print(int a){
        printf("print i=%d\n",i);
    }
    int main(){
        printf("main i=%d\n",i);
        // i=5;
        // print(i);
        int i=5;  //这里加了int后，就是在main里面定义了一个名为i的局部变量，局部变量是存放在自己的栈空间里的
        print(i);
    }
```
- 定义函数中所指定的形参，如果函数没有调用，她们并不占用内存单元。只有发生函数调用时，它们才会被分配内存单元。函数调用结束后，形参所占据的内存单元也会被释放。
- 实参可以使常量、变量或表达式，但要求他们有确定的值比如print(i+3)，不可用print(i,i++)，因为C标准未规定函数调用是从左到右计算还是从右到左计算。
- 形参类型必须指定，实参与形参按顺序对应，一一传递数据
- 实参与形参类型应相同或赋值兼容。
- 实参与形参的数据传递是单向“值传递”
- 形参相当于局部变量，因此不能再定义局部变量与形参同名

### 6.2 递归调用
- 递归就是函数自己调用自己
```c
#include<stdio.h>
//函数在函数中自己调用自己
int f(int n){
    if (n==1){
        return 1; //一定要写结束条件
    }
    return n*f(n-1); //首先写好公式
}
int main(){
    int n=5;
    int result=f(n);
    printf("result=%d\n",result);
}
```

## 6.3 变量及函数的作用域
### 6.3.1 局部变量与全局变量
- 内部函数中不能有名称相同的局部变量，形参也是一种局部变量






