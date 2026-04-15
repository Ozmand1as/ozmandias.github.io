# 分支循环
## 分支结构-if语句和switch语句
### if语句
C语言里，有两种分支语句**if**和**switch**用来实现分支结构。
先来介绍if语句：

### 1.if函数的基本写法
``` c
#include <stdio.h>
int main()
{
    if(表达式);//表达式里面写的是判断的条件，表达式成立，则执行；反之，则语句不执行
    {
    执行语句
    }
    return 0;
}
```
C语言中，**0为假，非0为真**，所以if语句的判断既可以使用表达式里进行判断，如果成立则为真，结果为非0，语句执行；如果不成立，则结果为0，语句不执行，也可以直接使用0(假)，非0(真)来直接放进去判断，效果相同。
if(表达式)示例如下:
```c
#include <stdio.h>
void Compare(int a, int b)
{
    if (a > b)//使用了if来判断a是否大于b
    {
        printf("A大\n");
    }
    else if (a < b)//使用了else if的嵌套来判断a是否小于b
    {
        printf("B大\n");
    }
    else//使用了else来判断最后一种情况a等于b的时候
    {
        printf("一样大\n");
    }
}

    int main()
    {
        int a = 0;
        int b = 0;
        printf("输入两个数比较大小：");
        scanf("%d%d", &a, &b);//输入两个数
        Compare(a,b);//自定义函数来判断a和b的大小
        return 0;
    }
```
在上面代码中分别使用了
- if
- else if
- else
else的使用，等会会解释。

**另外一种情况**
if()里面直接放0或者1
```c
#include <stdio.h>
int main()
{
	int a = 0;
	printf("请输入一个数来判断你是否要给我擦皮鞋:");
	scanf("%d", &a);
	if (1)//无论你填了什么，判断永远是真
	{
		printf("不管是什么,都要给我,擦皮鞋\n");
	}
	return 0;
}
```
上面代码中，if语句里面填的为非0(真)，所以里面的判断条件跟你输入什么都没有关系，不会影响输出结果，都会直接执行语句。

### 2.else
在第一个代码案例中，就已经使用了else。那else什么时候用呢？比如说一种情况，假如a和b是非0正整数，你要判断a和b谁大，那么就有三种情况
- A比B大
- A比B小
- A跟B一样大
if(表达式)
    语句1;
else
    语句2;
举个例子，
```c
#include <stdio.h>
int main()
{
    if (a > b)//使用了if来判断a是否大于b
    {
        printf("A大\n");
    }
    else
    {
        printf("B大\n");//err
    }
    return  0;
}
```
上面代码中if语句正常情况只能判断一种情况，那就是要么是成立（非0），要么不成立（0）。只能用来判断其中两个情况，但是情况一共可能有三种，所以计算机第一种情况外的两种情况都会执行第二种情况，比如：a和b一样大，那么也只会打印B大。
那如果想要判断更多情况那就需要使用if...else语句了。
### 3.if分支中包含多条语句
默认在if...else语句中默认都只控制一条语句，比如:
```c
#include <stdio.h>
int main()
{
	int a = 0;
	scanf("%d", &a);
	if (a == 0)
	{
		printf("数字为0\n");
	}
	else
	{
		printf("数字不是0\n");
	}
	return  0;
}
```
如果想要判断三种既以上，就要使用else if
示例如下：
```c
#include <stdio.h>
int main()
{
      if (a > b)//使用了if来判断a是否大于b
    {
        printf("A大\n");
    }
    else if (a < b)//使用了else if的嵌套来判断a是否小于b
    {
        printf("B大\n");
    }
    else//使用了else来判断最后一种情况a等于b的时候
    {
        printf("一样大\n");
    }
    return  0;
}
```
这样就可以用来判断多种情况了。

### 悬空else情况
在没什么经验的时候写代码会经常出现一些问题.
如果有多个if和else，记住，else总是跟**最接近**的if匹配
示例如下：
```c
#include <stdio.h>
int main()
{
    int a = 0;
    int b = 2;
    if(a == 1)
        if(b == 2)
            printf("heihei\n");
    else 
            printf("XD\n");
    return 0;
}
那么按理说a是0，不是1的情况下，会打印XD
但是实际上什么都不输出。
这就是悬空else问题，如果有多个if和else，可以记住，else总是跟**最接近**的if匹配
那么上面的问题该如何解决：
```c
#include <stdio.h>
int main()
{
    int a = 0;
    int b = 2;
    if(a == 1)
    {
        if(b == 2)
            printf("heihei\n");
    }
    else 
            printf("XD\n");
    return 0;
}
```
这样就代码就可以正常运行了。