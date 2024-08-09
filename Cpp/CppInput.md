# C++输入  

**

## 标准输入流与缓冲区

**stdin**是一个文件描述符（Linux）或句柄（Windows），它在 C 程序启动时就被默认分配好。在 Linux 中一切皆文件，stdin也相当于一个可读文件，它对应着键盘设备的输入。因为它不断地被输入，又不断地被读取，像流水一样，因此通常称作输入流。

stdin是一种行缓冲I/O。当在键盘上键入字符时，它们首先被存放在键盘设备自身的缓存中（属于键盘硬件设备的一部分）。只有输入换行符时，操作系统才会进行同步，将键盘缓存中的数据读入到stdin的输入缓冲区（存在于内存中）。所有从stdin读取数据的输入流，都是从内存中的输入缓冲区读入数据。当输入缓冲区为空时，函数将被阻塞。

若无特殊说明，以下所有的**缓冲区**均是指内存中的stdin输入缓冲区。用户程序中自定义的buffer数组、str数组等，将称作“数组”、“变量”，以免产生混淆。

**

## 基础函数

### scanf()

#### 函数原型

``int scanf(const char * restrict format,...);``

#### 说明

1. 如果成功，该函数返回成功匹配和赋值的个数。如果到达文件末尾或发生读错误，则返回 EOF
2. scanf需要按回车键才能完成该“行”数据的输入确认,而scanf对这个回车确认符并不进行处理，回车符会留在输入缓存区中。
因此，在下一个读“字符”操作函数（getchar, scanf("%c"), gets()等）运行时，会读到这个字符。
3. 在读数值型数据或字符串时，scanf()会从第一个非空白字符（空白字符指：回车，空格，TAB键）开始读取，自动忽略前面的空白字符，而遇到空白字符结束该类型数据的输入。
4. scanf单字符输入时规定只接收一个字符，且在遇到空白字符时空白字符会继续保留在缓冲区，所以在读取字符时，可能会出现如下情况
  
```cpp
    char c1,c2;
    scanf("%c %c",&c1,&c2);   //这里有一个空格
    printf("%d %d\n",c1,c2);
    scanf("%c%c",&c1,&c2);  //这里没有空格
    printf("%d %d\n",c1,c2);
    /*
    输入a b,对应输出为
    97 98
    10 97
    1.第一次输入a b 时 ，第一个scanf("%c %c")之间有一个空格，在输入字符a之后，我们可以输入空格，回车，那个空格会读取停止字符并释放掉，所以第一次输入正常
    2.第二次中，第二个%c读取的是缓冲区中的空格，故错误
    */
    //解决这个问题还可以用以下思路刷新缓冲
    fflush(stdin); //直接清除缓冲区，windows有效
    getchar(); //吃掉回车确认符
```

#### 格式控制符号

| 符号                   | 描述                                        |
| ---------------------- | ------------------------------------------- |
| %c                     | 单个字符,，包括空白字符(\t, \r, \n, 空格等) |
| %s                     | 字符串，遇到空白字符完成读取                |
| %d                     | 有符号十进制                                |
| %s                     | 无符号十进制                                |
| %i                     | 有符号可选进制数                            |
| %e, %E, %f, %F, %g, %G | 浮点数                                      |
| %lf, %le, %lg          | 双精度浮点数                                |
| %p                     | 指针                                        |
| %o                     | 八进制整数                                  |
| %x, %X                 | 十六进制整数                                |
| %%                     | 读取%                                       |

#### 实例

```c++
#include<iostream>
using namespace std;
int main() 
{ 
    int i1, i2, i3; 
    double d1, d2, d3;
    char s[10];
    scanf("%d%d%d", &i1, &i2, &i3); 
    scanf("%f%f%f", &d1, &d2, &d3); 
    scanf("%s", s);
    //以下是特殊用法
    //1.使用 scanf对 string 进行输入的方法
    string s;
    s.resize(10000);
    scanf("%s", &s[0]);
}
```

**

### gets()

#### 函数原型

`char *gets(char *str)`

#### 说明

1. 按下回车键时，从stdin读取一行  
2. 所有空格、Tab等空白字符均被读取，不忽略  
3. 按下回车键时，缓冲区末尾的换行符被丢弃，字符串末尾没有换行符\n，缓冲区也没有残留的换行符\n

#### 实例

```c++
#include<iostream>
using namespace std;
int main() 
{ 
    char str[100];
    gets(str);  
}
```

**

### fgets()

#### 函数原型

`char *fgets(char *str, int n, FILE *stream)`

#### 说明

1. 从指定的流 stream 读取一行，并把它存储在 str 所指向的字符串内
2. 当读取 (n-1) 个字符时，或者读取到换行符时，或者到达文件末尾时停止
3. 返回存储读取字符串的字符数组的指针，若到达文件尾端或出现错误，则返回空指针
4. 所有空格、Tab等空白字符均被读取，不忽略
5. 按下回车键时，缓冲区末尾的换行符也被读取，字符串末尾将有一个换行符\n

#### 实例

```c++
//读取文件流

char str[100];
memset(str, 0, sizeof(str));
int i = 1;
 
FILE *fp = fopen("...test.txt", "r");
if (fp == NULL) {
    printf("File open Error!\n");
    exit(1);
}
 
while (fgets(str, sizeof(str), fp) != NULL)
    printf("line%d [len %d]: %s", i++, strlen(str), str);
 
fclose(fp);

//读取stdin

char str[100];
memset(str, 0, sizeof(str));
int i = 1;
while (fgets(str, sizeof(str), stdin) != NULL)
    printf("line%d [len %d]: %s", i++, strlen(str), str);
```

**

### getchar()

#### 说明

1. 从stdin读取一个字符
2. 可用于清理缓冲区开头残留的换行符

#### 示例

```c++
char a;
a = getchar();
```

**

### cin

#### 说明

1. 标准输入流对象，istream类的一个对象实例
2. 有自己的缓冲区，但默认情况下与stdin同步
3. cin与stdin一样是行缓冲，即遇到换行符时才会将数据同步到输入缓冲区
4. 跳过开头空白字符，遇到空白字符停止读取，且空白字符（包括换行符）残留在缓冲区。如果不想跳过空白字符，可以使用流控制关键词noskipws，但这只对单个字符有效（类似于scanf中的%c）。

#### 实例

```cpp
int a, b;
cin >> a >> b;
char str[20];
cin >> str;
char c;
cin >> noskipws >> c;
```

### cin.get()

#### 说明

cin.get()读取指定长度个字符时，类似于 C 中的fgets()，但在换行符的处理上不同。它们都不会使换行符残留在缓冲区，但fgets()会将缓冲区末尾的换行符\n也写入字符串，而cin.get()会丢弃缓冲区末尾的\n。即：当输入test时，用fgets()读取得到的字符串长度为5，用cin.get()读取得到的字符串长度为4。

#### 实例

```cpp
char a, b;
char str[20];
 
// 读取一个字符，读取失败时返回0，多余字符残留在缓冲区（包括换行符）
a = cin.get();
 
// 读取一个字符，读取失败时返回EOF，多余字符残留在缓冲区（包括换行符）
cin.get(b);
 
// 在遇到指定终止字符（参数3）前，至多读取n-1个（参数2）字符
// 当不指定终止字符时，默认为换行符\n
// 如果输入的字符个数小于等于n-1（不含终止字符），则终止字符不残留在缓冲区
// 如果输入的字符个数多于n-1（不含终止字符），则余下字符将残留在缓冲区
cin.get(str, sizeof(str), '\n');
```

### getline()

#### 说明

1. 字符串流sstream的函数，只能用于读取数据给string类对象，使用时需要包含头文件string
2. getline()会读取所有空白字符，且缓冲区末尾的换行符会被丢弃，不残留也不写到字符串结尾。
3. 由于string对象的空间是动态分配的，所以会一次性将缓冲区读完，不存在读不完残留在缓冲区的问题。
4. 假如缓冲区开头就是换行符（比如可能是上一次cin残留的），则getline()会直接读取到空字符串并结束，不会给键盘输入的机会。这种情况下要注意先清除开头的换行符

#### 实例

```cpp
string str;
getline(cin, str);
```

**

## 应用

### [https://www.luogu.com.cn/problem/P1042]

首先可以想到这个方案

```cpp
string s = "", ss;
while (getline(cin, ss)) {
if (ss.size() == 0)
    break;
s += ss;
}
cout << s;
```

但是这显然不满足遇到E截止的问题

于是尝试

```cpp
char s[2501 * 25];
char ss;
int i = 0;
while (ss = getchar()) {
    if (ss == '\n')
        continue;
    if (ss == 'E') {
        i--;
        break;
    }
    s[i++] = ss;
}
```
