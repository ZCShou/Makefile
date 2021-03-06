# 命令处理机制
&emsp;&emsp;在前面的文章中，我们有单独章节来介绍过 Makefile 中规则的命令如何书写。但其中没有详细来说 `make` 如何来执行我们书写的命令，这里再进一步解释一下。

## 命令执行机制
&emsp;&emsp;如果目标中给出了多行命令，那么每一行命令将在一个独立的子 shell 进程中被执行。就是说，每一行命令的执行是在一个独立的 shell 进城中完成。因此多行命令之间的执行是相互独立的多个进程，相互之间不存在依赖。当 `make` 在执行命令时，如果某一条命令执行失败（被一个信号中止，或非零退出），且该条命令产生的错误未被忽略，那么其它的用于重建同一目标的命令执行也将会被终止，`make` 进程以错误告终。

> 这里就和 `make` 的  `-jxx` 参数有关系。该参数指出同时运行命令的个数。我们需要注意的是，如果没有这个参数，`make` 运行命令时能运行多少就运行多少，而不是固定一个个执行。

## 嵌套 make
&emsp;&emsp;这其实是命令的一个特殊情况：命令本身就是 `make -f xxx`，也就是在 Makefile 中调用 make 执行其他 Makefile。此时，`make` 并不是对每个子 `make -C` 的返回值做检测，而是对整个子 sh 的返回值做检测。确切的说应该是 `make` 调用了子进程 sh，然后 sh 又调用了子进程 `make` 运行 `make -C`，即 make –> sh –> make 的关系，所以 `make` 只能看到 sh 的返回值，而 sh 中最后一条语句的返回值会作为 sh 的返回值。
