# Unit1
## Unit1.1
***(Boolean Expression to Truth table)***
***公式(formular)➡真值表(truth table)***：每个可能的值代入公式填表就行了
### Commutative Laws(交换律)
> ***>> x AND y = y AND x***
>***>> x OR y = y OR x***

### Associative Laws(结合律)
>***>> x AND (y AND z) = (x AND y) AND z***
>***>> x OR (y OR z) = (x OR y) OR z***

### Distributive Laws(分配律)
>***>> x AND (y OR z) = (x AND y) OR (x AND z)***
>***>> x OR (y AND z) = (x OR y) AND (x OR z)***

### De Morgan Law(德摩根定律)
>***>> NOT(x AND y) = NOT(x) OR NOT(y)***
>***>> NOT(x OR y) = NOT(x) AND NOT(y)***

### Idempotence Law(幂等定律)
>***w AND w = w***

### Double Negation Law(双重否定定律)
>***NOT(NOT(x)) = x

## Unit1.2
***(Truth table to Boolean expression)***
### AND、OR、NOT
***真值表➡公式***：只关注value为1的行，写出每一个让单独这一行成立的表达式，最后用OR连接起来。

|  x  |  y  |  z  |   f   |
| :-: | :-: | :-: | :---: |
|  0  |  0  |  0  | ==1== |
|  0  |  0  |  1  |   0   |
|  0  |  1  |  0  | ==1== |
|  0  |  1  |  1  |   0   |
|  1  |  0  |  0  | ==1== |
|  1  |  0  |  1  |   0   |
|  1  |  1  |  0  |   0   |
|  1  |  1  |  1  |   0   |
>***>> NOT(x) AND NOT(y) AND NOT(z) ==OR==***
>***>> NOT(x) AND y AND NOT(z) ==OR==***
>***>> x AND NOT(y) AND NOT(z) 

***通过这种方法我们得出：所有的布尔表达式都可以用AND、OR、NOT三个操作符构建起来***

> [!summary]
> ***Any Boolean function can be represented using an expression containing AND、OR and NOT operations.*** 

### AND、NOT
👣***进一步***
由于De Mogen Laws，OR可以用AND和NOT表示
> ***> NOT(x OR y) = NOT(x) AND NOT(y)***
> ***>> x OR y = NOT(*** NOT(x) AND NOT(y) ***)***

> [!summary]
> 所以我们可以省去NOT，***“所有的布尔函数都可以用AND、NOT两个操作符来表示！”***

### NAND
***(仅当输入都为1时，输出为0。相当于对AND的否定)
x NAND y = NOT(x AND y) ------公式0***

|  x  |  y  | NAND  |
| :-: | :-: | :---: |
|  0  |  0  |   1   |
|  0  |  1  |   1   |
|  1  |  0  |   1   |
|  1  |  1  | ==0== |
👣***更进一步***
NOT和AND都可以用NAND表示
>***>> NOT(x) = (x NAND x) ------公式1*** 
>***>> 结论：NAND可以表示NOT***
>***>> x AND y = NOT(x NAND y) ------使用公式0
>= (x NAND y) NAND (x NAND y) ------使用公式1***
>***>> 结论：NAND可以表示AND

> [!summary]
> ***所有的布尔函数都可以仅用NAND操作符来构建！与非门！***

## Unit1.3 Logic Gates

interface --- what
implementation --- how
一个interface可以有不止一种实现方式
## Unit1.4 HDL
Hardware Description Language
### XOR gate(异或门)

|  a  |  b  | out |
| :-: | :-: | :-: |
|  0  |  0  |  0  |
|  0  |  1  |  1  |
|  1  |  0  |  1  |
|  1  |  1  |  0  |
(nota AND b) OR (a AND notb)
HDL是一种函数式functional or declarative声明式语言

### 多路复用器
真值表

|  a  |  b  | set | out |
| :-: | :-: | :-: | :-: |
|  0  |  0  |  0  |  0  |
|  0  |  1  |  0  |  0  |
|  1  |  0  |  0  |  1  |
|  1  |  1  |  0  |  1  |
|  0  |  0  |  1  |  0  |
|  0  |  1  |  1  |  1  |
|  1  |  0  |  1  |  0  |
|  1  |  1  |  1  |  1  |
