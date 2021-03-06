[#]: collector: (lujun9972)
[#]: translator: (An-DJ)
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (How To Check CPU, Memory And Swap Utilization Percentage In Linux?)
[#]: via: (https://www.2daygeek.com/linux-check-cpu-memory-swap-utilization-percentage/)
[#]: author: (Vinoth Kumar https://www.2daygeek.com/author/vinoth/)

如何查看Linux下CPU，内存和Swap（交换分区）的占用率？
======

在Linux下有很多可用的命令和选项来查看内存占用情况，但是我并没有看见关于内存利用率的更多的信息。

在大多数情况下我们只单独查看内存使用情况，并没有考虑占用的百分比究竟是多少。

如果你想要了解这些信息，那你看这篇文章就对了。

我们将会详细地在这里帮助你解决这个问题。

这篇教程将会帮助你在面对Linux服务器下频繁内存高占用情况时，确定内存使用情况。

但是在同时，如果你使用的是`free -m`或者`free -g`，占用情况描述地并不是十分清楚。

这些格式化命令属于Linux高级命令。它将会对Linux专家和中等水平Linux使用者非常有用。

### 方法-1：如何查看Linux下内存占用率？

我们可以使用下面命令的组合来达到此目的。在该方法中，我们使用的是`free`和`awk`命令的组合来获取内存占用率。

如果你正在寻找其他有关于内存的文章，你可以导航到如下链接。这些文章有 **[free命令][1]** , **[smem命令][2]** , **[ps_mem命令][3]** , **[vmstat命令][4]** 及 **[多种方式来查看物理内存大小][5]**.

对于获取不包含百分比符号的`内存`占用率：

```
$ free -t | awk 'NR == 2 {print "Current Memory Utilization is : " $3/$2*100}'
或
$ free -t | awk 'FNR == 2 {print "Current Memory Utilization is : " $3/$2*100}'

Current Memory Utilization is : 20.4194
```

对于获取不包含百分比符号的`Swap（交换分区）`占用率：

```
$ free -t | awk 'NR == 3 {print "Current Swap Utilization is : " $3/$2*100}'
或
$ free -t | awk 'FNR == 3 {print "Current Swap Utilization is : " $3/$2*100}'

Current Swap Utilization is : 0
```

对于获取包含百分比符号及保留两位小数的`内存`占用率：

```
$ free -t | awk 'NR == 2 {printf("Current Memory Utilization is : %.2f%"), $3/$2*100}'
或
$ free -t | awk 'FNR == 2 {printf("Current Memory Utilization is : %.2f%"), $3/$2*100}'

Current Memory Utilization is : 20.42%
```

对于获取包含百分比符号及保留两位小数的`Swap（交换分区）`占用率：

```
$ free -t | awk 'NR == 3 {printf("Current Swap Utilization is : %.2f%"), $3/$2*100}'
或
$ free -t | awk 'FNR == 3 {printf("Current Swap Utilization is : %.2f%"), $3/$2*100}'

Current Swap Utilization is : 0.00%
```

如果你正在寻找有关于内存的其他文章，你可以导航至如下链接。这些链接有 **[使用LVM（逻辑盘卷管理，Logical Volume Manager）创建和扩展Swap交换分区][6]** , **[多种方式创建或扩展Swap交换分区][7]** 和 **[多种方式创建/删除和挂载交换分区文件][8]**。

键入free命令会更好地作出阐释：

```
$ free
 total used free shared buff/cache available
Mem: 15867 3730 9868 1189 2269 10640
Swap: 17454 0 17454
Total: 33322 3730 27322
```

如下是一些细节：

  * **`free:`** free是一个标准命令，用于在Linux下查看内存使用情况。
  * **`awk:`** awk是一个专门用来做文本数据处理的强大命令。
  * **`FNR == 2:`** 该命令给出了对于每一个输入文件的行数。其基本上用于挑选出给定的行(针对于这里，它选择的是行数为2的行)
  * **`NR == 2:`** 该命令给出了处理的行总数。其基本上用于过滤给出的行（针对于这里，它选择的是行数为2的行）
  * **`$3/$2*100:`** 该命令将列3除以列2并将结果乘以100。
  * **`printf:`** 该命令用于格式化和打印数据。
  * **`%.2f%:`** 默认情况下，其打印小数点后保留6位的浮点数。使用后跟的格式来约束小数位。



### 方法-2：如何查看Linux下内存占用率？

我们可以使用下面命令的组合来达到此目的。在这种方法中，我们使用`free`,`grep`和`awk`命令的组合来获取内存占用率。

对于获取不包含百分比符号的`内存`占用率：

```
$ free -t | grep Mem | awk '{print "Current Memory Utilization is : " $3/$2*100}'
Current Memory Utilization is : 20.4228
```

对于获取不包含百分比符号的`Swap（交换分区）`占用率：

```
$ free -t | grep Swap | awk '{print "Current Swap Utilization is : " $3/$2*100}'
Current Swap Utilization is : 0
```

对于获取包含百分比符号及保留两位小数的`内存`占用率：

```
$ free -t | grep Mem | awk '{printf("Current Memory Utilization is : %.2f%"), $3/$2*100}'
Current Memory Utilization is : 20.43%
```

对于获取包含百分比符号及保留两位小数的`Swap（交换空间）`占用率：
```
$ free -t | grep Swap | awk '{printf("Current Swap Utilization is : %.2f%"), $3/$2*100}'
Current Swap Utilization is : 0.00%
```

### 方法-1：如何查看Linux下CPU的占用率？

我们可以使用如下命令的组合来达到此目的。在这种方法中，我们使用`top`,`print`和`awk`命令的组合来获取CPU的占用率。

如果你正在寻找其他有关于CPU（译者勘误，原文为memory)的文章，你可以导航至如下链接。这些文章有 **[top命令][9]** , **[htop命令][10]** , **[atop命令][11]** 及 **[Glances命令][12]**.

如果在输出中展示的是多个CPU的情况，那么你需要使用下面的方法。

```
$ top -b -n1 | grep ^%Cpu
%Cpu0 : 5.3 us, 0.0 sy, 0.0 ni, 94.7 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st
%Cpu1 : 0.0 us, 0.0 sy, 0.0 ni,100.0 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st
%Cpu2 : 0.0 us, 0.0 sy, 0.0 ni, 94.7 id, 0.0 wa, 0.0 hi, 5.3 si, 0.0 st
%Cpu3 : 5.3 us, 0.0 sy, 0.0 ni, 94.7 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st
%Cpu4 : 10.5 us, 15.8 sy, 0.0 ni, 73.7 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st
%Cpu5 : 0.0 us, 5.0 sy, 0.0 ni, 95.0 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st
%Cpu6 : 5.3 us, 0.0 sy, 0.0 ni, 94.7 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st
%Cpu7 : 5.3 us, 0.0 sy, 0.0 ni, 94.7 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st
```

对于获取不包含百分比符号的`CPU`占用率：

```
$ top -b -n1 | grep ^%Cpu | awk '{cpu+=$9}END{print "Current CPU Utilization is : " 100-cpu/NR}'
Current CPU Utilization is : 21.05
```

对于获取包含百分比符号及保留2位小数的`CPU`占用率：

```
$ top -b -n1 | grep ^%Cpu | awk '{cpu+=$9}END{printf("Current CPU Utilization is : %.2f%"), 100-cpu/NR}'
Current CPU Utilization is : 14.81%
```

### 方法-2：如何查看Linux下CPU的占用率？

我们可以使用如下命令的组合来达到此目的。在这种方法中，我们使用的是`top`,`print/printf`和`awk`命令的组合来获取CPU的占用率。

如果在单个输出中一起展示了所有的CPU的情况，那么你需要使用下面的方法。

```
$ top -b -n1 | grep ^%Cpu
%Cpu(s): 15.3 us, 7.2 sy, 0.8 ni, 69.0 id, 6.7 wa, 0.0 hi, 1.0 si, 0.0 st
```

对于获取不包含百分比符号的`CPU`占用率：

```
$ top -b -n1 | grep ^%Cpu | awk '{print "Current CPU Utilization is : " 100-$8}'
Current CPU Utilization is : 5.6
```

对于获取包含百分比符号及保留2位小数的`CPU`占用率：

```
$ top -b -n1 | grep ^%Cpu | awk '{printf("Current CPU Utilization is : %.2f%"), 100-$8}'
Current CPU Utilization is : 5.40%
```

如下是一些细节：

  * **`top:`** top命令是一种用于查看当前Linux系统下正在运行的进程的非常好的命令。
  * **`-b:`** -b选项，允许top命令切换至批处理的模式。当你从本地系统运行top命令至远程系统时，它将会非常有用。
  * **`-n1:`** 迭代次数
  * **`^%Cpu:`** 过滤以%CPU开头的行。
  * **`awk:`** awk是一种专门用来做文本数据处理的强大命令。
  * **`cpu+=$9:`** 对于每一行，将第9列添加至变量‘cpu'。
  * **`printf:`** 该命令用于格式化和打印数据。
  * **`%.2f%:`** 默认情况下，它打印小数点后保留6位的浮点数。使用后跟的格式来限制小数位数。
  * **`100-cpu/NR:`** 最终打印出’CPU平均占用‘，即用100减去其并除以行数。



--------------------------------------------------------------------------------

via: https://www.2daygeek.com/linux-check-cpu-memory-swap-utilization-percentage/

作者：[Vinoth Kumar][a]
选题：[lujun9972][b]
译者：[An-DJ](https://github.com/An-DJ)
校对：[校对者ID](https://github.com/校对者ID)

本文由 [LCTT](https://github.com/LCTT/TranslateProject) 原创编译，[Linux中国](https://linux.cn/) 荣誉推出

[a]: https://www.2daygeek.com/author/vinoth/
[b]: https://github.com/lujun9972
[1]: https://www.2daygeek.com/free-command-to-check-memory-usage-statistics-in-linux/
[2]: https://www.2daygeek.com/smem-linux-memory-usage-statistics-reporting-tool/
[3]: https://www.2daygeek.com/ps_mem-report-core-memory-usage-accurately-in-linux/
[4]: https://www.2daygeek.com/linux-vmstat-command-examples-tool-report-virtual-memory-statistics/
[5]: https://www.2daygeek.com/easy-ways-to-check-size-of-physical-memory-ram-in-linux/
[6]: https://www.2daygeek.com/how-to-create-extend-swap-partition-in-linux-using-lvm/
[7]: https://www.2daygeek.com/add-extend-increase-swap-space-memory-file-partition-linux/
[8]: https://www.2daygeek.com/shell-script-create-add-extend-swap-space-linux/
[9]: https://www.2daygeek.com/linux-top-command-linux-system-performance-monitoring-tool/
[10]: https://www.2daygeek.com/linux-htop-command-linux-system-performance-resource-monitoring-tool/
[11]: https://www.2daygeek.com/atop-system-process-performance-monitoring-tool/
[12]: https://www.2daygeek.com/install-glances-advanced-real-time-linux-system-performance-monitoring-tool-on-centos-fedora-ubuntu-debian-opensuse-arch-linux/
