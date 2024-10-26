# getchar()

## 1.大致介绍

getchar是读取单个字符的函数，要读取多个字符请用gets()。

好玩  很巧妙的点就是getchar用中文输入法打出来是个体插入 get char。

## 2.getchar的返回值和类型

1.getchar会返回int类型的值 即输入字符的asc值。

2.如果结束或者读取失败会返回EOF（本质上是-1）。

## 3.工作原理

1.输入函数都是从缓冲区读取键盘中的输入，如果缓冲区以及有了数据，会直接读取，不用输入。

2.特殊举例：

getchar（）；

当你向其中输入a 实际上输入的是a\n,但getchar每次只能读取一个字符，下一次getchar（）再读取时会直接把\n读取了

3.清空

由举例我们可以知道只要把缓冲区清空就可以了，此时我们只要加上getchar（）来清空缓存区即可。

## 4.代码示例

### 1.连续三个字符串



```c
#include <stdio.h>
#include <string.h>

int main()
{
 int ch = 0;
 while((ch = getchar()) != EOF)
       printf("%c",ch);//putchar(ch);等价
 return 0;      
}
```

输入Ctrl+Z来退出

### 2.判断是不是字母

## 描述

KiKi想判断输入的字符是不是字母，请帮他编程实现。

### 输入描述：

多组输入，每一行输入一个字符。

### 输出描述：

针对每组输入，输出单独占一行，判断输入字符是否为字母，输出内容详见输出样例。



```c
#include <stdio.h>

int main()
{
  char a;
    while((a = getchar() != EOF))//循环读取
    {
        getchar();//特殊例子所用到的，如果没有就会在下次读取一个\n
    if(a>='a'&&a<='z')||(a>='A'&&a<="Z")
        printf("%c is an alphabet.\n",a);
    else
        printf("%c is not an alphabet",a);
            
    }
  return 0;
}
```

### 3.输入密码

**题目：输入一个字符串，自己判断是否为正确的密码，如果正确输入 Y 否则输入 N ，在进行**

**字符判断 为 Y 输出“确认成功”否则输出“确认失败”。**

```c
#include<stdio.h>
int main()
{
	char password[20] = { 0 };
	printf("请输入密码:>");
	scanf("%s", password);
	printf("请确认密码(Y/N):>");
	int ch = getchar();
	if (ch == 'Y')
	{
		printf("确认成功\n");
	}
	else
	{
		printf("确认失败\n");
	}
	return 0;
}
```

这样会出现和特殊示例一样的问题 用getchar（）来清理'\n'

```c
#include<stdio.h>
int main()
{
	char password[20] = { 0 };
	printf("请输入密码:>");
	scanf("%s", password);
	getchar();//把缓冲区中的\n清理掉
	printf("请确认密码(Y/N):>");
	int ch = getchar();
	if (ch == 'Y')
	{
		printf("确认成功\n");
	}
	else
	{
		printf("确认失败\n");
	}
	return 0;
}
```

那假如输入密码中间有空格呢 scanf读取到空格就会停下来

所以有

```c
//把缓冲区中的内容全读走
	while ( getchar() != '\n')
	{
		;
	}
```

最终

```c
#include<stdio.h>
int main()
{
	char password[20] = { 0 };
	printf("请输入密码:>");
	scanf("%s", password);
	//把缓冲区中的内容全读走
	while (getchar() != '\n')
	{
		;
	}
	puts(password);  // 验证输入的字符串
	printf("请确认密码(Y/N):>");
	int ch = getchar();
	if (ch == 'Y')
	{
		printf("确认成功\n");
	}
	else
	{
		printf("确认失败\n");
	}
 
	return 0;
}
```

## 还有一些杂七杂八的项比如说两个getchar等等，之后看到第八章再来补充