---
layout: post
title: "C语言笔记1"
date: 2023-6-23
categories: notes
---

#include <stdio.h> /* 标准输入输出库。这行代码告诉编译器包含标准输入/输出库，它提供了输入/输出操作的函数。 */
#include <stdlib.h> /* 标准库。这行代码告诉编译器包含标准库，它提供了一些通用函数，包括动态内存管理、随机数生成、与环境通信、整数运算、搜索、排序和转换。 */

// 定义阶乘函数
double factorial(int n) { /* 函数定义。函数接受一个整数n，返回一个double。 */
    double fact = 1; /* 声明并初始化一个double变量。这个变量存储在堆栈内存中。 */
    for(int i = 1; i <= n; i++) { /* for循环。循环变量i也存储在堆栈中。 */
        fact *= i; /* 乘法赋值运算符。它将变量fact乘以i，并将结果赋值给fact。 */
    }
    return fact; /* return语句。它结束函数，并将fact的值返回给调用者。 */
}

// 定义递归阶乘函数
double f(int n){ /* 递归函数定义。函数调用自身来计算n的阶乘。 */
    if (n == 0) /* if语句。它检查n是否等于0。 */
        return 1; /* 如果n是0，函数返回1。 */
    else
        return n*f(n-1); /* 如果n不是0，函数用参数n-1调用自身，并将结果乘以n。 */
}

// 定义汉诺塔函数
void hanno(int n, char a, char b, char c) { /* 函数定义。函数接受三个字符a, b, c和一个整数n作为参数，返回void。 */
    if (n==1) /* if语句。它检查n是否等于1。 */
    {
        printf("%c -> %c\n", a, c); /* printf函数。它打印字符a和c，中间有一个箭头。 */
    }
    else{
        hanno(n-1,a ,c, b); /* 递归函数调用。函数用参数n-1, a, c, b调用自身。 */
        printf("%c -> %c\n", a, c); /* printf函数。它打印字符a和c，中间有一个箭头。 */
        hanno(n-1, b, a, c); /* 递归函数调用。函数用参数n-1, b, a, c调用自身。 */
    }
}

int```c
main() /* main函数。每个C程序必须有一个main函数作为程序的入口点。 */
{
    // 汉诺塔问题
    hanno(2, 'a', 'b', 'c');

    // 组合数计算
    int m, n; /*声明两个整数变量m和n。这些变量存储在堆栈内存中。 */
    printf("Enter values for m and n: "); /* printf函数。它向标准输出打印一个字符串。 */
    scanf("%d %d", &m, &n); // 读取m和n /* scanf函数。它从标准输入读取两个整数，并将它们存储在变量m和n中。&运算符用于获取变量的地址。 */

    // 计算C(m, n)
    double result = factorial(m) / (factorial(n) * factorial(m - n)); /* 组合计算的结果存储在变量result中。这个变量存储在堆栈内存中。factorial函数被调用三次。函数调用的返回值用于计算。 */
    printf("C(%d, %d) = %f\n", m, n, result); /* printf函数。它将组合结果打印到标准输出。 */

    // 系统调用
    system("ping www.google.com"); /* system函数。它将命令"ping www.google.com"传递给主机环境，由命令处理器执行。 */

    // 递归阶乘计算
    int v = f(m); /* 递归阶乘函数f被调用，参数为m。结果存储在变量v中。这个变量存储在堆栈内存中。 */
    printf("%d\n",v); /* printf函数。它将整数v打印到标准输出。 */

    return 0; /* return语句。它结束main函数，并将值0返回给操作系统。返回值0通常表示程序已成功执行。 */
}

