第四章 字符串和格式化输入/输出
====================================================================

.. Note::

    本章介绍以下内容：
     - 函数 strlen()
     - 关键字：const
     - 字符串
     - 如何创建、存储字符串
     - 如何使用strlen()函数获取字符串的长度
     - 用C预处理器指令#define和ANSIC的const修饰符创建符号常量

本章重点介绍输入和输出。与程序交互和使用字符串可以编写个性化的程序，本章将详细介绍C语言的两个输入/输出函数printf()和scanf()。 最后简要介绍一个重要的工具-C预处理指令，并学习如何定义、使用符号常量。

4.1 前导程序
------------------------------------------------------------------

程序清单4.1talkback.c程序

 .. literalinclude:: code/code4-1.c
    :language: c


改程序包含了一下新特性:
    - 使用数组储存字符串
    - 使用%s转换说明来处理字符串的输入和输出，注意在scanf()中，name，没有&前缀，而weight有。
    - 用C预处理器把字符常量DENSITY定义为62.4
    - 用C函数strlen()获取字符串的长度。



写到这里的时候有个小插曲，编译的时候提示::

    WARNING: Could not lex literal_block as "c". Highlighting skipped.

经检查上面的4-1的代码发生了错误，然后发现是双引号和单引号的区别 ， 这个还能检查语法错误呢。不错。

4.2 字符串简介
------------------------------------------------------------------

字符串是一个或多个字符的序列

4.2.1 char类型数组和null字符
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

C语言没有专门用于存储字符串变量类型，字符串都被存储在char类型的数组中，数组由连续的存储单元组成，字符串中的字符被存储在响铃的存储单元，每个单元存储一个字符。

字符串末尾字符\0 ，这是空字符，C语言用来标记字符串的结束。空字符不是数字0 ，他是非打印字符。

4.2.2 使用字符串
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

程序清单4.2 praise1.c
 .. literalinclude:: code/code4-2.c
    :language: c

C语言还有其他输入函数，如fgets() 用于读取一般字符串。后面会详细介绍。


4.2.3 strlen() 函数

用于获取字符串长度

 .. literalinclude:: code/code4-3.c
    :language: c


如果使用ANSI C之前的编译器 必须移除这一行::

    #include <string.h>

string.h 头文件包含多个与字符串相关的函数原型，包括strlen()。

另外值得注意的一点，之前使用sizeof 使用了圆括号 本例中没有使用，但还是建议所有情况下都写上圆括号。


4.3 常量和预处理器
------------------------------------------------------------------

定义常量::

    #define NAME value

这样就是定义了预处理的常量了

4.3.1 const关键字
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

C90标准新增const关键字，用于限定一个变量只读::

    const int MONTHS = 12;

const用起来比#define更灵活。

4.3.2 明示常量
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

C头文件limits.h 和float.h 分别提供了整数类型和浮点数类型大小限制相关的详细信息，

4.4 printf() 和scanf() 
------------------------------------------------------------------ 
输入输出函数

4.4.1 printf() 函数
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ 

.. list-table:: 表4.3转换说明及其打印的输出结果
   :header-rows: 1

   * - 转换说明
     - 输出
   * - %a
     - 浮点数、十六进制和p计数法 C99、C11
   * - %A
     - 浮点数、十六进制和p计数法 C99、C11
   * - %c
     - 单个字符
   * - %d
     - 有符号十进制整数
   * - %e
     - 浮点数、e计数法
   * - %E
     - 浮点数、e计数法
   * - %f
     - 浮点数、十进制计数法
   * - %g
     - 根据值的不同，自动选择%f或%e，%e格式用于指数小于-4或者大于等于精度时
   * - %G
     - 根据值的不同，自动选择%f或%E，%E格式用于指数小于-4或者大于等于精度时
   * - %i
     - 有符号十进制整数 与%d相同
   * - %o
     - 无符号八进制整数
   * - %p
     - 指针
   * - %s
     - 字符串
   * - %u
     - 无符号十进制整数
   * - %x
     - 无符号十六进制整数，使用十九禁止数0f
   * - %X
     - 无符号十六进制整数，使用十六进制数0F
   * - %%
     - 打印一个百分号

4.4.2 使用printf()
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

略

4.4.3 printf() 的转换说明修饰符
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

略

4.4.4 转换说明的意义
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

转换说明应该与待打印的值类型相匹配。通常都有多种选择，例如打印int类型可以使用%d、%x、%o ,对应的打印double的值可以使用%
f、%e、%g

输出较长的字符串的时候，可以使用 \ 反斜杠换行。

4.4.5 使用scanf()
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

注意：
 - 如果使用scanf()读取基本变量的值，在变量名前面加上一个&
 - 如果使用scanf()把字符串读入字符数组中，不要使用&


4.5关键概念
------------------------------------------------------------------

C语言用char类型表示单个字符，用字符串表示字符序列。

在程序中，最好用#define定义数值常量，用const关键字声明的变量为只读。


4.6 本章小结
------------------------------------------------------------------ 

字符串是一系列被视为一个处理单元的字符，在C语言中，字符串是以空字符结尾的一系列字符

strlen()函数说获取字符串长度 

C预处理器为预处理器指令查找源代码，并在开始编译程序之前处理他们。













.. include:: ../../../ad.rst  


