# pset
## pset1
## pset2
[pset2](https://cs50.harvard.edu/x/2024/psets/2/)
### Scrabble
```c
// 拼字游戏
#include <cs50.h>
#include <ctype.h>
#include <stdio.h>
#include <string.h>

int calculate(string s);

// A->Z共26个字母的得分数组
int scores[] = {1, 3, 3, 2, 1, 4, 2, 4, 1, 8, 5, 1, 3, 1, 1, 3, 10, 1, 1, 1, 1, 4, 4, 8, 4, 10};

int main(void)
{
    // 提示两名玩家输入单词
    string word1 = get_string("Player1: ");
    string word2 = get_string("Player2: ");

    // 计算单词得分
    int score1 = calculate(word1);
    int score2 = calculate(word2);

    // 输出游戏结果
    if (score1 > score2)
    {
        printf("Player 1 wins!\n");
    }
    else if (score1 < score2)
    {
        printf("Player 2 wins!\n");
    }
    else
    {
        printf("Tie!\n");
    }
}

// 计算玩家输入的单词得分
int calculate(string s)
{
    int sum = 0;
    for (int i = 0, l = strlen(s); i < l; i++)
    {
        if (isupper(s[i]))
        {
            sum += scores[s[i] - 'A'];
        }
        else if (islower(s[i]))
        {
            sum += scores[s[i] - 'a'];
        }
    }
    
    return sum;
}
```
- 遍历单词中的每个字母，每个字母的得分通过在scores数组中索引得到，`index = 大写字母 - 'A'` 或` index = 小写字母 - 'a'`
- 注意只对字母计分，不算符号。因此在calculate函数里必须用if else 嵌套条件语句，如果简单归为“if大写/else非大写”，就没有考虑标点符号的问题。
### Readability
```c
// 阅读水平测试
#include <cs50.h>
#include <ctype.h>
#include <math.h>
#include <stdio.h>
#include <string.h>

int count_letters(string text);
int count_words(string text);
int count_sentences(string text);

int main(void)
{
    // 提示用户输入文本
    string text = get_string("Text: ");

    // 对文本中的字母、单词、和句子计数
    int letters = count_letters(text);
    int words = count_words(text);
    int sentences = count_sentences(text);

    // Compute the Coleman-Liau index
    float l = (letters / (float) words) * 100;
    float s = (sentences / (float) words) * 100;
    int index = round(0.0588 * l - 0.296 * s - 15.8);

    // Print the grade level
    if (index < 1)
    {
        printf("Before Grade 1\n");
    }
    else if (index >= 1 && index <= 16)
    {
        printf("Grade %i\n", index);
    }
    else
    {
        printf("Grade 16+\n");
    }
}

// Return the number of letters in text
int count_letters(string text)
{
    int sum = 0;
    for (int i = 0, l = strlen(text); i < l; i++)
    {
        if (isalpha(text[i]))
        {
            sum++;
        }
    }

    return sum;
}

// Return the number of words in text
int count_words(string text)
{
    int sum = 1;
    for (int i = 0, l = strlen(text); i < l; i++)
    {
        if (text[i] == ' ')
        {
            sum++;
        }
    }

    return sum;
}

// Return the number of sentences in text
int count_sentences(string text)
{
    int sum = 0;
    for (int i = 0, l = strlen(text); i < l; i++)
    {
        if (text[i] == '.' || text[i] == '!' || text[i] == '?')
        {
            sum++;
        }
    }

    return sum;
}
```
- 计算**字母**数量。用到ctype库中的函数**isalpha(char c)**，遍历文本中的每个字符，条件判断“是字母”时，计数菌+1
- 计算**单词**数量。单词数 = 空格数 + 1。只要看文本中有多少空格就行了喵~
- 计算**句子**数量。也就是计算标点符号`. ! ?`的数量啦！简单！
- 最后打印年级时需要用到math库中的**四舍五入**函数round()
### Caesar
[Caesar](https://cs50.harvard.edu/x/2024/psets/2/caesar/)
凯撒算法：c = (p + k) % 26
```c
// 凯撒密码
#include <cs50.h>
#include <ctype.h> // isdigit(),isalpha(),isupper()
#include <stdio.h>
#include <stdlib.h> // atoi()
#include <string.h> // strlen()

bool only_digits(string s);
char rotate(char c, int i);

int main(int argc, string argv[])
{
    // 检查命令行参数数量
    if (argc != 2)
    {
        printf("Usage: ./caesar key\n");
        return 1;
    }

    // 检查用户输入key是否为数字
    if (!only_digits(argv[1]))
    {
        printf("Usage: ./caesar key\n");
        return 1;
    }

    // 将string类型的key转换为int
    int key = atoi(argv[1]);

    // 提示用户输入明文
    string plaintext = get_string("plaintext: ");
    printf("ciphertext: ");

    // 调用rotate函数将明文转换为密文，并打印
    for (int i = 0, l = strlen(plaintext); i < l; i++)
    {
        printf("%c", rotate(plaintext[i], key));
    }
    printf("\n");
}

// 对字符串中每一个字符遍历，判断是否为数字
bool only_digits(string s)
{
    for (int i = 0, l = strlen(s); i < l; i++)
    {
        // ctype库中的isdigit()函数只适用于char
        if (!isdigit(s[i]))
        {
            return false;
        }
    }
    return true;
}

// 根据凯撒算法c = (p + k) % 26来加密字母
char rotate(char c, int i)
{
    // 非字母时直接返回
    if (!isalpha(c))
    {
        return c;
    }

    // 字母分大小写两种情况
    else if (isupper(c))
    {
        return ((c - 'A' + i) % 26) + 'A';
    }
    else
    {
        return ((c - 'a' + i) % 26) + 'a';
    }
}
```
- [!] 思路：
1. main函数接受命令行参数，**获取用户输入的key**
2. **检查命令行参数数量**（是否按要求`./caesar key`）
3. 检查**key是否为数字**（`only_digits()`函数）
4. **将key从string转换为int**（命令行参数是string类型，需要用**stdlib**库中的`atoi()`函数，将string转换为int类型）
5.  **提示用户输入明文**
6. **调用rotate函数**将明文**加密**为密文
7. **only_digits()函数实现**：遍历字符串key的每个字符，挨个用**ctype库**中的`isdigit(char c)`函数，检查是否为数字
8. **rotate()函数的实现**：接受一个明文的**单字符**和**密钥**，返回一个密文的**单字符**。
- 注意在`c = (p + k) % 26`中，c、p都是字母的索引（A--0、B--1...），得到明文的索引需要字母**减去'A'或'a'**，通过计算得到密文的索引后，还要**加上'A'或'a'**才能正确输出密文字母
- 好几次bug都是在检查命令行参数错误后忘记添加`return 1;`这行代码
### Subsititution
作业链接：https://cs50.harvard.edu/x/2024/psets/2/substitution/
代码实现：
```c
// 字母替换加密（定制版）
#include <cs50.h>
#include <ctype.h>
#include <stdio.h>
#include <string.h>

bool letters_26(string s);
bool unique_letters(string s);
char rotate(char c, string s);

int main(int argc, string argv[])
{
    // 检查命令行参数数量
    if (argc != 2)
    {
        printf("Usage: ./substitution key\n");
        return 1;
    }

    string key = argv[1];

    // 检查key是否为26个字母
    if (!letters_26(key))
    {
        printf("Key must contain 26 characters.\n");
        return 1;
    }

    // 检查26个字母是否有重复
    if (!unique_letters(key))
    {
        printf("Key must not contain repeated characters.\n");
        return 1;
    }

    // 提示用户输入明文
    string plaintext = get_string("plaintext: ");

    // 调用函数rotate转为密文，并打印
    printf("ciphertext: ");

    for (int i = 0, l = strlen(plaintext); i < l; i++)
    {
        printf("%c", rotate(plaintext[i], key));
    }
    printf("\n");
}

// 检查key是否是26个字母
bool letters_26(string s)
{
    // 如果长度不等于26，直接返回false
    if (strlen(s) != 26)
    {
        return false;
    }

    // 长度为26时再检查是否全为字母
    for (int i = 0; i < 26; i++)
    {
        if (!isalpha(s[i]))
        {
            return false;
        }
    }
    return true;
}

// 检查26字母是否不重复
bool unique_letters(string s)
{
    bool letters[26] = {false};

    for (int i = 0; i < 26; i++)
    {
        int index = toupper(s[i]) - 'A';
        if (letters[index])
        {
            return false;
        }
        letters[index] = true;
    }
    return true;
}

// 将明文转换为密文
char rotate(char c, string s)
{
    // 非字母直接返回
    if (!isalpha(c))
    {
        return c;
    }

    // 大写字母转换后返回
    if (isupper(c))
    {
        return toupper(s[c - 'A']);
    }

    // 小写字母转换后返回
    return tolower(s[c - 'a']);
}
```
- [!] **思路**：
1. 从命令行参数获取用户的**替换密钥key**
2. 检查key是否符合期待：
	- 检查命令行参数数量是否为2（即`./substitution key`的形式）
	- 检查key是否为26个字母（即检查**长度为26**且每个字符都是**字母**）（letters_26函数实现）
	- 检查key是否为**不重复**的字母（unique_letters函数实现）
1. 提示用户输入明文
2. 明文转换为密文，挨个字符打印（rotate函数实现）
- [x] 自定义函数代码实现：
1. ==letters_26()==

**函数功能**：接收一个字符串，检查其是否为**26**个**字母**，返回一个布尔值
**函数实现**：strlen函数检查字符串长度；遍历字符串，调用isalpha函数进行单字符【是/非字母】的严格排查！

2. ==unique_letters()==

**函数功能**：接收一个字符串，检查其中字母是否重复。*这里我硬编码了26，是因为前面已经确定了字母的数量一定为26，为了减少strlen()的调用次数才如此。如果想要写一个函数，能判断任一个长度<=26的字符串是否有重复字母，就可以改成`int l = strlen(s)`、`bool letters[l] = {false}`、`i < l`*
**函数实现**：使用一个**布尔数组**记录每个字母是否已经出现过，确保每个字母在密钥中只出现一次。

- 创建一个布尔数组 `bool letters[26] = {false};`，长度为26，对应26个字母。
- 初始化数组中的每个元素为 `false`，表示字母未出现过。
- 遍历密钥字符串中的每个字母，`toupper`将其转换为大写字母（统一处理大小写），然后计算其在数组中的索引index。
- 如果该索引位置的值`letters[index]`已经是 `true`，则表示字母重复，返回 `false`。
- 如果该索引位置的值是 `false`，则将其设置为 `true`，继续检查下一个字母。
- 如果遍历完成后没有发现重复字母，则返回 `true`。

声明一个**布尔数组**还是第一次喵！

- [<] 代码改进过程：
1. **去掉了`letters_26`和`rotate`里不必要的else语句**：当一个条件分支以`return`结束时，不需要`else`。
2. 把`string key = argv[1]`移到检查26个字母之前，因此调用`letters_26`和`unique_letters`函数时，传入的参数是`key`而非`argv[1]`，可能会更清晰明了一点~

## pset3
### plurality(多数选举)

# practice
练习题🔗：https://cs50.harvard.edu/x/2024/practice/
## week1
## week2
### no-vowels
代码实现：
1. 使用命令行参数
```c
// Write a function to replace vowels with numbers
// Get practice with strings
// Get practice with command line
// Get practice with switch

#include <cs50.h>
#include <stdio.h>
#include <string.h>

string replace(string s);

int main(int argc, string argv[])
{
    // 检查命令行参数数量
    if (argc != 2)
    {
        printf("Usage: ./no-vowels word\n");
        return 1;
    }

    // 调用replace函数更改元音，并打印
    printf("%s\n", replace(argv[1]));
}

string replace(string s)
{
    for (int i = 0, l = strlen(s); i < l; i++)
    {
        switch (s[i])
        {
            case 'a':
                s[i] = '6';
                break;
            case 'e':
                s[i] = '3';
                break;
            case 'i':
                s[i] = '1';
                break;
            case 'o':
                s[i] = '0';
                break;
            default:
                break;
        }
    }
    return s;
}
```
2. 不使用命令行参数
```c
// 元音变数字！
#include <cs50.h>
#include <stdio.h>
#include <string.h>

string replace(string s);

int main(void)
{
    // 获取用户输入的单词（小写）
    string word = get_string("word: ");
    // 调用replace函数将元音变数字，并打印
    printf("%s\n", replace(word));
}

string replace(string s)
{
    for (int i = 0, l = strlen(s); i < l; i++)
    {
        switch (s[i])
        {
            case 'a':
                s[i] = '6';
                break;
            case 'e':
                s[i] = '3';
                break;
            case 'i':
                s[i] = '1';
                break;
            case 'o':
                s[i] = '0';
                break;
            default:
                break;
        }
    }
    return s;
}

// 关于作业描述留下的思考问题：
// “为什么要使用命令行参数而不是 get_string 、 get_int 等？”
// 不 知 道 啊！我这用get_string不是好好的嘛
// 我不觉得这里的设计比用命令行参数差啊
```

### password
代码实现：
```c
// Check that a password has at least one lowercase letter, uppercase letter, number and symbol
// Practice iterating through a string
// Practice using the ctype library

#include <cs50.h>
#include <ctype.h>
#include <stdio.h>
#include <string.h>

bool valid(string password);

int main(void)
{
    string password = get_string("Enter your password: ");
    if (valid(password))
    {
        printf("Your password is valid!\n");
    }
    else
    {
        printf("Your password needs at least one uppercase letter, lowercase letter, number and "
               "symbol\n");
    }
}

// TODO: Complete the Boolean function below
bool valid(string password)
{
    // 定义四个布尔变量，储存密码中这些字符的状态
    bool is_upper = false;
    bool is_lower = false;
    bool is_digit = false;
    bool is_symbol = false;

    // 定义一个字符数组储存符号集
    const char symbols[] = "!\"#$%&'()*+,-./:;<=>?@[\\]^_`{|}~";

    // 遍历密码，找到相应字符类型就修改状态
    for (int i = 0, l = strlen(password); i < l; i++)
    {
        // 有大写字母吗？
        if (isupper(password[i]) && (!is_upper))
        {
            is_upper = true;
        }

        // 有小写字母吗？
        if (islower(password[i]) && (!is_lower))
        {
            is_lower = true;
        }

        // 有数字吗？
        if (isdigit(password[i]) && (!is_digit))
        {
            is_digit = true;
        }

        // 有符号吗？
        if (!is_symbol)
        {
            for (int j = 0; j < sizeof(symbols) - 1; j++)
            {
                if (password[i] == symbols[j])
                {
                    is_symbol = true;
                    break;
                }
            }
        }
    }

    // 前面四关都通过了吗？
    if (is_upper && is_lower && is_digit && is_symbol)
    {
        return true;
    }

    return false;
}

```

## week3