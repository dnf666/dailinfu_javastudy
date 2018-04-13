# Reader 与 Writer

Reader 和 Writer 的设计是为了兼容国际化，因为 InputStream 与 OutputStream 的老的继承结构仅支持 8 位字节流，并不能很好的处理 16 的汉字

*！* Unicode 字符：是计算机科学领域里的一项业界标准。它对世界上大部分的文字系统进行了整理、编码，使得电脑可以用更为简单的方式来呈现和处理文字。在 Unicode 当中每一个字符占 2 个字节

Reader 与 Writer 的继承层次结构就是为了在所有的 I/O 操作当中都支持 Unicode 字符，另外由于是新设计的类库，所以比旧类库效率高运行快
