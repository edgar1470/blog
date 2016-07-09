在HW工作时经常用来衡量工作量（数量和质量）的一个重要指标就是：你这个功能需要写多少行代码？
那个时段项目组的代码库基线指标是一个人50行／天, 刚开始听到这个数字的感觉：
  * 好保守的数字
  * 这样是要磨洋工的好借口

但做了一段时间后，才发现在多人协作的大型开发项目中提出这个基线指标是有丈量依据和事实数据支撑的。

下面这个工具[cloc](https://github.com/AlDanial/cloc) 可以用于实际编码中的代码量统计：

<!-- toc -->

### cloc Overview
cloc counts blank lines, comment lines, and physical lines of source code in many programming languages. Given two versions of a code base, cloc can compute differences in blank, comment, and source lines. It is written entirely in Perl with no dependencies outside the standard distribution of Perl v5.6 and higher (code from some external modules is embedded within cloc) and so is quite portable. cloc is known to run on many flavors of Linux, FreeBSD, NetBSD, OpenBSD, Mac OS X, AIX, HP-UX, Solaris, IRIX, z/OS, and Windows. (To run the Perl source version of cloc on Windows one needs ActiveState Perl 5.6.1 or higher, Strawberry Perl, Cygwin, or MobaXTerm with the Perl plug-in installed. Alternatively one can use the Windows binary of cloc generated with perl2exe to run on Windows computers that have neither Perl nor Cygwin.)

cloc contains code from David Wheeler's SLOCCount, Damian Conway and Abigail's Perl module Regexp::Common, Sean M. Burke's Perl module Win32::Autoglob, and Tye McQueen's Perl module Algorithm::Diff. Language scale factors were derived from Mayes Consulting, LLC web site http://softwareestimator.com/IndustryData2.htm.

### Why Use cloc
cloc has many features that make it easy to use, thorough, extensible, and portable:

 * Exists as a single, self-contained file that requires minimal installation effort---just download the file and run it.
 * Can read language comment definitions from a file and thus potentially work with computer languages that do not yet exist.
 * Allows results from multiple runs to be summed together by language and by project.
 * Can produce results in a variety of formats: plain text, SQL, XML, YAML, comma separated values.
 * Can count code within compressed archives (tar balls, Zip files, Java .ear files).
 * Has numerous troubleshooting options.
 * Handles file and directory names with spaces and other unusual characters.
 * Has no dependencies outside the standard Perl distribution.
 * Runs on Linux, FreeBSD, NetBSD, OpenBSD, Mac OS X, AIX, HP-UX, Solaris, IRIX, and z/OS systems that have Perl 5.6 or higher. The source version runs on Windows with either ActiveState Perl, Strawberry Perl, Cygwin, or MobaXTerm+Perl plugin. Alternatively on Windows one can run the Windows binary which has no dependencies.


###  cloc usage
```bash
$ ./cloc-1.55.pl /cygdrive/d/source/65X/NT9665x_CarDV_20141013
lsUse of qw(...) as parentheses is deprecated at ./cloc-1.55.pl line 1841.         
          1814 text files.
          1696 unique files.
          45 files ignored.
 
          http://cloc.sourceforge.net v 1.55  T=16.0 s (103.2 files/s, 29969.2 lines/s)
          -------------------------------------------------------------------------------
          Language                     files          blank        comment           code
          -------------------------------------------------------------------------------
          C                              466          28407          51002         206452
          C/C++ Header                   721          20749          42535          55748
          D                              369          23225              0          46732
          make                            83            807           1576           1949
          DOS Batch                       11             45              0            230
          Assembly                         1              6             26             18
          -------------------------------------------------------------------------------
          SUM:                          1651          73239          95139         311129
          -------------------------------------------------------------------------------
```

