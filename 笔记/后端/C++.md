# C++基础

## 1 c++初识

### 1.1 第一个C++程序 HelloWorld!

1. 创建项目

2. 创建文件

3. 编写代码

   ```C++
   #include<iostream>
   using namespace std;
   
   int main(){
   
       cout << "HelloWorld!" << endl;
   
       system("pause");
   
       return 0;
   }
   ```

4. 编译执行

### 1.2 注释

- 单行注释

  ```C++
  // 单行注释
  ```

- 多行注释

  ```C++
  /*
   * 多行注释
   */
  ```

### 1.3 变量

**作用：**给一段内存起名，便于操作这块内存

**变量的创建：**`变量类型 变量名 = 初始值;`

```C++
int a = 10;
```

### 1.4 常量 

**作用：**用于记录程序中不更改的数据

定义常量的两种方式：

1. **#define宏常量**：`#define 常量名 常量值`
   - 通常在文件上方定义，表示一个常量
2. **const修饰的变量**：`const 数据类型 常量名 = 常量值;`
   - 通常在变量定义前加关键字const，修饰该变量为一个常量，不可修改

```C++
#include<iostream>
using namespace std;

#define DAY 7
int main() {
    cout << "一周有" << DAY << "天" << endl;

    const int day = 365;
    cout << "一年有" << day << "天" << endl;

    system("pause");
    return 0;
}
```



### 1.5 关键字

作用：关键字是C++中预先保留的单词(标识符)

- 在定义变量或常量的时候不要使用关键字

### 1.6  标识符命名规则

- 标识符不可以是关键字
- 标识符由字母、数字、下划线组成
- 标识符第一个字符只能是字母或下划线
- 标识符区分大小写

## 2 数据类型

C++明确规定在创建变量或常量前必须指出数据类型，否则无法分配内存。

数据类型的意义：给变量分配合适的内存空间。

### 2.1 整型

**作用:**整型变量表示的是整数类型的数据。

C++中能够表示整型的类型有以下几种，**区别在于所占内存空间不同**：

| 数据类型  | 占用空间                                       | 取值范围       |
| --------- | ---------------------------------------------- | -------------- |
| short     | 2字节                                          | (-2^15~2^15-1) |
| int       | 4字节                                          | (-2^31~2^31-1) |
| long      | windows为4字节,Linux为4字节(32位)，8字节(64位) | (-2^31~2^31-1) |
| long long | 8字节                                          | (-2^63~2^63-1) |

### 2.2 sizeof关键字

**作用**：利用sizeof关键字可以统计数据类型所占内存大小

**语法**：`sizeof (数据类型 / 变量)`

```C++
#include<iostream>
using namespace std;

int main() {
    cout << sizeof(short) << endl;	  // 2
    cout << sizeof(int) << endl;	  // 4
    cout << sizeof(long) << endl;	  // 4
    cout << sizeof(long long) << endl;// 8
    system("pause");
    return 0;
}
```

### 2.3 实型(浮点型)

**作用**:用于表示小数

浮点型变量分为两种：

- 单精度浮点数 float
- 双精度浮点数 double

两者的区别在于表示的有效数字范围不同。默认情况下输出都为6位有效数字。

| 数据类型 | 占用空间 | 有效数字范围    |
| -------- | -------- | --------------- |
| float    | 4字节    | 7位有效数字     |
| double   | 8字节    | 15~16位有效数字 |

**科学计数法**：3e5 = 3*10^5

```C++
#include<iostream>
using namespace std;
int main()
{
    float f1 = 1.11111111f;
    double d1 = 1.11111111111;
    cout << "float:" << f1 << endl;	// 1.11111
    cout << "double:" << d1 << endl;// 1.11111

    cout << "float占用内存空间：" << sizeof(float) << endl;// 4
    cout << "double占用内存空间：" << sizeof(double) << endl;// 8
    // 科学计数法
    float e = 3e2;
    cout << "3e2" << e << endl; // 300
    system("pause");
    return 0;
}
```

### 2.4 字符型

**作用：**字符型变量用于显示单个字符

**语法：**`char ch = 'a';`

> 1、在现实字符型变量时，用单引号将字符括起来，不要用双引号
>
> 2、单引号内只能有一个字符，不可以是字符串

- C和C++字符型变量只占用1个字节
- 字符型变量并不是把字符本身放到内存中储存，而是将对应的ASCII编码放到存储单元

### 2.5 转义字符

**作用**：用于表示一些不能显示出来的ASCII字符

|      |            |      |
| ---- | ---------- | ---- |
| \n   | 换行       |      |
| \t   | 水平制表符 |      |
| \\   | 反斜杠 \   |      |

### 2.6 字符串型

**作用：**用于表示一种字符

**两种风格**：

1. **C风格字符串**：`char 变量名[] = "字符串值"`

2. **C++风格字符串**：`string 变量名 = "字符串值"`

   > 需要引入头文件 #include<string>

```C++
string str = "C++风格字符串";
char string1[] = "C风格字符串";
```

### 2.7 布尔型 bool

**作用**：布尔型表示真或假

**bool类型只有两个值**：

- true	真(本质是1)

- false   假(本质是0)

  > 在输入时 只要是非0的值都代表真

**bool类型占1个字节大小**

```C++
#include<iostream>
using namespace std;

int main(){
    bool flag = true;
    cout << flag << endl; // 1
    flag = false;
    cout << flag <<endl; // 0

    cout << "布尔类型大小：" << sizeof(bool) << endl; // 1
    return 0;
}
```

### 2.8 数据的输入

**作用**：用于从键盘获取数据

**关键字**：cin

**语法：**`cin >> 变量名`

```C++
#include<iostream>
#include<string>

using namespace std;

int main() {
    //整型数据输入
    int a = 0;
    cout << "a的值为:\t\t" << a << endl;
    cout << "请修改a的值：\t";
    cin >> a ;
    cout << "您输入的值是：\t" << a << endl;
    //浮点型数据输入
    float f = 0.001f;
    cout << "f的值为:\t\t" << f << endl;
    cout << "请修改f的值：\t";
    cin >> f ;
    cout << "您输入的值是：\t" << f << endl;
    //char 型数据输入
    char c = 'a';
    cout << "c的值为:\t\t" << c << endl;
    cout << "请修改c的值：\t";
    cin >> c ;
    cout << "您输入的值是：\t" << c << endl;
    //字符串类型数据输入
    string str = "abcd";
    cout << "str的值为:\t\t" << str << endl;
    cout << "请修改str的值：\t";
    cin >> str ;
    cout << "您输入的值是：\t" << str << endl;
    //bool 型数据输入
    bool flag = true;
    cout << "flag的值为:\t\t" << flag << endl;
    cout << "请修改flag的值：\t";
    cin >> flag ;
    cout << "您输入的值是：\t" << flag << endl;
    return 0;
}
```

## 3 运算符

**作用：**用于执行代码的运算

**运算符类型：**

| 运算符类型 | 作用                                   |
| ---------- | -------------------------------------- |
| 算术运算符 | 用于处理四则运算                       |
| 赋值运算符 | 用于将表达式的值赋给变量               |
| 比较运算符 | 用于表达式的比较，并返回一个真值或假值 |
| 逻辑运算符 | 用于表达式的值返回真值或假值           |

### 3.1 算术运算符

**作用：**用于处理四则运算

算术运算符包含以下符号：

| 运算符 | 术语       | 示例       | 结果     |
| ------ | ---------- | ---------- | -------- |
| +      | 正号       | +3         | 3        |
| -      | 负号       | -3         | -3       |
| +      | 加         | 1+2        | 3        |
| -      | 减         | 2-1        | 1        |
| *      | 乘         | 2*3        | 6        |
| /      | 除         | 6/3        | 2        |
| %      | 取模(取余) | 10%3       | 1        |
| ++     | 前置递增   | a=2;b=++a; | a=3;b=3; |
| ++     | 后置递增   | a=2;b=a++; | a=3;b=2; |
| --     | 前置递减   | a=2;b=--a; | a=1;b=1; |
| --     | 后置递减   | a=2;b=a--  | a=1;b=2; |

> 两个小数不能做取模运算

```C++
#include<iostream>
using namespace std;

int main(){
    int a,b;
    a = 5;
    b = 2;
    cout << "a=" << a << ";b=" << b << endl;
    //四则运算
    cout << "a+b=" << a+b <<endl;
    cout << "a-b=" << a-b <<endl;
    cout << "a*b=" << a*b <<endl;
    cout << "a/b=" << a/b <<endl;
    //取模
    cout << "a%b=" << a%b << endl;
    cout << "---------------------------" << endl;
    //前置自增
    a = 2;
    cout << "a=" << a << endl;
    b = ++a;
    cout << "a=" << a << endl;
    cout << "++a=" << b << endl;
    //后置自增
    a = 2;
    cout << "a=" << a << endl;
    b = a++;
    cout << "a=" << a << endl;
    cout << "a++=" << b << endl;
    //前置自减
    a = 2;
    cout << "a=" << a << endl;
    b = --a;
    cout << "a=" << a << endl;
    cout << "--a=" << b << endl;
    //后置自减
    a = 2;
    cout << "a=" << a << endl;
    b = a--;
    cout << "a=" << a << endl;
    cout << "a--=" << b << endl;
    //浮点数相除
    double d1 = 3.3;
    double d2 = 1.111;
    cout << d1 / d2 << endl;
    return 0;
}

```

### 3.2 赋值运算符

**作用：**用于将表达式的值赋给变量

赋值运算符包含以下几个符号：

| 运算符 | 术语   | 示例      | 结果     |
| ------ | ------ | --------- | -------- |
| =      | 赋值   | a=2;b=3;  | a=2;b=3; |
| +=     | 加等于 | a=0;a+=2; | a=2;     |
| -=     | 减等于 | a=5;a-=3; | a=2;     |
| *=     | 乘等于 | a=2;a*=3; | a=6;     |
| /=     | 除等于 | a=4;a/=2; | a=2;     |
| %=     | 模等于 | a=3;a%=2; | a=1;     |

### 3.3 比较运算符

**作用：**用于表达式的比较，并返回一个真值或假值

比较运算符包含以下符号：

| 运算符 | 术语     | 示例 | 结果 |
| ------ | -------- | ---- | ---- |
| ==     | 相等于   | 4==3 | 0    |
| !=     | 不等于   | 4!=3 | 1    |
| <      | 小于     | 4<3  | 0    |
| >      | 大于     | 4>3  | 1    |
| <=     | 小于等于 | 4<=3 | 0    |
| >=     | 大于等于 | 4>=3 | 1    |

### 3.4 逻辑运算符

**作用：** 用于根据表达式的值返回真值或假值

逻辑运算符包含以下符号：

| 运算符 | 术语 | 示例   | 结果                                                     |
| ------ | ---- | ------ | -------------------------------------------------------- |
| !      | 非   | !a     | 如果a为假,则!a为真;如果a为真,则!a为假。                  |
| &&     | 与   | a&&b   | 如果a和b都为真，则结果为真，否则为假。                   |
| \|\|   | 或   | a\|\|b | 如果a和b至少一个为真，则结果为真；二者都为假，结果为假。 |

## 4 程序流程结构

C/C++支持最基本的三种程序运行结构：`顺序结构、选择结构、循环结构`

- 顺序结构：程序按顺序执行，不发生跳转。
- 选择结构：依据条件是否满足。有选择的执行相应的功能。
- 循环结构：依据条件是否满足，循环多次执行某段代码。

### 4.1 选择结构

#### 4.1.1 if语句

**作用：**执行满足条件的语句。

if语句的三种形式：

- 单行格式if语句

- 多行格式if语句

- 多条件的if语句

  

1. **单行格式if语句：**`if(条件){条件满足执行的语句}`
   
   ```flow
   st=>start: 开始
   cond=>condition: 判断条件
   sub1=>subroutine: 执行程序
   e=>end: 结束
   st->cond
   cond(true)->sub1->e
   cond(false)->e
   ```
   
2. **多行格式if语句：**`if(条件){条件满足执行的代码}else{条件不满足执行的代码}`

   ```flow
   st=>start: 开始
   cond=>condition: 判断条件
   sub1=>subroutine: 执行语句1
   sub2=>subroutine: 执行语句2
   e=>end: 结束
   st->cond
   cond(true)->sub1->e
   cond(false)->sub2->e
   ```

   

3. **多条件的if语句(级联)：**`if(条件1){条件一满足执行的语句}else if(条件2){条件2满足执行的语句} ...else{以上条件都不满足执行的语句}`

   ```flow
   st=>start: 开始
   cond1=>condition: 判断条件1
   cond2=>condition: 判断条件2
   cond3=>condition: ......
   condn=>condition: 判断条件n
   sub1=>subroutine: 执行语句1
   sub2=>subroutine: 执行语句2
   sub3=>subroutine: 执行语句3
   sub4=>subroutine: 执行语句4
   sub5=>subroutine: 执行语句5
   e=>end: 结束
   st->cond1
   cond1(true)->sub1->e
   cond1(false)->cond2
   cond2(true)->sub2->e
   cond2(false)->cond3
   cond3(true)->sub3->e
   cond3(false)->condn
   condn(true)->sub4->e
   condn(false)->sub5->e
   ```

4. **嵌套if语句：**在if语句中，可以嵌套使用if语句，达到更精确的条件判断。

#### 4.1.2 三目运算符

**作用：**通过三目运算符实现简单的判断

**语法：**`表达式1 ? 表达式2 : 表达式3`

**解释：**

> 如果表达式1的值为真，执行表达式2，并返回表达式2的结果；
>
> 如果表达式1的值为假，执行表达式3，并返回表达式3的结果。

> 三目运算符返回的是变量，可以继续赋值。

```C++
#include<iostream>

using namespace std;

int main() {
    int a = 10, b = 20;
    cout << "a:" << a << endl; //10
    cout << "b:" << b << endl; //20
    cout << "-----------------" << endl;
    cout << "(a>b?a:b):" << (a > b ? a : b) << endl;//20
    cout << "a:" << a << endl; //10
    cout << "b:" << b << endl; //20
    cout << "-----------------" << endl;
    cout << "((a>b?a:b)=100):" << ((a > b ? a : b) = 100) << endl;//100
    cout << "a:" << a << endl;//20
    cout << "b:" << b << endl;//100
    return 0;
}
```

#### 4.1.3 选择结构

**作用：**执行多条分支语句

**语法：**

```C++
switch(表达式)
{
    case 结果1:执行语句;break;
    case 结果2:执行语句;break;
    ......
    default:执行语句;break;
}
```

> switch 语句中的表达式类型只能是整型或字符型

> case里如果没有break，那么程序会一直向下执行

> 总结：与if语句相比，对于多条件判断时，Switch的结构清晰，执行效率高，缺点是switch不可以判断区间

### 4.2 循环结构

#### 4.2.1 while循环语句

**作用：**满足循环条件，执行循环语句

**语法：**`while(循环条件){循环语句}`

**解释：**只要循环条件的结果为真，就执行循环语句

```flow
st=>start: 开始
cond=>condition: 循环条件
sub1=>subroutine: 执行语句
e=>end: 结束
st->cond
cond(true)->sub1->cond
cond(false)->e
```

**示例：**

```C++
#include<iostream>
using namespace std;
int main(){
    int n = 0;
    while(n<10){
        cout << n << endl;
        n++;
    }
    return 0;
}
```

> 注意：在执行循环语句的时候，程序必须提供跳出循环的出口，否则出现死循环

#### 4.2.2 do...while循环语句

**作用：**满足循环条件，执行循环语句

**语法：**`do{循环语句}while(循环条件)`

**注意：**与while的区别在于do...while会先执行一次循环语句，再判断循环条件

```flow
st=>start: 开始
cond=>condition: 循环条件
sub1=>subroutine: 循环语句
e=>end: 结束
st->sub1->cond
cond(true)->sub1
cond(false)->e
```

#### 4.2.3 for循环语句

**作用：**满足循环条件，执行循环语句

**语法：**`for(起始表达式;条件表达式;末尾循环体){循环语句}`

**执行顺序：**起始表达式->条件表达式->循环语句->末尾循环体->条件表达式->...

```C++
#include<iostream>
using namespace std;
// 从0打印到9
int main() {
    for (int i = 0; i < 10; i++) {
        cout << i << endl;
    }
    return 0;
}
```

> 注意：for循环中的表达式，要用分号进行分割，

> 总结：while,do...while,for 都是常用的循环语句，for循环结构比较清晰比较常用

#### 4.2.4 嵌套循环

**作用：**在循环体中再嵌套一层循环，解决一些实际问题

**示例：**

```C++
#include<iostream>
using namespace std;
int main() {
    // 外层循环
    for (int i = 0; i < 10; i++) {
        // 内层循环
        for (int j = 0; j < 10; j++) {
            cout << "* ";
        }
        cout << endl;
    }
    return 0;
}
```

### 4.3 跳转语句

#### 4.3.1 break语句

**作用：**用于跳出选择结构或者循环结构

break使用的时机:

- 出现在switch条件语句中，作用是种植case并跳出switch
- 出现在循环语句中，作用是跳出当前的循环语句
- 出现在嵌套循环中，跳出最近的内层循环语句

```C++
#include<iostream>
using namespace std;

int main() {
    cout << "请选择副本难度：" << endl;
    cout << "1-简单难度" << endl;
    cout << "2-困难难度" << endl;
    cout << "3-地狱难度" << endl;

    int select = 0;
    cin >> select;

    switch (select) {
        case 1:
            cout << "您选择的是简单难度！" << endl;
            break;
        case 2:
            cout << "您选择的是困难难度！" << endl;
            break;
        case 3:
            cout << "您选择的是地狱难度！" << endl;
            break;
        default:
            cout << "默认" << endl;
            break;
    }
    return 0;
}
```

#### 4.3.2 continue语句

**作用：**在循环语句中，跳过本次循环中余下尚未执行的语句，进入下一次循环

**实例：**

```C++
#include<iostream>
using namespace std;

int main() {
    for (int i = 0; i < 10; i++) {
        if(i==5){
            continue;
        }
        cout << i << endl;
    }
    return 0;
}
```

> 注意：continue不会终止整个循环，而break会跳出循环

#### 4.3.3 goto语句

**作用：**可以无条件跳转语句

**语法：**`goto标记`

**解释：**如果标记的名称存在，执行到goto语句，会跳转到标记的位置

**示例：**

```C++
#include <iostream>
using namespace std;

int main() {
    cout << "1.xxxxx" << endl;
    cout << "2.xxxxx" << endl;
    goto Flag; // goto 标记
    cout << "3.xxxxx" << endl;// 不再执行
    cout << "4.xxxxx" << endl;// 不再执行
    Flag://标记
    cout << "5.xxxxx" << endl;
    cout << "6.xxxxx" << endl;
    return 0;
}
```

> 注意：程序中不建议使用goto语句，以免造成程序流程混乱

## 5 数组

### 5.1 概述

> 所谓数组，就是一个存放了很多相同类型数据元素的集合

**特点1：**数组中每个数据元素都是相同的数据类型

**特点2：**数组是由连续的内存位置组成的

### 5.2 一维数组

#### 5.2.1 一维数组的定义方式

一维数组的三种定义方式：

1. `数据类型 数组名[数组长度];`
2. `数据类型 数组名[数组长度] = {值1,值2,....};`
3. `数据类型 数组名[] = {值1,值2,....};`

> 注意：数组下标从0开始

> 总结：数组命名规范与变量命名规范一致，不要和变量重名

```C++
#include <iostream>

using namespace std;

int main() {
    // 第一种数组定义方式
    int num1[5];
    // 按数组下标赋值
    num1[0] = 10;
    num1[1] = 20;
    num1[2] = 30;
    num1[3] = 40;
    num1[4] = 50;
    // 按数组下标输出
    for (int i = 0; i < 5; i++) {
        cout << num1[i] << endl;
    }
    // 第二种数组定义方式
    int num2[5] = {10, 20, 30, 40, 50};
    for (int i = 0; i < 5; i++) {
        cout << num2[i] << endl;
    }
    // 第三种数组定义方式
    int num3[] = {10, 20, 30};
    for (int i = 0; i < 3; i++) {
        cout << num3[i] << endl;
    }
    return 0;
}
```

#### 5.2.2 一维数组数组名

一维数组名称的用途：

1. 可以统计整个数组在内存中的长度
2. 可以获取数组在内存中的首地址

```C++
#include <iostream>
using namespace std;

int main() {

    int arr[] = {10, 20, 30};
    // 可以统计整个数组在内存中的长度
    cout << "数组在内存中的长度：" << sizeof(arr) << endl;
    cout << "数组第一个元素在内存中的长度：" << sizeof(arr[0]) << endl;
    cout << "数组元素个数：" << sizeof(arr) / sizeof(arr[0]) << endl;
    // 可以获取数组在内存中的首地址
    cout << "数组在内存中的首地址:" << arr << endl;
    cout << "数组在内存中的第一个元素地址:" << &arr[0] << endl;
    cout << "数组在内存中的第二个元素地址:" << &arr[1] << endl;
    return 0;
}
```

#### 5.2.3 冒泡排序

**作用：**最常用的排序算法，对数组内元素进行排序

1. 比较相邻的元素，如果第一个比第二个大，就进行交换
2. 对每一对相邻元素进行上述工作，执行完毕后，找到第一个最大值
3. 重复以上的步骤，每次比较次数-1，直到不需要比较

> 排序总轮数 = 元素个数 - 1
>

> 内层循环对比次数 = 元素个数 - 排序轮数 - 1
>

```C++
#include<iostream>
using namespace std;

int main() {
    int nums[] = {9, 8, 7, 6, 5, 4, 3, 2, 1, 0, 10};
    int n = sizeof(nums) / sizeof(nums[0]);
    cout << "排序前：" << endl;
    for (int i = 0; i < n; i++) {
        cout << nums[i] << " ";
    }
    cout << endl;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            int temp = nums[j];
            if (nums[j] > nums[j + 1]) {
                nums[j] = nums[j + 1];
                nums[j + 1] = temp;
            }
        }
    }
    cout << "排序后：" << endl;
    for (int i = 0; i < n; i++) {
        cout << nums[i] << " ";
    }
    return 0;
}
```

### 5.3 二维数组

> 在一位数组的基础上添加一个维度

#### 5.3.1 二维数组的定义方式

二维数组的四种定义方式：

```
1. 数据类型 数组名[行数][列数];
2. 数据类型 数组名[行数][列数] = {数据1,数据2},{数据3,数据4};
3. 数据类型 数组名[行数][列数] = {数据1,数据2,数据3,数据4};
4. 数据类型 数组名[][列数] = {数据1,数据2,数据3,数据4};
```

> 建议使用第二种，更加直观，提高代码可读性
>

```C++
#include<iostream>
using namespace std;

int main() {
    // 数据类型 数组名[行数][列数]
    int arr1[2][2];
    // 数据类型 数组名[行数][列数] = {数据1,数据2},{数据3,数据4};
    int arr2[2][2] = {
            {1, 2},
            {3, 4}
    };
    // 数据类型 数组名[行数][列数] = {数据1,数据2,数据3,数据4};
    int arr3[2][2] = {1, 2, 3, 4};
    //数据类型 数组名[][列数] = {数据1,数据2,数据3,数据4};
    int arr4[][2] = {1, 2, 3, 4};
    return 0;
}
```

#### 5.3.2 二维数组数组名

- 查看二维数组所占内存空间
- 获取二维数组首地址

```C++
cout << "二维数组所占内存空间：" << sizeof(arr2) << endl;
cout << "二维数组第一行所占内存空间：" << sizeof(arr2[0]) << endl;
cout << "二维数组首元素所占内存空间：" << sizeof(arr2[0][0]) << endl;
cout << "二维数组行数：" << sizeof(arr2) / sizeof(arr2[0]) << endl;
cout << "二维数组元素数：" << sizeof(arr2) / sizeof(arr2[0][0]) << endl;
cout << "二维数组首地址：" << arr2 << endl;
cout << "二维数组首行地址：" << arr2[0] << endl;
cout << "二维数组第二行地址：" << arr2[1] << endl;
cout << "二维数组首元素地址：" << &arr2[0][0] << endl;
cout << "二维数组第二个地址：" << &arr2[0][1] << endl;
```

#### 5.3.3 二维数组应用案例

**考试成绩统计：**

案例描述：有三名同学(张三、李四、王五)，在一次考试中的成绩分别如下，**请分别输出三名同学的总成绩**

|      | 语文 | 数学 | 英语 |
| ---- | ---- | ---- | ---- |
| 张三 | 100  | 100  | 100  |
| 李四 | 90   | 50   | 100  |
| 王五 | 60   | 70   | 80   |

```C++
#include<iostream>
#include<string>
using namespace std;

int main() {
    int score[3][3] = {
            {100, 100, 100},
            {90,  50,  100},
            {60,  70,  80}
    };
    string names[3] = {"张三", "李四", "王五"};
    for (int i = 0; i < 3; i++) {
        int sum = 0;
        for (int j = 0; j < 3; j++) {
            sum += score[i][j];
        }
        cout << names[i] << "的总成绩为：" << sum << endl;
    }
    return 0;
}
```

## 6 函数

### 6.1 概述

**作用：**将一段经常使用的代码封装起来，减少重复代码

一个较大的程序，一般分为若干个程序块，每个模块实现特定的功能。



### 6.2 函数的定义

函数的定义一般主要有5个步骤：

1. 返回值类型
2. 函数名
3. 参数列表
4. 函数体语句
5. return 表达式

**语法：**

```C++
返回值类型 函数名 (参数列表)
{
    函数体语句;
    
    return 表达式;
}
```

- 返回值类型：一个函数可以返回一个值
- 函数名：给函数起个名
- 参数列表：使用该函数时，传入的数据
- 函数体语句：花括号内的代码，函数内需要执行的语句
- return 表达式：和返回值类型挂钩，函数执行完后，返回相应的数据



### 6.3 函数的调用

**功能：**使用定义好的函数

**语法：**`函数名(参数)`

```C++
#include<iostream>
using namespace std;

// 定义函数
int add(int num1, int num2)// num1、num2为形式参数
{
    int sum = num1 + num2;
    return sum;
}

int main() {
    int num1, num2;
    cin >> num1 >> num2;
    // main 函数中调用 add() 函数
    int sum = add(num1, num2);// 此时num1、num2为实参
    cout << num1 << "+" << num2 << "=" << sum << endl;
    return 0;
}
```



### 6.4 值传递

- 所谓值传递，就是函数调用时实参将数值传给形参
- 值传递时，如果形参发生，并不会影响实参

```C++
#include<iostream>

using namespace std;

// 定义函数
void swap(int num1, int num2) {
    int temp = num1;
    num1 = num2;
    num2 = temp;
    cout << "交换后：" << endl;
    cout << "num1=" << num1 << endl;
    cout << "num2=" << num2 << endl;
}

int main() {
    int num1, num2;
    cin >> num1 >> num2;
    cout << "交换前实参：" << endl;
    cout << "num1=" << num1 << endl;//11
    cout << "num2=" << num2 << endl;//22
    swap(num1, num2);//num1=22,num2=11
    cout << "交换后实参：" << endl;
    cout << "num1=" << num1 << endl;//11
    cout << "num2=" << num2 << endl;//22
    return 0;
}
```



### 6.5 函数常见的样式

常见的函数样式：

1. 无参无返
2. 有参无返
3. 无参有返
4. 有参有返



### 6.6 函数的声明

**作用：**告诉编译器函数名称及如何调用函数。函数的实际主体可以单独定义。

> 函数的声明可以多次，但是函数的定义只能有一次。



### 6.7 函数的分文件编写

**作用：**让代码结构更加清晰

函数分文件编写一般有4个步骤：

1. 创建后缀名为.h的头文件
2. 创建后缀名为.cpp的源文件
3. 在头文件中写函数的声明
4. 在源文件中写函数的定义

```C++
// swap.h 头文件
#include<iostream>
using namespace std;
void swap(int num1, int num2) {
    int temp = num1;
    num1 = num2;
    num2 = temp;
    cout << "交换后：" << endl;
    cout << "num1=" << num1 << endl;
    cout << "num2=" << num2 << endl;
}
```

```C++
// .cpp 文件
#include<iostream>
#include "headfiles/swap.h" // 引入头文件
using namespace std;

int main() {
    int num1, num2;
    cin >> num1 >> num2;
    cout << "交换前实参：" << endl;
    cout << "num1=" << num1 << endl;
    cout << "num2=" << num2 << endl;
    swap(num1, num2);
    cout << "交换后实参：" << endl;
    cout << "num1=" << num1 << endl;
    cout << "num2=" << num2 << endl;
    return 0;
}
```

## 7 指针

### 7.1 指针的基本概念

**指针的作用：**可以通过指针间接访问内存

- 内存编号是从0开始记录的，一般用十六进制数字表示
- 可以利用指针变量保存地址



### 7.2 指针变量的定义和使用

**指针变量定义语法：**`数据类型 * 变量名;`

```C++
#include<iostream>
using namespace std;

int main() {
    // 定义整型变量a
    int a = 10;
    // 定义指针
    int *p;
    // 指针变量赋值
    p = &a;// 指针变量指向变量a的地址
    
    // 通过*操作指针变量指向的内存
    cout << "*p=" << *p << endl;
    cout << "p=" << p << endl;
    cout << "a的地址为=" << &a << endl;
    return 0;
}
```



### 7.3 指针所占内存空间

32位操作系统下为4字节，64位系统下为8字节。

```C++
#include<iostream>
using namespace std;

int main() {
    int a = 10;
    int *p = &a;
    cout << sizeof(*p) << endl;// 4
    cout << "sizeof(p)=" << sizeof(p) << endl; // 8
    cout << "char * 所占内存大小：" << sizeof(char *) << endl;		// 8
    cout << "int * 所占内存大小：" << sizeof(int *) << endl;		// 8
    cout << "float * 所占内存大小：" << sizeof(float *) << endl;	// 8
    cout << "double * 所占内存大小：" << sizeof(double *) << endl;	// 8
    return 0;
}
```



### 7.4 空指针和野指针

**空指针：**指针变量指向内存中编号为0的空间

**用途：**初始化指针变量

**注意：**空指针指向的内存是不可以访问的

> 0~255之间的内存编号为系统占用，不可以访问



**野指针：**指针变量指向非法的内存空间

```C++
#include<iostream>
using namespace std;

int main() {
    int *p = (int *) 0x1100;
    // 访问野指针报错
    cout << *p << endl;
    return 0;
}
```

> 总结：空指针和野指针都不是我们申请的内存，因此不要访问



### 7.5 const修饰指针

const修饰指针有三种情况：

1. const修饰指针 ---常量指针

   1. 特点：指针的指向可以修改，但指针指向的值不可以修改

   2. ```C++
      int a = 10;
      int b = 20;
      const int *p = &a;
      *p = 20;// 错的
      p = &b;// 对的
      ```

2. const修饰常量 ---指针常量

   1. 特点：指针的指向不可以改，指向的值可以改

   2. ```C++
      int * const p = &a;
      *p = 20; // 对的
      p = &b;  // 错的
      ```

3. const既修饰指针，又修饰常量

   1. ```C++
      const int * const p = &a;
      *p = 20; // 错的
      p = &b;	 // 错的的
      ```

      

### 7.6 指针和数组

**作用：**利用指针访问数组中元素

```C++
#include<iostream>
using namespace std;

int main() {
    int array[] = {1, 2, 3, 4, 5, 6, 7};
    int *p = array;// *p指向array[0]
    cout << "array[0]=" << array[0] << endl;
    // 利用指针访问数组首元素
    cout << "*p=" << *p << endl;
    for (int i = 0; i < sizeof(array) / sizeof(array[0]); i++) {
        //利用指针遍历数组
        cout << *p << endl;
        p++;
    }
    return 0;
}
```



### 7.7 指针和函数

**作用：**利用指针做函数参数，可以修改实参的值

> 值传递：值传递不会改变实参

> 地址传递：地址传递会修改实参

```C++
#include<iostream>
using namespace std;
// 值传递
int swap(int num1, int num2) {
    int temp = num1;
    num1 = num2;
    num2 = temp;
}
// 地址传递
int swap(int *num1, int *num2) {
    int temp = *num1;
    *num1 = *num2;
    *num2 = temp;
}

int main() {
    int a = 10;
    int b = 20;
    cout << "初始值：" << endl;
    cout << "a=" << a << endl;
    cout << "b=" << b << endl;
    cout << "&a=" << &a << endl;
    cout << "&b=" << &b << endl;
    // 值传递
    swap(a, b);
    cout << "值传递后：" << endl;
    cout << "a=" << a << endl;
    cout << "b=" << b << endl;
    cout << "&a=" << &a << endl;
    cout << "&b=" << &b << endl;
    // 地址传递
    swap(&a, &b);
    cout << "地址传递后：" << endl;
    cout << "a=" << a << endl;
    cout << "b=" << b << endl;
    cout << "&a=" << &a << endl;
    cout << "&b=" << &b << endl;
    return 0;
}
```

> 值传递后实参的值可能会改变，但是实参的地址不变



## 8 结构体

### 8.1 结构体基本概念

结构体属于用户**自定义的数据类型**，允许用户存储不同的数据类型



### 8.2 结构体的定义和使用

**语法：**`struct 结构体名 { 结构体成员列表 };`

通过结构体创建变量的方式有三种：

1. struct 结构体名 变量名;
2. struct 结构体名 变量名 = {成员1值,成员2值,...}
3. 定义结构体是顺便创建结构体变量

```C++
#include<iostream>
#include<string>

using namespace std;
struct student {
    string name;
    int age;
    string sex;
} s3;// s3 为结构体变量
int main() {
    // 第一种定义方式 struct 结构体名 变量名;
    // struct 可以省略
    //struct student s1;
    student s1;
    s1.name = "XYY";
    s1.age = 10;
    s1.sex = "男";
    cout << s1.name << "是个" << s1.age << "岁的" << s1.sex << "孩儿。" << endl;

    //第二种定义方式 struct 结构体名 变量名 = {成员1值,成员2值,...}
    struct student s2 = {"DYY", 12, "女"};
    cout << s2.name << "是个" << s2.age << "岁的" << s2.sex << "孩儿。" << endl;

    // 第三种定义方式 定义结构体是顺便创建结构体变量
    s3.name = "YYY";
    s3.age = 14;
    s3.sex = "女";
    cout << s3.name << "是个" << s3.age << "岁的" << s3.sex << "孩儿。" << endl;

    return 0;
}
```

> 总结1：定义结构体时的关键字是struct，不可省略

> 总结2：创建结构体变量时，关键字struct可以省略

> 总结3：结构体变量利用操作符"."访问成员



### 8.3 结构体数组

**作用：**将自定义的结构体放入到数组中方便维护

**语法：**`struct 结构体名 数组名[元素个数] = { {} ,{} ,...};`

```C++
#include<iostream>
#include<string>
using namespace std;
struct student {
    string name;
    int age;
    string sex;
};

int main() {
    // 创建结构体数组
    struct student students[5] = {
            {"XYY", 10, "男"},
            {"DYY", 12, "女"},
            {"YYY", 14, "女"}
    };
    // 给结构体数组中的元素赋值
    students[3] = {"ZZZ", 16, "男"};

    students[4].name = "XXX";
    students[4].age = 18;
    students[4].sex = "男";
    // 遍历结构体数组
    for (int i = 0; i <5;i++){
        cout << students[i].name << "是个" << students[i].age << "岁的" << students[i].sex << "孩儿。" << endl;
    }
    return 0;
}
```



### 8.4 结构体指针

**作用：**通过指针访问结构体中成员

- 利用操作符`->`可以通过结构体指针访问结构体属性 

```C++
#include<iostream>
#include<string>

using namespace std;
struct student {
    string name;
    int age;
    string sex;
};

int main() {
    student s = {"ZZZ", 16, "男"};
    student *p = &s;
    // 通过操作符 -> 访问成员变量
    cout << p->name << "是个" << p->age << "岁的" << p->sex << "孩儿。" << endl;
    return 0;
}
```



### 8.5 结构体嵌套结构体

**作用：**结构体中的成员可以是另一个结构体

```C++
#include<iostream>

using namespace std;

struct phone {
    string type;
    string number;
};

struct person {
    string name;
    int age;
    string sex;
    struct phone phone;
};

int main() {
    struct person p1 = {"XYY", 11, "男", {"HUAWEI nova5Pro", "17539776800"}};
    cout << p1.name << " " << p1.age << " " << p1.sex << " " <<p1.phone.type << " " << p1.phone.number << endl;
    return 0;
}
```



### 8.6 结构体做函数参数

**作用：**将结构体作为参数向函数中传递

传递方式有两种：

- 值传递
- 地址传递

```C++
#include<iostream>
#include<string>

using namespace std;

struct student {
    string name;
    int age;
};

// 值传递
void printStudent(student student) {
    cout << "name:" << student.name << ";age:" << student.age << endl;
};

// 地址传递
void printStudent(student *student) {
    cout << "name:" << student->name << ";age:" << student->age << endl;
}

int main() {
    struct student student = {"XYY", 11};
    // 值传递
    printStudent(student);
    // 地址传递
    printStudent(&student);
    return 0;
}
```

> 注意：使用值传递时，会拷贝一份数据给函数;而使用地址传递时不会拷贝数据，减少了内存的使用





### 8.7 结构体中const使用场景

**作用：**用const来防止误操作

```C++
#include<iostream>
#include<string>

using namespace std;

struct student {
    string name;
    int age;
};

// const修饰，防止误操作
void printStudent(const student *student) {
    //student->age = 11; // 操作失败，因为加入了const修饰
    cout << "name:" << student->name << ";age:" << student->age << endl;
}

int main() {
    struct student student = {"XYY", 11};
    printStudent(&student);
    return 0;
}
```



## 9 案例

### 9.1、生成随机数

```C++
#include<iostream>
#include<ctime>
using namespace std;

int main() {
    srand((unsigned) time(NULL));
    int ran = rand() % 100 + 1;
    for (int i = 0; i < 100; i++) {
        cout << (rand() % 100 + 1) << endl;
    }

    return 0;
}
```

### 9.2、练习案例

#### 9.2.1猜数字游戏

```C++
#include<iostream>
#include<ctime>

using namespace std;

int main() {
    srand((unsigned) time(NULL));
    int ran = rand() % 100 + 1;
    int ci = 0;
    while (ci != ran) {
        cout << "请输入您要猜的数：";
        cin >> ci;
        if (ci > ran) {
            cout << "猜大了" << endl;
        } else if (ci < ran) {
            cout << "猜小了" << endl;
        }
    }
    // 跳出循环说明猜对了
    cout << "生成的随机数为：" << ran << endl;
    cout << "恭喜您获胜" << endl;
    return 0;
}
```



#### 9.2.2 水仙花数

**案例描述：**水仙花数是指一个三位数，它的每个位上的数字的三次幂等于它本身

例如：1^3+5^3+3^3 = 153

请利用do...while语句，求出所有三位数中的水仙花数

```C++
#include<iostream>
using namespace std;

int main() {
    int i = 100;// 初始值
    do {
        int gw = i % 10;// 获取个位数
        int sw = i / 10 % 10;//获取十位数
        int bw = i / 100; //获取百位数
        if ((gw * gw * gw + sw * sw * sw + bw * bw * bw) == i) {
            cout << i << endl;
        }
        i++;
    } while (i < 1000);
    return 0;
}
```

#### 9.2.3 敲桌子

**描述：**从1开始数到数字100，如果数字中含有7或者是7的倍数，打印“敲桌子”，其余数字直接打印输出。

```C++
#include<iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 100; i++) {
        if (i % 10 == 7 || i / 10 == 7 || i % 7 == 0) {
            cout << "敲桌子:" << i << endl;
        } else {
            cout << i << endl;
        }
    }
    return 0;
}
```

#### 9.2.4 打印九九乘法表

```C++
#include<iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 9; i++) {
        for (int j = 1; j <= i; j++) {
            cout << i << "*" << j << "=" << i * j << "\t";
        }
        cout << endl;
    }
    return 0;
}
```

#### 9.2.5 五只小猪称体重

```C++
#include <iostream>
using namespace std;

int main() {

    int arr[5] = {300, 350, 300, 400, 250};
    int max = 0;
    for (int i = 0; i < 5; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    cout << "最重的小猪体重：" << max << endl;
    return 0;
}
```

#### 9.2.6 元素逆置

一个数组中若干个元素，将数组中元素逆置。

```C++
#include <iostream>
using namespace std;

int main() {

    int arr[] = {1, 3, 2, 5, 4};
    int start = 0;//起始下标
    int end = sizeof(arr) / sizeof(arr[0]) - 1;//结尾下标
    do {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    } while (start < end);
    // 打印逆置元素
    for (int i = 0; i < (sizeof(arr) / sizeof(arr[0])); i++) {
        cout << arr[i] << endl;
    }
    return 0;

```



#### 9.2.7 指针、数组、函数 实例

**案例描述：**封装一个函数，利用冒泡排序，实现对整型数组的升序排序

例如数组：int arr[10] = {4,3,6,9,1,2,10,8,7,5};

```C++
#include<iostream>

using namespace std;
// 冒泡排序
void bubbleSort(int *arr, int len) {
    for (int i = 0; i < len - 1; i++) {
        for (int j = 0; j < len - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
};
// 打印数组
void printArray(int *arr, int len) {
    for (int i = 0; i < len; i++) {
        cout << arr[i] << " ";
    }
}

int main() {
    int arr[10] = {4, 3, 6, 9, 1, 2, 10, 8, 7, 5};
    int len = sizeof(arr) / sizeof(arr[0]);
    cout << "排序前：" << endl;
    printArray(arr, len);
    cout << endl;
    bubbleSort(arr, len);
    cout << "排序后：" << endl;
    printArray(arr, len);
    return 0;
}
```



#### 9.2.8 结构体案例

设计一个英雄的结构体，包括成员姓名，年龄，性别；创建结构体数组，数组中存放5名英雄。
通过冒泡排序的算法，将数组中的英雄按照年龄进行升序排序，最终打印排序后的结果。

```C++
#include<iostream>
#include<string>

using namespace std;

struct hero {
    string name;
    int age;
    string sex;
};

void bubbleSort(hero *arrHero, int len) {
    for (int i = 0; i < len - 1; i++) {
        for (int j = 0; j < len - i - 1; j++) {
            if (arrHero[j].age > arrHero[j + 1].age) {
                hero temp = arrHero[j];
                arrHero[j] = arrHero[j + 1];
                arrHero[j + 1] = temp;
            }
        }
    }
}

void printHero(hero *arrHero, int len) {
    for (int i = 0; i < len; i++) {
        cout << "姓名：" << arrHero[i].name << ";年龄：" << arrHero[i].age << ";性别：" << arrHero[i].sex << endl;
    }
}

int main() {
    struct hero arrHero[5] = {
            {"刘备",   20, "男"},
            {"关羽",   22, "男"},
            {"不知火舞", 18, "女"},
            {"诸葛亮",  16, "男"},
            {"小乔",   17, "女"}
    };
    int len = sizeof(arrHero) / sizeof(arrHero[0]);
    bubbleSort(arrHero, len);
    printHero(arrHero, len);
    return 0;
}
```



# 通讯录管理系统

## 1.系统需求

通讯录是一个可以记录亲人、好友信息的工具。
本教程主要利用C++来实现一个通讯录管理系统
系统中需要实现的功能如下：

- 添加联系人：向通讯录中添加新人，信息包括(姓名、性别、年龄、联系电话、家庭住址)最多记录1000人。
- 显示联系人：显示通讯录中所有联系人信息
- 删除联系人：按照姓名进行删除指定联系人
- 查找联系人：按照姓名查看指定联系人信息
- 修改联系人：按照姓名重新修改指定联系人
- 清空联系人：清空通讯录中所有信息
- 退出通讯录：退出当前使用的通讯录
