## 编译器和转译器

编译的定义：将一种编程语言转成另一种编程语言，主要指的是高级语言到低级语言。

编译器（Compiler）是指高级语言到低级语言的转换工具。

转换编译器（简称转译器：Transpiler）是指高级语言到高级语言的转换工具。

babel 就是一个 Javascript Transpiler。

为什么官网[https://babeljs.io/](https://babeljs.io/)里说的 Babel is a JavaScript compiler.

原因：**transpiler 是一种特殊的 compiler。**

## babel 的编译流程

整体流程分三步：

**1. 解析（parse）：将代码字符串解析成抽象语法树（AST）**

这个过程分为两个阶段：

- 词法分析（Lexical Analysis）：将字符串分解成有意义的代码块，这些代码块被称为“token”
- 语法分析（Syntactic Analysis）：将词法分析得到的 token 递归组装转换成 AST 的形式

**2. 转换（transform）：对 AST 进行遍历，调用各种 transform 插件对 AST 进行增删改**

这个过程会进行 AST 的遍历，遍历的过程中处理到不同的 AST 节点会调用注册的相应的 visitor 函数，visitor 函数可以对 AST 进行增删改，返回新的 AST。

**3. 生成（generate）：根据修改后的 AST 生成目标代码，并生成 sourcemap**

这个过程中不同的 AST 对应的不同结构的字符串。比如 `IfStatement` 就可以打印成 `if(test) {}` 格式的代码。这样从 AST 根节点进行递归的字符串拼接，就可以生成目标代码的字符串。

## 拓展

**为什么分三步？**

为了让计算机理解代码需要先对源码字符串进行 parse，生成 AST，把对代码的修改转为对 AST 的增删改，转换完 AST 之后再打印成目标代码字符串。

**抽象语法树（abstract syntax tree）**：通过不同的对象来保存不同的数据，并且按照依赖关系组织起来的一种数据结构。它的结构中省略了一些无具体意义的分隔符，比如 `{`、`}`、`;` 等，到转回字符串的过程中会把之前删掉的一些分隔符再加回来。

**sourcemap** 就是一个映射表，它包含源代码和构建后代码之间的映射关系。

有了它，我们可以实现两个功能：

1. 调试源代码
2. 错误提示


