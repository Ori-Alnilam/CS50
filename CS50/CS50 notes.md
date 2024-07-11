---
date: 2024-04-10
---
# 前言
需要阅读：
[C风格指南](https://cs50.readthedocs.io/style/c/)
[CS50手册](https://manual.cs50.io/)
一些链接：
[练习题](https://cs50.harvard.edu/x/2024/practice/)
[成绩单](https://cs50.me/cs50x)
[我的Github主页](https://github.com/Ori-Alnilam?tab=overview&from=2024-05-01&to=2024-05-31)


须知：笔记的作用是自己的lecture notes，在忘记课程中的知识点时，能直接从笔记中获得解答，而不需要再去翻讲座视频。也是一种记录和巩固学习过程：一般视频中某个知识点讲完后，趁热自己从头到尾敲一遍演示代码，再把学到的东西自己（不看视频）写一遍出来，亲自动手的时候就能发现对某些知识点的了解可能还是模糊的，巩固即可。

# week1 C
## 知识点总结
- **好代码的三标准**——correct(代码是否是正确的？)、design(代码是否是好的设计、便于后期维护？)、style(代码风格如何，是否易读？)
- **命令行** commend line interface == CLI == 命令行command line == 终端窗口terminal window
不要再只认识终端不认识“命令行”三个字啦！QAQ
- escape character**转义字符**--- \ (这个符号在记笔记时也很有用，告诉Obisidian某些符号像`[]`有时作为*字面意思*\[中括号\]而不是“链接”来使用---`\[\]` )；用`\n`换行而不是简单敲回车，在C里如果有一串文本，它们必须保持在同一行。
- **字面意思的%百分号**---与\类似，如果想要在printf里使用字面意思的%：`printf("I got 100%%")`，在运行后将在终端看到`I got 100%`。也就是用`%%`来表示字面意思的百分号。否则单个`%`会被视为**占位符**而因缺少完整如`%s`报错。
- **字面意思的等号也类似**--- `x == y`（在布尔表达式里千万要注意！）
- **限定符** unsigned、const等。unsigned int --- 正值加倍，无负值。0-40亿
- **数据类型** （所占字节、只在定义变量时声明类型）data type---int、long、float、double、char、string(cs50)、bool(cs50)
- **创建多个同类型变量**---`int height, width;`
- **if和swith条件语句**
- **无限循环while(ture)** 按ctrl+c可以退出---关键字true需要include stdbool库（或cs50库）
- **三个循环语句**：while(重复未知不确定次数)、do while(不确定循环次数但至少一次)、for(某个确定的循环次数，未知，可以由用户输入决定)
**while** --- run the control flow for a game不知道用户何时结束游戏，所以一直循环运行
**do while** --- promting the user for input获取期待的用户输入
**for** --- repeat a loop a discrete number of times(even u don't know the times. )
- **命令行的一些简单操作**——ls、cd、mkdir、cp、rm、mv
- **清空终端**---终端窗口输入clear回车 or Ctrl +L
- **magic number**——`#define PI 3.14`
- **变量整型截断**——`int i = 10 / 3;` --- i 的值为3
- **变量类型**——bool、char、double、float、int、long、string
- **注释comments**——单行`//` 多行`/**/`
- **副作用side effect 和返回值return value**--**副作用**是屏幕上出现的*视觉效果*；**返回**值是*函数的输出*，可以用变量接住后继续使用，用变量接住返回值通过`=`**赋值语句**
- **标准I/O库**Standard I/O library---Standard Input and Output---标准输入输出
- `#include <stdio.h>`--**include a library that declare the function to exist**--历史上的效率问题，在电脑运行速度慢、资源有限的时代，我们不想能随意访问所有函数，而是只包含自己需要使用的函数，提高效率。
- **placeholder占位符%s**--placeholder for a string--just a format code(格式代码)，means plug in some value here
- **style**--`if (x < y)` 在if后加上空格，在printf后不需要`printf("no space after printf")`(只是一种风格约定)。如下：
```c
if (x < y)
  ^ // 有空格
printf("x < y");
      ^ // 无空格
```
> when using the **keyword if**, you should, as a matter of best practice, put a **space** after the word if.
- **命令回溯**(自己起的名字hh)---箭头键
> use your keyboard's **arrow keys** in VS Code to scroll back through time
- syntactic sugar**语法糖**---`i = i + 1`➡`i += 1`➡`i++`
- **关键字true和false**---包含在stdbool库里`#include <stdbool.h>` or `#include <cs50.h>`
- **ls**---hello\*星号表示可执行文件，在PC可以双击打开，在命令行需要`.\hello`运行；hello.c是源代码文件
- **命名约定**：函数名以小写字母开头
- **布尔表达式一定一定要注意比较运算符和赋值运算符！！！错很多次了**
- 和布尔值有关的代码我总会出错，**(布尔表达式)表示真，(!布尔表达式)为假，不需要`epre == true`or`epre == false`之类的**
- **return** -- return后面可以接布尔表达式，布尔表达式可以直接作为`return`语句的返回值。如`return x > y;`在 C 语言中，布尔表达式的计算结果会自动转换为 `true` 或 `false`（或者 1 或 0）。可以直接返回布尔表达式，而不需要显式地检查条件并返回 `true` 或 `false`。
- 占位符：
`%s` -- 字符串string
`%c` -- 单字符char
`%i` -- 整数int
`%f` -- 浮点数float--`%.2f`可以指定小数点后的位数
- **英语积累：**
> [!note]+ Engnish
>  curly brace  ---  花括号{}
>  GUI(Graphical User Interface)  ---  图形用户界面
>  CLI(Commend Line interface)  ---  命令行界面
>  double quotes  ---  双引号
>  single quotes  ---  单引号
>  backslash  ---  反斜杠
>  implement  ---  实现
>  syntax  ---  语法
>  syntactic sugar  ---  语法糖
>  initialize  ---  初始化
>  File Explorer  ---  文件资源管理器
>  canonical  ---  经典的
>  pseudocode --- 伪代码

## bug重现（小测验！）
(准备好迎接bug军团的挑战吧！！！)
- 在credit中`return (50 < start < 56);`为什么报错？
- [x] 正确的代码为==~~return (start > 50 && start < 56)~~==
> [!hibox]
> `return 50 < start < 56;` 这个表达式它会首先评估 `50 < start`，返回一个布尔值（`true` 或 `false`，即 1 或 0）。然后，这个布尔值（1或0）会被与 `56` 进行比较，成为一个永远true的布尔表达式。逻辑错误❌
- 在credit中`return (start1 = 4 || start2 = 4);`怎么次次强调次次错啊:明明刚学的时候几乎不会犯这种错误的，反倒现在学久了知识全混了是吧！不应该啊我哭╥﹏╥...
- [x] success：==~~\=\=我都不想说你！~~==


## week1心得体会
1. 第一次接触到有**辅助轮**的学习，只专注于需要练习的内容就可以，其余的困难几乎都帮我们解决了。感觉学不好都是对这样用心的课程的辜负hh
2. 有了ddb和GPT的辅助，可以辅助我们一步步优化自己的代码。这点我觉得很好！不是写完了通过check了就丢一边，继续检查是否是好的设计，代码还可以怎样优化
3. 函数封装的思想好有魅力！被迷住了喵...❤*(在这发病是吧)*
先整体把大的问题分成小部分，每个部分再去思考如何实现，是否可以封装成函数？感觉有点像最近在画画里学到的【概括】技能呢！

## lecture1代码示例
**要求：复习回顾时能根据笔记大纲写出所有的完整代码，熟悉代码是如何一步步优化的**

- [lecture1双语精翻](https://www.bilibili.com/video/BV1Yp4y1J7Rk/?spm_id_from=333.788&vd_source=dab7ee9d5c2d604b3bf4fe7298837d4f)
- [lecture1官网笔记](https://cs50.harvard.edu/x/2024/notes/1/)

**碎碎念**：第一次接触到这种把知识浓缩到全是精华部分呈给你的讲座，几乎没有废话，听得非常享受，也完全不会走神！太感动了，感觉教学的课堂就该是这样的😭
### Conditionals
#### 单一if语句
```c
// code compare.c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int x = get_int("What's x? ");
    int y = get_int("What's y? ");

    if (x < y)
    {
        printf("x is less than y\n");
    }
}
```
只考虑了一种情况，使用**if-else语句**改进：
#### if-else语句考虑所有情况
- **x y关系大小比较：**
```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int x = get_int("What's x? ");
    int y = get_int("What's y? ");

    if (x < y)
    {
        printf("x is less than y\n");
    }
    else if (x > y)
    {
        printf("x is greater than y\n");
    }
    else
    {
        printf("x is equal to y\n");
    }
}
```
- **yes or no 判断：组合布尔表达式**
四种情况`Y、y、N、n`分两条路：
`if (c == Y || c == y)`
`else if (c == N || c == n)`
而不是“代码味怪怪的”四条路

### Loops(猫叫循环)
#### meow0直接打印
```c
#include <stdio.h>

int main(void)
{
    printf("meow\n");
    printf("meow\n");
    printf("meow\n");
}
```
拒绝复制粘贴！重复的部分使用循环变得简洁并且不易在修改时出错：
#### meow1使用循环语句
##### 1.1while循环
```c
#include <stdio.h>

int main(void)
{
    int i = 0;
    while (i < 3)
    {
        printf("meow\n");
        i++;
    }
}
```
我们不用`i从1计数i++`也不用`i从3计数i--`，在计算机科学中，从0计数
##### 1.2for循环
```c
#include <stdio.h>

int main(void)
{
    for (int i = 0; i < 3; i++)
    {
        printf("meow\n");
    }
}
```
#### meow2函数封装
**把实现meow的部分用函数封装起来**
##### 实现猫叫
**函数实现：**
```c
void meow(void)
{
    printf("meow\n");
}
```
不接受参数，该函数只实现打印meow
**函数声明后在main函数调用：**
```c
#include <stdio.h>

void meow(void);

int main(void)
{
    for (int i = 0; i < 3; i++)
    {
        meow();
    }
}

void meow(void)
{
    printf("meow\n");
}
```
注意在最前面写上函数声明。接下来尝试给meow函数传递一个参数，以控制猫叫的次数：
##### 实现指定次数猫叫
```c
#include <stdio.h>

void meow(int n);

int main(void)
{
    meow(3);
}

// Meow some number of times
void meow(int n)
{
    for (int i = 0; i < n; i++)
    {
        printf("meow\n");
    }
}
```
- 还可以进一步由用户决定猫叫次数
>0. 获取用户输入的一个整数，存于变量n
>1. meow(n);

### Abstraction抽象

#### 打印一行4个问号砖块
```c
#inclulde <stdio.h>

int main(void)
{
	for (int i = 0; i < 4; i++)
	{
		printf("?");
	}
	printf("\n");
}
```

#### 打印一列3个垂直砖块
```c
#include <stdio.h>

int main(void)
{
	for (int i = 0; i < 3; i++)
	{
		printf("#\n");
	}
}
```

#### 打印3\*3的砖块
```c
#include <stdio.h>

int main(void)
{
	for (int i = 0; i < 3; i++)
	{
		for (int j = 0; j < 3; j++)
		{
			printf("#");
		}
		printf("\n");
	}
}
```
- 两个循环不能都用i哦~(i敲顺手了可能会不小心忘记..没错说的就是我)
- 接下来我们添加注释comments提高代码可读性
- 注意到`3`这个magic number，如果想打印固定边长的正方形砖块，可以定义一个常量变量`const int n = 3`也可以由用户输入决定边长大小`int n = get_int("Size: ")`，记得在调用`get_int`函数前`include <cs50.h>`。根据**用户不可信**原则，用`do while()`给代码加上防御点，**避免用户输入非正整数：**
```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
	// 提示用户输入正整数边长
	int n = 0;
	do
	{
		n = get_int("Size: ");
	}
	while (n < 1);

	// 打印正方形砖块
	for (int i = 0; i < n; i++)
	{
		for (int j = 0; j < n; j++)
		{
			printf("#");
		}
		printf("\n");
	}
}
```

#### Abstraction函数封装打印砖块
##### 尝试在更高层次用伪代码实现功能：
```c
// Get Size of grid
int n = get size();
// Print grid of bricks
print_grid(n);
```
**现在整个main函数里除开注释仅仅两行代码，类似的处理非常利于团队合作来解决一个大型项目---将大型程序拆分成小部分，团队成员各自实现不同的部分**
> spllitting up large programs into smaller parts, having different people implement different parts, so long as you all agree in advance on what those inputs and those outputs actually are.

##### get_size()函数实现
不接收参数，返回一个int：
```c
int get_size(void)
{
	int n = 0;
	do
	{
		n = get_int(Size: );
	}
	while (n < 1);

	return n;
}
```
##### print_grid()函数实现
接受一个int，无返回值，有副作用：
```c
void print_grid(int n)
{
	for (int i = 0; i < n; i++)
	{
		for (int j = 0; j < n; j++)
		{
			printf("#");
		}
		printf("\n");
	}
}
```
##### 函数声明
最后在main函数之前记得声明这两个自定义函数：
```c
#include <cs50.h>
#include <stdio.h>

int get_size(void);
void print_grid(int n);

int main(void)
{
	// get size of grid
	int n = get_size();

	// print grid of bricks
	print_grid(n);
}
```
##### 总结代码实现

> [!success]+ 函数封装打印砖块
> ```c
> #include <cs50.h>
> #include <stdio.h>
> 
> int get_size(void);
> void print_grid(int n);
> 
> int main(void)
> {
> 	// get size of grid
> 	int n = get_size();
> 
> 	// print grid of bricks
> 	print_grid(n);
> }
> 
> int get_size(void)
> {
> 	int n = 0;
> 	do
> 	{
> 		n = get_int(Size: );
> 	}
> 	while (n < 1);
> 
> 	return n;
> }
> 
> void print_grid(int n)
> {
> 	for (int i = 0; i < n; i++)
> 	{
> 		for (int j = 0; j < n; j++)
> 		{
> 			printf("#");
> 		}
> 		printf("\n");
> 	}
> }
> ```

### Integer Overflow、Truncation、Floating-point Imprecision
尝试在c里实现我们自己的计算器：
##### 将加法抽象为函数
可以在c语言中用数学操作符实现计算器，我们尝试将加法抽象为函数：
```c
#include <cs50.h>
#include <stdio.h>

int add(int a, int b);

int main(void)
{
    // Prompt user for x
    int x = get_int("x: ");

    // Prompt user for y
    int y = get_int("y: ");

    // Perform addition
    int z = add(x, y);
    printf("%i\n", z);
}

int add(int a, int b)
{
    int c = a + b;
    return c;
}
```
- **add函数接收两个参数，并返回它们的和**
- **可以去除不必要的变量，使代码更简洁**：因为我们只是把 `a` 和 `b` 相加然后返回结果，所以可以直接在返回语句中进行计算，而不必使用临时变量 `c`

##### 优雅化：去除不必要变量
```c
#include <cs50.h>
#include <stdio.h>

int add(int a, int b);

int main(void)
{
    // Prompt user for x
    int x = get_int("x: ");

    // Prompt user for y
    int y = get_int("y: ");

    // Perform addition
    printf("%i\n", add(x, y));
}

int add(int a, int b)
{
    return a + b;
}
```
##### Integer Overflow整型溢出
上述代码运行，当输入`x = 2000000000`&`y = 2000000000`时，我们期待得到输出4000000000。
实际上，会得到一个奇怪的负数
> [!note]+ Integer Overflow的原因
> int类型在内存中占32bits(4bytes), 最多能表示11111111111111111111111111111111（约40亿）个数字。因为将这些内存平等分给正数和负数，所以实际上，一个int差不多可以表示最小-20亿、最大20亿的数。

要获得期望输出，可以将变量定义为long类型，使用64位，以获得更大的计数。但不管怎样，请记住，**计算机的内存是有限的！**
> We only have a **finite** amount of memory!

##### Truncation截断
在浮点数运算时尤其容易出现，**丢失小数点后的所有内容**
> truncate the value-- that is lose everything after the decimal point.

> [!question] 
> `int z = 1 / 3` z gets the value 0；在定义变量时改为float？`float z = 1 / 3` z gets the value 0.000000

> the issue fundamentally is that C is still treating x (1) and y (3) as integers **with no decimal point**, and dividing one by the other, therefore has no room for any numbers after a decimal point.

How to solve this ? **type casting!**

- [?] 突然的问题：为什么`float f = 1`可以gets the value 1.000000，而`int i = 1.0`却无法通过编译呢？为什么不能gets the value 1？

##### type casting类型转换
> type casting-- that is convet one data type to another

**代码实现：**`float z = (float) 1 / (float) 3`
`printf("%f\n", z)` ptint z 0.333333

试试打印小数点后更多位？
`printf("%.20f\n", z`(打印小数点后20位)
0.33333334326744079590

！出现了！浮点数不精确！

##### Floating-point Imprecision浮点数不精确


#### 
## Shorts
shorts会补充一些讲座上没时间讲的细节，对我这个初学者很友好~可以选择听自己觉得掌握得不太好的部分

### 条件语句Conditional Statements
✨==if（if-else、if-else if-...-else）、switch、?:==

#### **布尔表达式**：boolean-expression
（在条件语句里用到的布尔表达式）逻辑运算符、关系运算符
```c
AND --- &&
OR --- ||
NOT --- ! // 这个就是最开始不知道的▼ ▼
if (! x < y) 
<、>、==、! =...请注意相等运算符是== 如if(x == y)
```

#### **if else 嵌套**的条件语句：
```c
if()
{
}
else if()
{
}
else if()
{
} // 三个if互斥
```

> [!warning]
> 注意，else只能绑定到最近的一个if，如果：
> ```c
> if()
> {
> }
> if()
> {
> }
> if()
> {
> }
> else
> {
> }
> ```
> 这里的三个if不是互斥的，之后最后一个if与else互斥

####  **switch()语句**
```c
int n = get_int();
switch (n)
{
	case 1:
		printf("one\n");
		break; // 不加break会继续向下遍历，有时需要
	case 2:
	...
	case 3:
	...
	default:
}
```

#### ternary operator---(?:)
```c
int x;
if (expr) // expr表示某个布尔表达式boolean-expreesion
{
	x = 5;
}
else
{
	x = 6;
}
```
以上代码可以简化成：
```c
int x = (expr) ? 5 : 6; // ?后真:后假
```
酷酷的代码😎（很高大上的样子喵~）(bushi)

### 循环语句loops
#### while()
- 无限循环while(ture)
#### do while()语句：获取期待的用户输入
do while是C有的，Python没有
> A general piece of advice within programming is that you should **never fully trust your user**. They will likely misbehave, typing incorrect values where they should not.
```c
do
{

}
while (boolean-expr);
```
do while()语句与while()语句的区别：do while()保证{}至少会执行一次
do while循环用于**提示用户输入**，比如希望用户输入一个正整数：
```c
do
{
	int i = get_int("请输入一个正整数: ");
}
while (i < 1);
```
**注意while语句后面加分号**

补充：单独用while语句也能实现，但**copy/paste, bad**：
```c
int i = get_int(Size: );
while (i < 1)
{
	i = get_int(Size: );
}
```
1,4行太重复了
#### for循环
```c
for (start; expre; increment)
// for (int i = 0; i < 3; i++)
```
- 硬编码可能会导致magic number

### Linux Conmmand Line
(适用于Unix-based operating system, like Linux、Mac OS)(不适合Windows😭)
最常用的ls查看目录中所有文件
#### cd
change directory
```c
cd <directory> --- 进入（下一级）目录
cd --- home directory --- 返回主目录
cd .. --- parent directory --- 返回上一级目录
```
#### mkdir
make a directory
```c
mkdir <directory> --- 创建目录（or folder）
```
#### cp
cope a file/directory
```c
cp <source> <destination> ......复制单个file
// cp hello.c hi.c
cp -r <source> <destination> ......复制整个目录entire directory整个文件夹folder
// cp -r hello hi
```

#### rm
remove a file/directory
```c
rm <file>
rm -f <file> ......不询问直接删除
// rm hi.c
// rm -f hi.c
rm -r <directory> ......与cp类似
rm -rf <directory>
// rm -r hi
// rm -rf hi
```
`rmdir <目录名>`也是不询问直接删除

#### mv
rename a file
```c
mv <source> <destination>
// mv studio.c stdio.c
```

### magic number
```c
#define NAME REPLACEMENT
没有分号结尾！！！NAME一般大写，与变量区分开
如#define PI 3.14
```

## Section
Section内容比较基础，时间长但知识密度不大，特别我是学了week5回来查漏补缺做的笔记，快听睡着了😴
### 类型Types
变量类型、变量名称、变量值
```c
int i = 65;
```
>    **int       i      =    65;
>\[tpye\] \[name\] | \[value\]
>\[assignment operator\]
>**"Creat an **integer** named **i** that **gets** the value **65**." 

为什么在声明变量时要强调变量类型int？当我们修改了变量类型，i储存的值就完全不同了：
```c
char i = 65;
```
>**i gets the value 'A'**

operator
- Syntacyic sugar: +=、-=、*=、/=......
- Trunction截断
```c
int i = 9;
i = i / 2; // 这条语句后i gets the value 4
```
>在定义变量时，类型为int，严格整数，i / 2会截断小数部分gets the value **4**(not 4.5)。

- printf格式代码，占位符 %i

## pset1
[pset1](https://cs50.harvard.edu/x/2024/psets/1/)
### mario less
#### 作业描述
- [mario-less](https://cs50.harvard.edu/x/2024/psets/1/mario/less/)
- 目的：打印一个右对齐金字塔

#### 代码实现
##### 分开
**1. 内层两循环分别打印#和空格**：
> [!NOTE]+ HUmario
> ```c
> // Print a right-aligned pyramid
> #include <cs50.h>
> #include <stdio.h>
> 
> int get_height(void);
> void print_pyramid(int h);
> 
> int main(void)
> {
>     // Get the height from the user
>     int height = get_height();
> 
>     // Print a pyramid
>     print_pyramid(height);
> }
> 
> int get_height(void)
> {
>     int i = 0;
>     do
>     {
>         i = get_int("Height: ");
>     }
>     while (i < 1);
>     return i;
> }
> 
> void print_pyramid(int h)
> {
>     for (int i = 0, m = h - 1; i < h; i++)
>     {
>         for (int j = 0; j < m; j++)
>         {
>             printf(" ");
>         }
>         for (int k = 0; k < h - m; k++)
>         {
>             printf("#");
>         }
>         printf("\n");
>         m--;
>     }
> }
> ```

**思路：**
1. main函数里共两行代码，功能**从用户那获取金字塔高度**和**打印金字塔**，用函数来实现；
2. **获取高度**：使用do while()语句，保证height为正整数；
3. **打印金字塔**：一个外层循环height次，两个内层循环分别打印空格和哈希符号；
4. **自我检查问题**：变量m显得有点多余，但暂时想不到怎样设计更好。


 **2.ChatGPT优化后代码：**
```c
#include <cs50.h>
#include <stdio.h>

// Function prototypes
int get_height(void);
void print_pyramid(int h);

int main(void)
{
    // Get the height from the user
    int height = get_height();

    // Print a pyramid
    print_pyramid(height);
}

// Prompt user for the pyramid height, ensuring it's between 1 and 8
int get_height(void)
{
    int height;
    do
    {
        height = get_int("Height (1-8): ");
    }
    while (height < 1 || height > 8);
    return height;
}

// Print a right-aligned pyramid of height h
void print_pyramid(int h)
{
    for (int i = 0; i < h; i++)
    {
        // Print leading spaces
        for (int j = 0; j < h - i - 1; j++)
        {
            printf(" ");
        }
        // Print hashes
        for (int k = 0; k <= i; k++)
        {
            printf("#");
        }
        // Move to the next line
        printf("\n");
    }
}

```

**具体优化点：**
1. **减少局部变量的使用**：去掉了`m`变量，直接在循环中计算空格的数量。
*这点确实很好，我写的时候也觉得有点臃肿..没想到可以把`i`利用起来*
3. **添加输入限制**：增加了对输入高度的上限限制（1到8），以符合常见的CS50课程的要求。
*碎碎念：没设上限是因为2024的作业没要求，23的作业设了的:(*
3. **注释**：添加了注释以便更易于理解。
*在每个自定义函数前添加一行注释说明函数功能，我给忘了*

##### 合起来
1. [mario-less讲解视频](https://www.youtube.com/watch?v=ZGAZIH3559g)
2. 代码实现：
 ```c
#include <cs50.h>
#include <stdio.h>

int get_height(void);
void print_pyramid(int height);

int main(void)
{
    // Get the height from the user
    int height = get_height();

    // Print a pyramid
    print_pyramid(height);
}

int get_height(void)
{
    int height = 0;
    do
    {
        height = get_int("Height: ");
    }
    while (height < 1 || height > 8); // Ensure height is between 1 and 8
    return height;
}

void print_pyramid(int height)
{
    for (int i = 0; i < height; i++) // Loop through each level
    {
        for (int j = 0; j < height; j++) // Loop through each position in the level
        {
            // Print spaces
            if (i + j < height - 1)
            {
                printf(" ");
            }
            else
            {
                // Print hashes
                printf("#");
            }
        }
        // Move to the next line
        printf("\n");
    }
}
```

**`print_pyramid` 函数代码解释**：
1. 使用嵌套的`for`循环来打印金字塔。
2. 外层循环控制金字塔的高度，每次迭代打印金字塔的一层。i是行索引。
3. 内层循环控制每一层的打印：j是列索引
 `if (i + j < height - 1)`：在当前行需要打印的空格数量。这个布尔表达式的逻辑是关键，要找出打印空格和哈希符号的规律。

**碎碎念**：
1. *坏ddb:( 用两个内循环分开的时候，要我把打印空格和哈希的逻辑合在一起；现在合一起了又要我分开！！）*
2. **区区一只橡皮鸭居然耍我，过分！！！**

##### 总结
1. 先思考如何打印左对齐的砖块
2. 用嵌套for循环打印#，与课程上*打印正方形砖块*类似。思考如何控制内层循环打印的#数量（即由布尔条件控制的**循环次数**），达到#递增效果
3. 左对齐->右对齐 -- **打印一个左对齐递减的空格群**，将递增#块“挤”到右边
### credit
#### 作业描述
1. [credit](https://cs50.harvard.edu/x/2024/psets/1/credit/)
2. **作业描述：**
- 实现Luln算法
- American Express -- 15位、34or37开头
- MasterCard -- 16位、51~55整数开头
- Visa -- 13or16位、4开头
7. **碎碎念：**满怀期待的下载好作业文件，结果打开只有include和空空的int main() 
充满怨念━┳━　━┳━没有辅助轮，完全没有

#### 代码实现
```c
#include <cs50.h>
#include <stdio.h>

bool luhn(long number);
bool is_american_express(long number);
bool is_mastercard(long number);
bool is_visa(long number);

int main(void)
{
    // Get the number from the user
    long number = get_long("Number: ");

    // Luhn?
    if (!luhn(number))
    {
        printf("INVALID\n");
    }
    else if (is_american_express(number))
    {
        printf("AMEX\n");
    }
    else if (is_mastercard(number))
    {
        printf("MASTERCARD\n");
    }
    else if (is_visa(number))
    {
        printf("VISA\n");
    }
    else
    {
        printf("INVALID\n");
    }

    return 0;
}

bool luhn(long number)
{
    bool alternate = false;
    int sum = 0;

    while (number > 0)
    {
        int digit = number % 10;
        if (alternate)
        {
            // Multiply by 2
            digit *= 2;
        }
        // Add
        sum += (digit % 10) + (digit / 10);
        // Move to the next digit
        number /= 10;
        // Switch alternate
        alternate = !alternate;
    }

    return sum % 10 == 0;
}

bool is_american_express(long number)
{
    int start = number / 10000000000000;
    return (start == 34 || start == 37);
}

bool is_mastercard(long number)
{
    int start = number / 100000000000000;
    return (start >= 51 && start <= 55);
}

bool is_visa(long number)
{
    int start1 = number / 1000000000000;
    int start2 = number / 1000000000000000;

    return (start1 == 4 || start2 == 4);
}
```
重点关注Luhn算法函数实现，回忆自己debug的过程
> [!note]+ 代码实现关键
> 1. **做除/去末位、取余%得末位**（除以几个0就可以去掉后几位，如1234**除以三个0**的100`1234 / 100 = 1`就可以**去掉后三位**得“1”）
> 2. Luln算法中控制转换的布尔类型变量
## bug set
###  do while()
创建变量需要在{}外
- [?] 可以说“声明变量”吗？应该是声明函数，我记混了吧。。

> [!error]+ do while错误示例：在{内声明变量}
> ```c
> do
> {
> 	int Height = get_int("Height: ");
> }
> while (Height < 1 || Height > 8);
> 
> > 报错信息：
> > > error: use of undeclared identifier 'Height'
> > > while (Height < 1 || Height > 8);
> > > 		 ^
> ```

**是因为在{}内声明的变量只存在于这个scope内吗？**
正确的代码：
```c
int Height;
do
{
	Height = get_int("Height: ");
}
while (Height < 1 || Height > 8);
```

> [!question]+ 思考内容
> ❓已经知道在函数内修改某个全局变量的值时，需要将变量的**地址**作为参数传入函数，再go to the address修改变量的值。如果仅将变量的**值**作为参数传入函数，则只能得到一个复制品，在函数调用结束后随着栈帧的释放变成垃圾值。这是作用域的问题。我们不能在函数里直接修改全局变量的值吗？好像模糊了全局变量的意思......**全局变量是在全前面就声明的，不是说在main主函数里声明**
>  突然理解了，像do{}、for{}、if{}里面声明的变量当然只能存在于{}内，而我的刚刚的困惑是当我在这些{}内改变main函数里变量的值时并没有用&获取地址，go to 什么的——这是因为，这些语句本来就在main的{}里啊，main的{}里声明的变量存在于整个main中，当然可以在其他条件语句里直接使用和重新赋值。可以理解为main的作用域和if语句的作用域是包含关系(个人理解)：$$ if\{\}\subset main\{\} $$ 而自定义函数与main的scope是互斥关系：$$ swap\{\}\cap main\{\} = \varnothing $$
> 如果是在main函数之外，我们另外定义的函数要改变main里的变量值，那就需要

# week2 Arrays
1. [lecture2中文精翻](https://www.bilibili.com/video/BV1nP411W7dG/?spm_id_from=333.788&vd_source=dab7ee9d5c2d604b3bf4fe7298837d4f)
2. [week2网站](https://cs50.harvard.edu/x/2024/weeks/2/)
3. [notes](https://cs50.harvard.edu/x/2024/notes/2/)

> this is week 2 wherein we're going to take a look at a lower level at how things work, and indeed, among the goals of the course is this bottom-up understanding so that in a couple of weeks' time, even a few years' time, when you encounter some new technology, you'll be able to think back hopefully on some of this week's and this is basic building blocks and primitives and really just deduce how tomorrow's technologies work.
> 我们会从底层来了解计算机怎么工作，课程的目标之一就是形成**自下而上**的理解。这样在以后我们遇到一些新技术时，能回想起这门课的内容，**从计算机科学最基础的构件出发，推断出未来那些全新技术背后的运作原理**
## 知识点总结
1. **编译compile** -- we needed to convert that **source code** in C to **machine code**, the 0's and 1's in binary that the computer understood.`make hello`
2. **编译器compiler** -- make命令自动调用了实际的Clang编译器。
3. **编译器命令**手动调用编译器需要运行 the raw compiler command(not make!)，比单纯的make命令更复杂
4. **手动clang编译** -- `clang hello.c` -- compile hello.c into an executable program.(`a.out`Assembler Output汇编器输出 is the default name of a program that's created when you just run Clang by itself)。输入`./a.out`可以运行程序，但这个名称并不能描述程序功能。接下来尝试增加命令行参数`-o`来指定输入的文件名称为hello
5. **命令行参数** -- clang命令支持**命令行参数command line arguments**
6. **-o限定输出** -- `clang -o hello hello.c` -- 通过`-o`指定输出名称为hello. `-o` means change Clang's output to be a file called **hello** instead of the default, which is **a.out**.
7. **-l链接第三方库** --  `clang -o hello hello.c -lcs50` -- 手动使用clang编译时若想调用`get_string`函数，光`#include <cs50.h>`是不够的[^1]，编译器虽然知道函数存在，却找不到函数实现的二进制文件（函数的声明和实现），我们还需要**链接**这步：`-l`会把CS50的所有二进制库文件链接到我们的代码里。*使用任何非内置的第三方库，都需要-l链接；对于内置标准库（standard library，带std的）则不需要。*
8. **make**不止适用于CS50，在C、C++都广泛使用
9. **编译** -- **preprocessing(预处理)、compiling(编译)、assembling()、linking(链接)
10. **Preprocessing预处理** -- C语言里的特殊符号`#`被称为**预处理指令preprocessor directive** -- anything with a **hash** symbol here(like`#include <cs50.h>`) should be preprocessed-- that is, analyzed initially before anything else happens.任何带有#的语句都会被预处理，也就是先于别的代码被初步分析。
11. **Where are those header files?(cs50.h & stdio.h)** -- 在code spaces终端键入`ls /usr/include`可见
12. **cs50.h** -- 文件里是所有CS50函数的**函数声明**function declaration（or函数原型functions prototype)，没有函数实现！所有CS50库中的函数原型，合并到一个名为cs50.h的单独文件中，这样就不必每次使用库里的函数时，都麻烦地手动输入或者复制粘贴 -- 只要include整个cs50.h，编译器会自动为我们复制粘贴过来——这是clang在第一步预处理中做的事情。
13. 函数实现一般在.c文件、函数声明在.h文件
14. **preprocessing预处理** -- clang找到所有带#的语句，将.h文件的内容（函数声明）复制粘贴到我们的代码中
15. **compiling编译** -- C code ➡assembly code汇编代码
16. **assembling汇编** -- assembly code ➡machine code(0、1)
17. **linking链接** -- 
18. 各数据类型所占字节：
- `bool` 1 byte
- `int` 4 bytes
- `long` 8 bytes
- `float` 4 bytes
- `double` 8 bytes
- `char` 1 byte
- `string` ? bytes
19. **打印出字符的ASCII代码**：
- `%c`--打印单字符
- `%i`--打印单字符对应的ASCII代码
20. ASCII图表![[Pasted image 20240620214714.png]]
21. `a to A`小变大、减32
22. 两个新库：
- `#include <string.h>`--strlen ...
- `#include <ctype.h>`--toupper ...
23. `argc & argv[]`注意运行的程序名字也是命令行参数哦！`argv[0] -> ./greet` 
24. `echo $?`检查程序退出状态

[^1]: 在手动clang编译`hello name`代码时，会报错`get_string的未定义引用`，尽管添加了cs50头文件，clang即使知道get_string函数存在，也无法找到实现函数的二进制，需要**链接**这步——`clang -o hello hello.c -lcs50`
## bug重现
（决定以后这一栏会写一些**萌新错误**，一报错就能发现，但写的时候总是不小心忽略/出错的bug）

- [?] 在检查命令行参数的条件语句中，出错后打印错误信息，还应该......==~~记得return 1啊亲爱的QAQ~~==
- [?] 在遍历字符串的时候，`if (int i = 0, l = strlen(s); i++)`这段代码问题在哪？==~~天哪为什么初始化两个变量的时候，就总是漏掉条件判断**i < l**呢？？？？~~==

## week2心得体会
- [!] <font color=orange>🐤橡皮鸭鸭调试法！</font>

超超超可爱！`♥++`（我不管就是要用小鸡的emoji，谁让它比小鸭🐥的emoji更可爱一点呢( ˘ ³˘)♥
- [!] 🐮cowsay!

🐤ducksay! 🐉dragonsay!
## lecture2 Notes
### Compiling编译
#### clang编译器
- `clang hello.c`编译后输出文件夹a.out
- `clang -o hello hello.c`指定输出文件夹为名称为hello
- `clang -o hello hello.c -lcs50`使用第三方库时（非std）需要链接
#### 编译四步骤
1. **preprocessing预处理**
**预处理**：clang找到所有`#include`开头的行，进行全局查找和替换——clang找到这些头文件，把内容复制粘贴到我们的代码中，这样我们的代码就包含了所需get_string、printf和其他库里各种函数的原型

🙋‍：cs50.h、stdio.h这些文件在哪呢？
🐤：在终端键入`ls /usr/include`能看到在云端这个文件夹里的所有内容
🙋‍：**include**文件里**所有原型**还是单纯**所需函数原型**
🐤：**所有**。之前一个简单的hello, world程序，对应的机器码是大量的0和1，就是因为很多0和1来自于这些实际上并不一定需要的代码。

2. **compiling编译**
to assembly code 
3. **assembling汇编**
to machine code
4. **linking链接**
combine things together
### debugging调试
1. 设置**断点**breakpoint
2. 在终端键入`debug50 ./buggy0`在调试器里运行程序
3. 程序在断点处暂停：
- step over运行下一行
- step into进入这一行（一般是进入函数实现）

4. 对有命令行参数的代码的调试：`debug50 ./caesar key`

### Array
> Arrays are a way of storing data back-to-back in memory such that this data is easily accessible.
#### 声明数组
##### **声明数组的方法：**
- `int array[3];`
- `int scores[] = {72, 73, 33};`
- `bool letters[26] = {false}`创建一个布尔数组，长度为26，初始化每个元素为false（来自pset2--substitution）

 ##### **引入：**
```c
// code scores.c
#include <stdio.h>

int main(void)
{
	int score1 = 72;
	int score2 = 73;
	int score3 = 33;

	printf("Average: %i\n", (score1 + score2 +score3) / 3);
}
```
**声明多个同类型变量时可以考虑用数组**：引入数组array`int scores[3]`，不需要单独声明int score1、2、3再给每个变量赋值。可以先告诉计算机，请给我一个叫scores的数组，大小为3，其中每个都是int。这就是在C语言里声明一个**数组**，会分配连续12个字节来储存3个整数

- [!] ==定义多个同类型变量用数组！==

##### **数组元素的索引：**
`array[i]`用方括号+序号访问数组，注意从零开始索引
```c
// 提示用户输入三门课成绩并输出平均值
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    int scores[3];
    for (int i = 0; i < 3; i++)
    {
        scores[i] = get_int("Score: ");
    }

    printf("Average: %f\n", (scores[0] + scores[1] +scores[2]) / (float) 3);
}
```
#### 传递数组为函数参数
> Not only can arrays be containers: They can be passed between functions.
> 数组不仅可以用作数据容器，还可以作为参数在不同的函数之间传递。

把数组作为函数参数传递，**抽象**出**计算平均值**的部分，封装成函数average()：
```c
// 把数组作为函数参数传递
#include <cs50.h>
#include <stdio.h>

const int N = 3;

float average(int length, int array[]);

int main(void)
{
    int scores[N];
    for (int i = 0; i < N; i++)
    {
        scores[i] = get_int("Score: ");
    }

    printf("Average: %f\n", average(N, scores));
}

float average(int length, int array[])
{
    int sum = 0;
    for (int i = 0; i < length; i++)
    {
        sum += array[i];
    }
    
    return sum / (float) length;
}
```
### String
> A `string` is simply an array of variables of type `char`: an array of characters.
> string就是字符数组而已
#### 字符串结束符
字符串就相当于一个数组（在内存里紧挨着的一个个单字符）
🙋‍：内存里字符串如何表示结束？
🐤：
> 人们多年前就定下来用数组来实现字符串，在每个字符串数组的末尾，都需要额外添加一个字节储存空字符`\0`，明确表示字符串到此结束，在这个字节里存有所谓的哨兵值。ASCII代码`0->NUL`

#### 字符串数组string array
（🚫禁止套娃喵！）
```c
#include <cs50.h>
#include <stdio.h>

int main(void)
{
	string words[2];

	words[0] = "HI!";
	words[1] = "BYE!";

	printf("%c%c%c\n", words[0][0], words[0][1], words[0][2]);
	printf("%c%c%c\n", words[1][0], words[1][1], words[1][2], words[1][3]);
}
```
- `words[0]`在数组words里索引到第一个元素`HI!`
- `words[0][0]`进一步地在字符串`HI!`里索引到第一个字符`H`
#### 计算字符串的长度：
**手动循环：**
```c
// 计算字符串长度（手动循环）
#include <cs50.h>
#include <stdio.h>

int main(void)
{
    // 提示用户输入字符串
    string s = get_string("String: ");

    // Count number of characters up until '\0' (aka NUL)
    int n = 0;
    while (s[n] != '\0')
    {
        n++;
    }
    printf("%i\n", n);
}
```
- 用while循环，索引每个字符直到空字符，并计数。

**函数封装：**
（把刚刚计算字符串长度的代码用函数封装起来）
```c
// 将计算字符串的代码抽象成函数
#include <cs50.h>
#include <stdio.h>

int length(string s);

int main(void)
{
    // 提示用户输入字符串
    string s = get_string("String: ");

    // 调用函数计算字符串长度并打印
    printf("%i\n", length(s));
}

int length(string s)
{
    int n = 0;
    while (s[n] != '\0')
    {
        n++;
    }
    
    return n;
}
```
- 其实已经有人写过这个函数啦！认识一个新库：**string.h**(字符串相关函数库)，内含计算字符串长度的函数**strlen()**

逻辑上确定为小写字母：`if (s[i] >= 'a' && s[i] <= 'z')`
在底层实现上，字符只是一个数字，大写字母和小写字母之间总是相隔32。小变大：`s[i] - 32`(可以用ctype库中的toupper函数)

> [!NOTE]+ toupper
> ⚠`int toupper(char c)`注意toupper()函数处理的是**单个字符**，不接收字符串作为参数(来自pset2--substitution--bug)

### 命令行参数
#### argc & argv[]
main函数的两种格式：
- `int main(void)`
- `int main(int argc, string argv[])`

argc是命令行参数的数量；argv相当于一个数组，是用户在命令提示符$后输入的所有字符（单词）
终端键入`./greet David`此时：
`argc == 2`
`argv[0]`--`./greet`
`argv[1]`--`David`

命令行参数：在提示符$后键入的所有字符（大概）

#### cowsay
`$ cowsay moo`🐮有话想说~
`$ cowsay -f duck quack`更改🐮的外观为--鸭鸭！🐤`-f`
`$ cowsay -f dragon RAWR`更改外观为凶猛的喷火巨龙🐉！RAWR~!

### exit  status
（退出代码、退出状态）like 404 error、not found

让我们看看main函数：
```c
		int main(void)
		 ^         ^
	返回一个int |没有命令行参数

```
main函数总是会返回一个整数，默认返回0。我们可以更改程序出错时的返回代码，来检查程序是否正常工作：
```c
#include <stdio.h>

int main(int argc, string argv[])
{
	if (argc != 2)
	{
		printf("Missing the command-line argument\n");
		return 1;
	}
	else
	{
		printf("hello %s\n", argv[1]);
		return 0;
	}
}
```
命令`echo $?`可以帮我们查看程序的退出状态

### cipher
```c
 plaintext, key ➡ ciphertext
				 ^
			   ciper
```

## Shorts
### Functions
函数的声明declaration、定义definition、调用call
```c
return-type name(argument-list)
^                      ^
返回值类型   逗号分隔的参数集，每个参数都是类型+名称的形式
```
练习：valid_triangle()--判断三边是否可以组成▲
```c
// function declaration
bool valid_triangle(float a, float b, float c);

// function definition
bool valid_triangle(float a, float b, float c)
{
	// 检查正数
	if (a <= 0 || b <= 0 || c <= 0)
	{
		return false;
	}

	// 检查两边之和大于第三边
	if (a + b <= c || a + c <= b || b + c <= a)
	{
		return false;
	}

	// 都满足返回真
	return true;
}
```

### Variable Scope
全局变量globle variabel & 局部变量local variable
函数有作用域的问题，这里提到的“按值传递”在week4会更加详细地解释
```c
int increment(int x);

int main(void)
{
	int x = 1;
	int y = 0;
	increment(x);
	y = increment(x);

	printf("x = %i, y = %i\n", x, y);
}

int increment(int x)
{
	x++;
	return x;
}
```
这段代码运行后实际上会输出`x = 1, y = 1`，也就是x的值不变，y加一。要注意在main函数里第3行调用增量函数时，并没有改变x的值，传递进increment函数的只是x的副本（按值传递）；只有在第4行，将调用增量函数的返回值，**赋值**给main函数中的local variabel "y"，这时才改变了main函数中的变量。而在increment中的`x++`并不能在函数被调用之后，改变main函数中的变量x

## 课后作业
### [[CS50x2024 problem set & practice#pset2|pset2]]
### [[CS50x2024 problem set & practice#week2|practice2]]
## ❓写lab和pset遇到的问题：
- 在no-vowels中**不会定义一个接受string做参数，并返回string的函数**。switch语句我只会print输出，该怎么return呢?
⬆这就是我第一次写这个作业时的奇怪问题啊~当时我还没有完全理解自定义函数的没有返回值void和有返回值分别是怎么一回事——来自2024.06.28的吐槽
# week3 Algorithms
[lecture3中文精翻](https://www.bilibili.com/video/BV1jN4y197WA/?spm_id_from=pageDriver&vd_source=dab7ee9d5c2d604b3bf4fe7298837d4f)
[week3网站](https://cs50.harvard.edu/x/2024/weeks/3/)
[notes](https://cs50.harvard.edu/x/2024/notes/3/)

> computer scientists discuss efficiency in terms of **the order of** various running times.
## 知识点总结
- 判断字符串相等的函数`strcmp(s1, s2) == 0`(string.h)
- 在检查用户输入的命令行参数时，错误情况记得`return`，如：
```c
if (argc < 2)
{
	printf("Usage:...");
	return 1;
}
```

## bug重现
## week3心得体会
## lecture3 notes

### 时间复杂度
- 在使用大$O$符号时，我们不关心**小阶项**(smaller order terms).即$O(n)$与$O(\frac{n}{2})$视为相同，它们算法图像的形状也是非常相似的。
![[Pasted image 20240625202713.png]]随着n->∞，这些算法的表现会非常相似，没有量级上的效率区别。对数可以忽略底数$O(\log n)$也是一个意思
- 分析算法效率的常用公式速查表：
- [*] $O(n^2)$ --- selection sort & bubble sort
- [*] $O(n\log n)$
- [*] $O(n)$ ----------- Linear search
- [*] $O(\log n)$  ------- Binary search
- [*] $O(1)$ 
- 以上$\mathbf{O(n^2) \longrightarrow O(1)}$按**慢⟶快**排列。
- 最好的$O(1)$，也就是无论n如何变化，执行算法的步骤都是一个常量。时间复杂度从概念上来说，表示的是算法执行效率**随着数据规模n增长**的**变化趋势**，不管这些常量的执行会花费多少功夫，我们都可以忽略掉，因为它跟n无关，不会影响到“增长趋势”。
> best is so-called order of 1, like one step or maybe two steps, maybe even 1,000 steps, but **a fixed, finite number of stpes** that **never changes no matter how big n is**.

- 大$O$ -- **上界upper bound** -- 通过大$O$表示法能衡量出**最坏**情况下算法的效率 -- 算法最多要多少步？课程的例子：线性查找最坏是7步（即n步），二分查找是$\log_2 7 \approx 3$步。（即$\log_2 7$
- $\Omega$ -- **下界lower bound** -- **最好**的情况 -- 算法最少要多少步？在课程的例子中：线性查找和二分查找最少都是一步，即$\Omega(1)$
- [*] $\Omega(n^2)$ --- selection sort
- [*] $\Omega(n\log n)$
- [*] $\Omega(n)$ --- bubble sort
- [*] $\Omega(\log n)$
- [*] $\Omega(1)$   ---  Linear search & Binary search
- $\Theta$ -- 表示上界和下界重合 -- 比如统计教师的学生人数1、2、3...这种数数的时间复杂度就是$\Theta(n)$ -- 最好最坏的情况都要数n名学生
- [*] $\Theta(n^2)$ --- selection sort
- [*] $\Theta(n\log n)$
- [*] $\Theta(n)$
- [*] $\Theta(\log n)$ 
- [*] $\Theta(1)$ 
- **总结**：
1. $O$ (大$O$) 表示上界(upper bound)，时间复杂度$O(f(n))$表示该算法的运行时间在**最坏**的情况下以$f(n)$的量级增长；
2. $\Omega$ (Omega) 表示下界(lower bound)，时间复杂度$\Omega(f(n))$表示该算法的运行时间在**最好**的情况下以$f(n)$的量级增长；
3. $\Theta$ (Theta) 表示紧确界(tight bound)，适用于上界和下界一致的情况。
4. 大$O$表示法使用的最为广泛，大部分情况下最能说明算法的效率。

### Search
> Find a element inside of an array查找数组内部元素的算法
1. **Linear search -- int**
```c
// Linear search -- int
#include <cs50.h>
#include <stdio.h>

int main(void)
{
	// An array of ints
    int numbers[] = {20, 500, 10, 5, 100, 1, 50};

	// Search for int
    int n = get_int("Number: ");
    for (int i = 0; i < 7; i++)
    {
        if (n == numbers[i])
        {
            printf("Found!\n");
            return 0;
        }
    }
    printf("Not found.\n");
    return 1;
}
```
- 在for、while语句里都可以用break跳出循环，但这里用return结束程序才是最合适的。（虽然我已经完全熟悉这个了，不过还是当第一次学一样乖乖**记在小本本上**哈哈(～￣▽￣)～
- 这里介绍了声明数组的第二种方法（早在上周的作业“scrabble拼字游戏”里就见过了喵~）
- [*] 请注意在循环里硬编码的数字“7”......
2. **Linear search -- string**
```c
// Linear search -- string
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
	// An array of strings
    string numbers[] = {"one", "two", "three", "four", "five", "six"};

	// Search for string
    string s = get_string("Number: ");
    for (int i = 0; i < 7; i++)
    {
        if (strcmp(numbers[i], s) == 0)
        {
            printf("Found!\n");
            return 0;
        }
    }
    printf("Not found.\n");
    return 1;
}
```
⬆请在5秒内找出以上代码的问题（5、4、3、2、1、0！）
> [!hibox]
> 在查找一个“数组里不包含的string”（如“seven”）时，会发生**段错误 segment fault**，原因是之前硬编码的“7”反过来咬了我们一口！在字符串数组里只有6个元素，第7次循环访问了不该操作的内存！

- **比较字符串相等***：简单`s == number[i]`是错误的，这在下一周学习了指针后解释==~~字符串实际上只是第一个字符在内存里的地址，比较两个地址当然永远是不同的~~==
在这里我们用到了`string.h`中的**strcmp函数**来比较两个字符串是否相等，它的函数原型是`int strcmp(string s1, string s2)`，在相等时返回0

> [!NOTE]+ 错误代码error codes
> 当程序越来越复杂时，要学着像工业环境里面的程序员一样，**在出错时给出错误码**，return0是最简单的表示程序正常运行的方式，返回错误代码是一种程序不按预期运行的信号。以后，在一些大型项目里，我们可能会希望实现软件自动化，代替手动运行程序，我们希望在某些时候代码能自动化地执行一些任务。**利用好退出代码，程序就能够确定其他代码是运行成功还是失败**。

> [!note]+ Linear search 算法效率分析
> 最**坏**的情况：目标元素在数组的最后一位或不存在在数组中，此时$O(n)$
> 最**好**的情况：目标元素在第一个位置，一步即可完成搜索，$\Omega(1)$

### Data Structures
- [!] 引入：
```c
#include <cs50.h>
#include <stdio.h>
#include <string.h>

int main(void)
{
    // Arrays of strings
    string names[] = {"Carter", "David", "John"};
    string numbers[] = {"+1-617-495-1000", "+1-617-495-1000", "+1-949-468-2750"};

    // Search for name
    string name = get_string("Name: ");
    for (int i = 0; i < 3; i++)
    {
        if (strcmp(names[i], name) == 0)
        {
            printf("Found %s\n", numbers[i]);
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}
```
如果name和number能相互关联，在查找name的时候就自动找到number。上面这种实现虽然有效，但显然是很糟糕的设计，容易出错且效率低下。
> if we could create our own data type where we could associate a person with the phone number?

- [!] C语言允许我们创建自己的数据结构、自定义数据类型！

- 以前我们创建数组：`int number[] = {...}`
	- 创建一个叫做number的数组，里面包含有相应的多个int类型变量。number -- 数组名称；int -- 数组元素数据类型。
- 现在我们创建数组：`person people[] = {...}`
	- 创建一个叫做people的数组，里面包含有相应的多个person类型变量！people -- 数组名称；person -- 数组元素数据类型。

**person类型变量**就是我们自定义的数据类型！

- [!] 接下来看看如何发明自己的person类型：

我们的person类型希望能将表示name和number的这两个string数据类型封装起来，合并成一种新的、改进的数据类型，做一层抽象，直接叫做person......
```c
typedef struct
{
	string name;
	string number;
}
person;
```
- [*] C语言有一个关键字typedef(type define) -- allow you to define your own type
- [*] struct 表明这是一整个structure(结构体) -- It's like a structure that has multiple values inside of it that you are trying to define.在这个结构体里面，有多个你要定义的值
- [*]  在`person;`后的每一行都可以访问person类型，此时我们可以像使用`int`一样使用`person`类型！
	- [x] 可以创建单个变量：`person p;`
	- [x] 也可以是整个数组：`person people[2];`
```c
// 自定义person数据类型储存名字和号码
#include <cs50.h>
#include <stdio.h>
#include <string.h>

typedef struct
{
    string name;
    string number;
}
person;

int main(void)
{
    // 将两人的信息以person类型存在数组中
    person people[2];

    people[0].name = "Carter";
    people[0].number = "+1-652-986-2681";

    people[1].name = "David";
    people[1].number = "+1-875-211-3248";

    // 获取用户输入姓名
    string name = get_string("Name: ");

    // 查找姓名并打印对应号码（如果有）
    for (int i = 0; i < 2; i++) // 硬编码只求方便，并不是好设计
    {
        if (strcmp(people[i].name, name) == 0)
        {
            printf("Found %s\n", people[i].number);
            return 0;
        }
    }
    printf("Not found\n");
    return 1;
}
```
- 这里更多是为了展示“如何定义”`typedef`以及“怎么把名字和数字放在person里面”的语法`.name`，
- 记住访问内存中person属性的语法：
	- 单个变量：`person p;`
		- `p.name = "Alnilam"`
		- `p.number = "+86-4ln1l2m"`
	- 整个数组：`person people[2];`
		- `people[0].name = "Juhayna"`
		- `people[0].number = "+86-7uh2yn2"`


> [!NOTE]+ 线性查找总结
> 以上这种“糟糕的设计”只是为了展示**struct的使用和相关的新语法`访问结构体的各属性如.name`**。等到一两周后，我们会开始把信息保存到文件里，会学到用逗号作为分隔符的csv文件，还有电子表格文件等等。很快就会学习**如何把姓名和号码等等信息存进文件**。到那时，就不像现在这样硬编码数字2，也不用在程序里手动输入名字和号码，**我们将从文件里动态读取信息**。*We'll read information dynamically from a file*.再几周后，我们会从数据库里动态读取数据。而现在，仅仅是介绍怎么用新语法创建一个大小为2的person类型数组。我们可以更新第一个人、第二个人的姓名和号码，还可以搜索这些姓名并打印出相应的号码。从这个意义上来说，代码设计得更好了——因为在这个用途不多的程序里面，person数据类型概括并包含了一个人需要的所有信息，它不再是零散的names数组、numbers数组等等人的单独属性，**一切被封装起来，放到一个数据类型里面作为属性**。*It's all encapsulated, which is a term of art inside of the same type*.我们可以很容易在结构体里添加新属性（如address），读写存入，和person关联在一起。
> 最终，我们会用文件、数据库来存储名称、数字或其他信息，不会再出现这种冗余的写法。简单几行代码就可以从文件或数据库中读取信息，然后把这些数据填进整个数组！*Forgive the bad design by design today!*

### sorting
几种排序的**可视化**效果：https://visualgo.net/en/sorting?slide=1

如果数据排好序就可以二分查找了！
关于**先排序再搜索**与**不排序直接搜索**的trade off（权衡）......
- ***selection sort(选择排序)***
```c
For i from 0 to n-1
	Find smallest number between number[i] and number[n-1]
	Swap smallest number with number[i]
```


显然无论是否中途已经完成了排序，我们都需要把所有的循环检查完才能确定

**算法的效率：**
对n个数字进行排序，首先找到第一个最小元素，需要的**比较次数：n - 1**；往后找第2、第3个最小元素需要n-2、n-3步...总共需要的比较次数为：
$$(n-1)+(n-2)+(n-3)+...+1$$
也就是一个**等差数列的和**：
$$\frac{n(n-1)}{2}$$
展开得：
$$n^2/2-n/2$$
当n越来越大，$n^2$占主导地位，经过简单得分析我们可以说**选择排序的上限**是：$O(n^2)$

考虑一下最好的情况：
即使是数字已经有序的情况下，选择排序所需要的步骤也不会减少，也就是它的下限也是：$\Omega(n^2)$
因此可以说，选择排序算法的效率是：$\Theta(n^2)$

- ***bubble sort(冒泡排序)***
```
Repeat n-1 times
    For i from 0 to n–2
        If numbers[i] and numbers[i+1] out of order
            Swap them
    If no swaps
        Quit
```
我们只聚焦两位元素，反复交换，让最大的元素逐渐浮出水面。当某次循环交换次数为0时，证明已经排序完成，可以退出程序。

**算法的效率：**
可以说冒泡排序每重复一次，都让一个最大的数字浮出水面，当重复n-1次时（*伪代码第1行*），所有数字就排好了；而每一个数字浮出水面需要进行比较的次数是：n-1（*伪代码第2行*）。总共需要比较的次数为：
$$(n-1)*(n-1)$$
展开：
$$n^2-2n+1$$
当n趋近无穷大时，我们可以说**冒泡排序的上限**是：$O(n^2)$

考虑数字已经有序的最好情况：
只需要进行一次遍历，发现没有交换就退出循环，总共的比较次数是n-1，即**冒泡排序的下界是**：$\Omega(n)$。在数据已经**有序的情况**下，冒泡排序的效率比选择排序高得多

- ***merge sort(归并排序)***
```
If only one number
    Quit
Else
    Sort left half of number
    Sort right half of number
    Merge sorted halves
```
归并排序总结为四个字：**分而治之！**(divide and conquer)
学习归并排序之前先了解***递归***：
### recursion
> Looking for [[CS50 notes#week3 Algorithms#lecture3 notes#recursion|recursion]]?
- **递归的含义**：当一个函数调用它自身，就说这个函数是递归的。*如在二分查找里伪代码`search the left/right` 就可以视为在一种搜索算法search里又使用了search，这个伪代码在做递归*
- **Google递归小彩蛋**：试试在Google搜索“recursion”？
- **递归的两个条件**：1. 递归终止条件(*无限制的递归只会触发段错误*)；2. 问题规模不断缩小(base case)。
- **分而治之**：先**分**，分到了base case再**治之**

用递归来解决pset1马里奥金字塔的例子：

> [!NOTE]+ 马里奥金字塔recursion
> ```c
> // 递归马里奥金字塔，启动！
> #include <cs50.h>
> #include <stdio.h>
> 
> void draw(int n);
> 
> int main(void)
> {
> 	// 提示用户输入高度
> 	int height = get_int("Height: ");
> 	
> 	// 打印金字塔
> 	draw(height);
> }
> 
> void draw(int n)
> {
> 	// 终止条件
> 	if (n == 0)
> 	{
> 		return;
> 	}
> 	
> 	// 调用函数
> 	draw(n - 1);
> 	
> 	// 打印一行
> 	for (int i = 0; i < n; i++)
> 	{
> 		printf("#");
> 	}
> 	printf("\n");
> }
> ```


## Shorts
### Bubble Sort
**In pseudocode:**
- Set **swap counter** to a non-zero value
- Repeat until the swap counter is 0:
	- Reset swap counter to 0
	- Look at each adjacent pair(相邻的对)
		- If two adjacent elements are not in order, swap them and add one to the swap counter

加入**swap counter**(交换计数)，当交换次数为0时(表示排序已完成)，退出循环。

### Recursion
- [!] shorts也有`recursion`的彩蛋哦！==~~当然这个笔记里也藏着recursion的彩蛋啦(✿◡‿◡)~~==
> Looking for [[CS50 notes#week3 Algorithms#Shorts#Recursion|recursion]]?

---
递归地定义一个函数时，需要：
- **base case**
	- 停止递归条件a simple solution to a problem which stops the recursive process from occurring.
- **recursive case**
	- 递归实际发生的地方，函数调用自身的地方。它不会以与被调用时完全相同的方式调用自身，而是每一次调用都让问题变得更小

> In general, but not always, **recursive functions** replace **loops** in non-recursive functions.

***factorial function ($n!$) ***
数学中的阶乘
$$
n!=n \times (n-1) \times ... \times 2 \times 1
$$
- **recursion version**
	- $fact(1) = 1$
	- $fact(n) = n \times fact(n - 1)$
```c
int fact(int n)
{
	// Base case
	if (n == 1)
		return 1;
	// Recursive case
	else
		return n * fact(n-1);
}
```
- **iterative version**
```c
int fact(int n)
{
	int product = 1;
	while (n > 0)
	{
		product *= n;
		n--;
	}
	return product;
}
```

多个`base case`和`recursive case`
***Collatz猜想***
- Repeat
	- if $n = 1$
		- stop
	- else
		- if n = even
			- $n = n / 2$
		- if n = odd
			- $n = 3*n + 1$

递归地定义collatz函数，计算`n to 1`的步数：
```c
// Collatz
#include <cs50.h>
#include <stdio.h>

int collatz(int n);

int main(void)
{
	// Get a positive integer
	int n = 0;
	do
	{
		n = get_int("A positive integer: ");
	}
	while (n < 1);
	// Print the steps of n to 1
	printf("Back to 1 takes %i steps.\n", collatz(n));
}

int collatz(int n)
{
	// Base case
	if (n == 1)
		return 0;
	// Recursive case
	else if (n % 2 == 0)
		return 1 + collatz(n / 2);
	else
		return 1 + collatz(3 * n + 1);
}
```
## pset3
- 线性查找linear search

**在mian里return可以表示程序执行完成**
```c
int main(void)
{
    // 定义一个静态数组
    int numbers[] = {20, 500, 10, 5, 100, 1, 50};
    // 获取用户输入的想要查找的数字
    int n = get_int("Number: ");

    for (int i = 0; i < 7; i++)
    {
        if (numbers[i] == n)
        {
            printf("Found\n");
            return 0;
            // 这里的return非常重要，可以让程序直接结束到24（debug结论）
            // 后来00:40:44老师也讲到了，return可以表示程序执行完成
            // 也就是说不会在Found后，退出循环了还继续往下执行25的Not found
        }
    }
    printf("Not found\n");
    return 1;
}
```
- 线性查找---字符串

**判断字符串相等不能像int一样用：**
```c
if (string[i] == s)
```
我们使用string库中的strcmp()函数：**(实际上就是某人用循环遍历了字符串中各个单字符判断是否相等)**
```c
if (strcmp(string[i], s) == 0)
```
# week4 Memory
## **指向int的指针**
```c
int n = 50; // 声明一个变量n，储存的是一个整数int的值value
int *p = &n; // 声明一个变量p，*表示p是一个指针，储存的是一个整数int的地址address
printf("%p\n", p); // 0x123可以根据变量名p得到它的地址
printf("%i\n", *p); // 50也可以反过来从地址取到那个变量
```
⬆line3在打印p的值（n的地址）时，没有用%i，因为在操作系统里指针point一般占8bytes，和占4bytes的整数int不同。p的值虽然是整数（比如0x123），但是是特殊的表示地址的整数，这个特殊性，我们用特殊的格式化字符%p

> [!指针的地址？]
> 指针p的值是n的地址，在内存上会给p一个地方，也就是p本身也有地址，试试打印出指针p的地址？（我们并不关心指针的地址在哪Who cares?重要的是藏宝图的地址（打印出来%p，p），go to藏宝图所在地（*p）

```c
printf("%p\n", *p);
```
## **指向字符串string的指针**
```c
string s = "HI!";
```
- 卸下辅助轮：
```c
char *s = "HI!";
```
- 在声明字符串时，实际上变量s是储存了首字符“H”的地址的一个指针
想打印出HI! **字符串就是首字符的地址而已！**
```c
char *s = "HI!";

printf("%s\n", s); // HI!
```
- 为什么不需要*(go to the address)?
在printf里%s就可以去到藏宝图背后的地址打印出值，直到NULL。如果用*则会go to the address打印出这个地址的值，也就是第一个字符的值"H"：
```c
printf("%c\n", *s) // H
```
与指向int的指针对比理解一下：
```c
printf("%s\n", s); // HI! 需要地址，s就是地址，直接用变量就好
printf("%p\n", p); // 0x123 需要地址，p就是地址，也直接用变量
printf("%i\n", *p); // 50 需要藏宝图背后的宝藏，去到地址看到值
```

> [!note]+ 关于%s
>printf想知道的不是 s 这个字符的值value是什么，而是这个字符的地址address是什么，这样才可以往后遍历，到空字符收尾。也就是%s虽然不像%p直接打印出变量p的地址，但%s也和它一样只需要变量的地址address，如果再加上解引用得到的就是s这个地址的值（首字符值H）这不是我们想要的。(printf函数里肯定有解引用实现“根据得到的首字符地址往后遍历到空字符，并打印出来”。但如果我们自己解引用 *s 得到的只有第一个字符的值，所以把地址交给printf，解引用的事也交给printf)
> **给printf一个地址，它能往后一直打印到空字符！**

^printf

想打印出s在内存的地址：
```c
printf("%p\n", s); // 0x123
```
s本来就是一个地址，直接%p打印就好
```c
printf("%p\n", s); // 0x123
printf("%p\n", &s[0]); // 0x123
```
其他字符的地址：
```c
printf("%p\n", &s[0]); // 0x123 s[0]是一个char，不是指针，要用&
printf("%p\n", &s[1]); // 0x124
printf("%p\n", &s[2]); // 0x125
printf("%p\n", &s[3]); // 0x126
```
当然，如果声明指针把各个字符的地址存起来就可以像打印第一个字符一样了：
```c
char *s = "HI!"
char *i = s[1];
char *j = s[2];
......
printf("%p\n", s); // 0x123
printf("%p\n", i); // 0x124
printf("%p\n", j); // 0x125
......
```

> [!note]+ 连续的地址
> 数组里面所有字符都是紧挨着的连续的单字节，上面分别打印出H、I、！、NULL的地址时可以发现它们是连续的

- **指针算数运算（试试打印出每一个字符？）**
曾学过的语法糖：
```c
printf("%c\n", s[0]); // H
printf("%c\n", s[1]); // I
......
```
在底层，方括号实际上：
```c
printf("%c\n", *s); // H go to the address            ---0x123
printf("%c\n", *(s+1)); // I                ---0x123+1---0x124
printf("%c\n", *(s+2)); // !                ---0x123+2---0x125
```
string只是一个字符序列，每个字符只占一个字节，而且字节是连续的，**我们可以去到内存里任何想去的地方！**

- 试试打印出字符串和它的子串？
```c
printf("%s\n", s); // HI!
printf("%s\n", s+1); // I!
printf("%s\n", s+2); // !
```
这里就用到了[[#^printf]]里的知识啦！
> [!note]+ 单引号和双引号
> - "C里时用双引号括起字符串string，在内存里会自动添加“\0”这个额外字节"
> -  '而单引号括起的char就不会如此'

- 比较字符串== 与strcmp

> [!failure]+ \==错误比较字符串
> ```c
> char *s = get_string("s: "); // 输入HI!
> char *t = get_string("t: "); // 输入HI!
> 
> if (s == t) // s和t都是地址
> {
> 	printf("Same!");
> }
> ```

s == t 只会比较首字节的地址，一般情况下不会相同，所以尽管两次输入都是HI!，结果还是Different

用strcmp函数：(前人写好的，其实就是挨个字符比较)
```c
if (strcmp(s, t) == 0) // 字符串相等时strcmp返回0
{
	printf("Same!");
}
```
- 按值复制
- 避免未预料到的用户输入导致的段错误（防御性编程）
- malloc内存分配 ==return首字节地址==
- free释放内存
> [!note]+ 电脑死机？
> 电脑死机或挂起时，系统可能会自动重启，可能的原因是：一个程序有bug，不断申请内存但永远不free，导致最后计算机耗尽所有内存崩溃。

- 标准库stdlib包含malloc和free
- malloc申请内存的防御性编程：(要加上一个空字符的内存)
```c
char *t = malloc(strlen(s) + 1);
```
注意当指针指向整数或其他数据类型时，malloc
- 在复制时注意循环要到最后一位空字符(否则如果尝试print出t的值时，将会往后打印出很多随机值，直到碰巧遇见\0)
```c
for (int i = 0, n = strlen(s) + 1; i < n; i++)
{
	t[i] = s[i];
}
```
- 复制字符串的函数strcpy(目标t, 源s)
```c
strcpy(t, s);
```

- get_string、malloc函数在出现问题时会返回NULL
```c
char *t = malloc(strlen(s) + 1);
if (t == NULL)
{
	return 1;
}
......
free(t); // malloc申请内存后一定要记得释放！！！
```
- 复制字符串
```c
#include <cs50.h>
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h> // 包含malloc和free
#include <string.h>

int main(void)
{
	char *s = get_string("s: ");
	if (s == NULL)
	{
		return 1;
	}
	
	char *t = malloc(strlen(s) + 1);
	if (t == NULL)
	{
		return 1;
	}
	
	for (int i = 0, n = strlen(s) + 1; i < n; i++)
	{
		t[i] = s[i];
	} // 用strcpy函数可以去掉循环

	if (strlen(t) > 0)
	{
		t[0] = toupper(t[0]);
	}

	printf("s: %s\n", s);
	printf("t: %s\n", t);

	free(t); // 在最底部释放内存

	return 0;
}
```
- 手动为数组申请内存sizeof(int)
```c
int *x = malloc(3 * sizeof(int)); // x存储的是申请到的内存首字节地址
```
想想之前的：
```c
int x[3];
```
一个int占4字节，会申请3 * 4 = 12个字节
- 检查段错误Seg faults---valgrind
$ valgrind ./memory
- 不初始化的变量，内存里有很多垃圾值
- 如果定义指针时没有初始化（未分配内存，指针没有指向任何地址），这时直接解引用go to the address 会发生不好的事情：

> [!failure]+ 错误示例：解引用未初始化指针
> ```c
> int *y; // y是一个指针
> *y = 13; // 对进行解引用，把13赋值
> ``` 

应该在赋值之前为指针分配内存，并指向它：

> [!success]+ 正确示例：在解引用前先为指针分配内存(初始化)
> ```c
> int *y;
> y = malloc(size(int));
> *y = 13;
> ```

- swap时的按值传递和按地址传递
按值传递：

> [!failure]+ 按值传递无法实现swap
> ```c
> void swap(int a, int b);
> 
> int main(void)
> {
> 	int x = 1;
> 	int y = 2;
> 
> 	printf("x is %i, y is %i\n", x, y);
> 	swap(x , y);
> 	printf("x is %i, y is %i\n", x, y);
> }
> 
> void swap(int a, int b)
> {
> 	int tmp = a;
> 	a = b;
> 	b = tmp;
> }
> // 编译运行：x is 1, y is 2
> // x is 1, y is 2
> ```

按地址传递：

> [!success]+ 按地址传递
> ```c
> void swap(int *a, int *b);
> 
> int main(void)
> {
> 	int x = 1;
> 	int y = 2;
> 	
> 	printf("x is %i, y is %i\n", x, y);
> 	swap(&x, &y); 
> 	printf("x is %i, y is %i\n", x, y);
> }
> 
> // ⬇swap的参数是两个指向整数的指针(地址)，这里的*不是解引用的意思
> void swap(int *a, int *b)
> {
> 	int tmp = *a; // 右go to a取值，左把a的值传给tmp
> 	*a = *b; // 右go to b取值，左go to a，把b的值传给a
> 	*b = tmp; // go to b，把tmp的值传给b。这三行的*都是解引用
> }
> // 编译运行：x is 1, y is 2
> // x is 2, y is 1
> ```

按地址传递解决了作用域scope的问题
- heep overflow---堆溢出malloc向下申请内存
- stack overflow---栈溢出调用函数向上使用内存，main、......栈帧
- 丢下辅助轮！尝试写写get_int、get_string
```c
#include <stdio.h> // 😊不导入cs50了喵！

int main(void)
{
	int n;
	printf("n: ");
	scanf("%i", &n); // 不要\n
	printf("n is %i", n);
}
// get_int实现！get!
```
注意一个可能出错的地方：(其实就是自己的bug..QAQ

> [!failure]+ 调用scanf时错误接住返回值
> ```c
> int n = 0;
> n = scanf("%i", &n);
> printf("%i\n", n); // 不管输入什么，结果：1
> ```
注意`scanf("%i", &n)`就已经实现了获取用户输入的值，并go to n改变n的值。如果还加上多余的【赋值】操作`n = scanf("%i", &n)`，就会把scanf的返回值1赋值给n

> [!note]+ 关于scanf为什么要加&
> scanf()两个参数：一个参数是格式代码format code---%i（要scan扫描用户键盘上输入的一个整数），一个参数是用来存放这个整数的**地址**---&n。scanf函数go to the address and change the value of n.前往n的地址，并改变n的值将用户输入的值保存在那。如果不加&就是按值传递了，只能是一个n的副本进入scanf函数，并不能改变n的值。

- File I/O
```c
FILE *file = fopen("phonebook.csv", "a");
```
fopen---以“appending(a)"的形式打开一个文件“phonebook.csv
还有reading(r)、writing(w)模式
fopen返回一个指向文件的指针。文件的地址存入(指针)变量file，指针file指向的是一个文件FILE
>[!note]+ fopen
>fopen函数---打开文件并返回地址(每次调用fopen后都要调用fclose)

检查fopen是不是返回NULL：(可能文件没找到)
```c
if (file == NULL)
{
	return 1;
}
```
>[!note]+ 检查是否返回NULL
>任何时候一个函数返回一个指针，都要检查它是否出了问题返回NULL。如malloc、get_string、fopen......
- fprintf---printing to that file(指向文件的指针变量名，后面和printf相同)
```c
fprintf(file, "%s%s\n", name, number);
```
## lab & pset
### filter
- sepia部分困扰了好久的bug
```c
image[i][j].rgbtRed = sepiaRed(image[i][j].rgbtRed, image[i][j].rgbtGreen, image[i][j].rgbtBlue);

image[i][j].rgbtGreen = sepiaGreen(image[i][j].rgbtRed, image[i][j].rgbtGreen, image[i][j].rgbtBlue);

image[i][j].rgbtBlue = sepiaBlue(image[i][j].rgbtRed, image[i][j].rgbtGreen, image[i][j].rgbtBlue);
```
在第一条语句执行后，后面函数里传递的参数值就变了