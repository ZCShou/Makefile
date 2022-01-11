# 跟我一起写 Makefile
&emsp;&emsp;最近,本人在使用 U-Boot 时，需要查看及更改 U-Boot 的 Makefile，由于对于 Makefile 不是很了解，于是在网上找到了《跟我一起写Makefile》。《跟我一起写Makefile》是[陈皓](https://coolshell.cn/haoel)发表在其 [CSDN 博客](https://blog.csdn.net/haoel/article/details/2886)上的系列文章。为了避免眼高手低，现通过将其整理到 Github 的方式来学习一下。

&emsp;&emsp;作者的原文中没有代码高亮，排版也不是很规则，文中的示例也没有提供代码，为了加深学习印象，我会提供完整的示例代码，并在原文中会添加了一些内容、图示等等，因此，本文与作者的原文稍有差异，但主体内容没有变化！我这里主要的更改有：
1. 增加示例代码，用于验证文中的示例
2. 在文中增加一些图片辅助理解
3. 全文均为 Markdown 格式，方便大家查看及修改
4. 调整了文章的排版

&emsp;&emsp;在整理额时候，发现已经有网友做个这个工作了：https://github.com/seisman/how-to-write-makefile ，但是他这个使用的是 reStructuredText（扩展名 .rst）格式的文件，不是目前流行的 Markdown 格式。而且它俩的语法差的也比较多，我这里再整理一个 Markdown 格式的！

<!-- 该系列文章应该是翻译整理自 。 -->

# 相关内容
1. 项目主页： https://github.com/ZCShou/Makefile

2. 网页在线版： https://zcshou.github.io/Makefile/

3. [GNU Make Manual](https://www.gnu.org/software/make/manual/)，英文比较好的也可以直接去看这个官方手册

# 关于本文档
1. 本文档系统使用开源文档网站生成器 **[docsify](https://docsify.js.org/#/)** 搭建，文档格式均为 Markdown 格式。
2. 文档中的图例使用开源软件 **[draw.io](https://www.diagrams.net/)** 绘制，并导出为 .PNG。所有图示的源码可以在这里下载（可使用 draw.io 打开即可）。
