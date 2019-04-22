# Autoconf 生成链接文件和创建层次目录

在 Autoconf 中自动安装过程中

- 为了生成链接文件可以通过在项目的 configure.ac 添加 `AC_PROG_LN_S` 关键字使其支持创建软连接命令。
- 为了创建更深层次的目录在shell 中使用的是 `mkdir -p`, 但在 Autoconf 中提供了关键字 `AC_PROG_MKDIR_P`

以下是在 makefile.am 中使用的例子。

```makefile
install-exec-hook:
	$(MKDIR_P) $(DESTDIR)/etc/init.d
	$(LN_S) $(DESTDIR)/bin/watchdog $(DESTDIR)/etc/init.d
```
## 引用：

[Installation FAQs](http://www.astro.gla.ac.uk/~norman/star/ssn78/ssn78.htx/N-a5b2.html)
[What Gets Installed](https://www.gnu.org/software/automake/manual/html_node/Install.html)
[4.11 Creating Configuration Links](https://www.gnu.org/software/autoconf/manual/autoconf-2.68/html_node/Configuration-Links.html)
[Creating a symlink with autotools](https://adam.younglogic.com/2007/09/creating-a-symlink-with-autotools/)
