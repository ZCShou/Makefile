# 规则匹配机制
&emsp;&emsp;在前的文章中，我们说过 Makefile 中有很多规则，规则也会有各种依赖规则。`make` 程序对于规则（以及规则的依赖）的匹配并不是完全匹配，而是使用近似匹配方式。如果给出了目标，则 `make` 优先去找匹配的规则（ ***匹配规则：完整匹配 > 通配符半匹配 > 完全通配符匹配*** ）去执行；如果没有给出参数，`make` 会自动找到 Makefile 中第一个目标中没有通配符的规则执行。

&emsp;&emsp;如果 Makefile 中存在多条同名规则，则 `make` 程序会尝试将他们合并。但是如果这些同名规则都有命令的话，`make` 会给出警告，并用后面的命令代替前面的命令。如下图所示：

![exp1](./images/match.png)

该图中的示例代码见 `examples/exp100/*`。


&emsp;&emsp;在默认情况下，`make` 总是会优先把 Makefile 本身作为目标，并尝试使用各种隐式规则去重建 Makefile。如下图所示的是 `examples/exp100/*` 下使用命令 `make --debug=all` 的执行记录（省略部分内容）：

![remakefile](./images/remakefile.jpg)

如上图中，make 读取了 Makefile 文件之后，随即开始将 Makefile 作为目标，尝试重建 Makefile。关于这部分内容可以在官方手册的 [How Makefiles Are Remade](https://www.gnu.org/software/make/manual/make.html#Remaking-Makefiles) 章节找到详细的说明。如果你不想让 `make` 自动构件 Makefile 本身，则可以在自己的 Makefile 中增加一条规则：`Makefile: ;` 命令依赖都是空的。添加后执行的结果如下：

![no_remakefile](./images/no_remakefile.jpg)
