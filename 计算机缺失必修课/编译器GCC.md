有了编译器GCC等等， 为什么要有make这个构建生成器，同样是老生常谈的内容。编译hello.c非常简单，只需要$ gcc hello.c就可以了，但当项目庞大起来后，假设hello.c依赖与a.c、b.c，而a.c又依赖于库w.lib，每一次编译，我们都要重新编写一次gcc编译命令行吗？所以，GNU发明了make这个工具软件，可以编写makefile文件来指定特定的项目构建过程，当项目一个文件的代码更改时，我们只需要重新make一下就可以了。  
但make依然有很多不足，比如make对于类unix系统是通用的，但对windows系统并不友好(不能跨平台)make语法简单，也就导致了它功能的限制不同编译器的语法规则不同，编写的makefile语法如果适合GCC则不适合MSVC所以，CMake就应运而生啦。  
CMake是比Make更高一层的工具，Make是编写对应编译器的makefile从而实现编译，而CMake是写一份独立的CmakeList.txt文件，然后该文件会根据当前系统环境选择适合的构建生成器（如VS或者make），然后将CmakeList.txt翻译为适合的文件，再进一步调用系统编译器进行项目构建。

```
  顺便再老生常谈一下程序的整个过程：
 我们先放一段Hello World：hello.c#include <stdio.h>
```

int main()  
{  
printf(“Hello World”);  
return 0;  
}  
然后就是一段老生常谈的描述了：  
要想让这段代码在Linux上运行，我们需要使用GCC  
预编译：将hello.c和stdio.h预编译为hello.i  
编译：将hello.i编译为hello.s  
汇编：将hello.s翻译为机器指令hello.o（.o目标文件）  
链接：链接各种需要的库和其他目标文件（该hello程序不需要）得到可执行文件hello.out（相当于windows的.exe）

整个过程将高级语言翻译成了机器语言，而编译器，就是这样的一个翻译工具。GCC可以完成从预编译编译，汇编，链接整个过程。但是平时使用Visual Studio等软件时并没有接触到这个过程，因为VS是高度集成开发环境（IDE、Integrated Development Environment），集成了代码编辑器，编译器，调试器和图像化用户界面，上述所有程序编译和链接过程都用一步build构建带过了。