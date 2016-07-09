C Tips
<!-- toc -->


### 程序执行时间测试
[Calculates the wall-clock time used by the calling process.](https://msdn.microsoft.com/en-us/library/4e2ess30.aspx)
The clock function tells how much wall-clock time the calling process has used. Note that this is not strictly conformant with ISO C99, which specifies net CPU time as the return value. To obtain CPU time, use the Win32 GetProcessTimes function.
A timer tick is approximately equal to 1/CLOCKS_PER_SEC seconds. Given enough time, the value returned by clock can exceed the maximum positive value of clock_t and become negative, or exceed the maximum absolute value and roll over. Do not rely on this value for total elapsed time in processes that run for more than 214,748 seconds, or about 59 hours.
```c
// crt_clock.c
// This example prompts for how long
// the program is to run and then continuously
// displays the elapsed time for that period.
//

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

void sleep( clock_t wait );

int main( void )
{
   long    i = 6000000L;
   clock_t start, finish;
   double  duration;

   // Delay for a specified time.
   printf( "Delay for three seconds\n" );
   sleep( (clock_t)3 * CLOCKS_PER_SEC );
   printf( "Done!\n" );

   // Measure the duration of an event.
   printf( "Time to do %ld empty loops is ", i );
   start = clock();
   while( i-- ) 
      ;
   finish = clock();
   duration = (double)(finish - start) / CLOCKS_PER_SEC;
   printf( "%2.1f seconds\n", duration );
}

// Pauses for a specified number of milliseconds.
void sleep( clock_t wait )
{
   clock_t goal;
   goal = wait + clock();
   while( goal > clock() )
      ;
}
```

### 自动转换代码
[Is it possible to convert C++ to C?](http://www.parashift.com/c++-faq/convert-to-c.html) 答案是：

- NO. 不能把C++代码自动转换成可读性和可维护性的C代码
- YES. 能自动转换,但有很多限制
[Can I use LLVM to convert C++ code to C code?](http://llvm.org/releases/3.1/docs/FAQ.html#translatecxx)

Yes, you can use LLVM to convert code from any language LLVM supports to C. Note that the generated C code will be very low level (all loops are lowered to gotos, etc) and not very pretty (comments are stripped, original source formatting is totally lost, variables are renamed, expressions are regrouped), so this may not be what you're looking for. Also, there are several limitations noted below.

在google 怎么用llvm 转换C++源代码到C源代码时,发现了这个 http://llvm.org/releases/3.1/docs/ReleaseNotes.html#changes LLVM 从3.1版本就不再支持从其它语言转换成C源代码的功能 但转换成汇编的功能继续可用
```bash
$ clang –c –emit-llvm –o test.bc test.c
$ opt –O1 –o test.bc test.bc
$ llc –o test.s test.bc
$ gcc –o test test.s
```
[http://en.wikipedia.org/wiki/Source-to-source_compiler](http://en.wikipedia.org/wiki/Source-to-source_compiler)


