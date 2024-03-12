最开始叫 `6to5` (es6 转 es5)，随着 es 标准的演进，改名为 babel。

## babel 的用途

**1. 转译 esnext、typescript、flow 等到目标环境支持的 js**

babel7 提供了 `@babel/preset-env` 的包，可以指定目标 env 来按需转换，转换更加的精准，产物更小。

**2. 代码转换实现特定功能**

比如实现函数插桩进行埋点代码、自动国际化等。

通过 babel 可以实现代码到 AST 的解析、转换、以及目标代码的生成。

**3. 代码的静态分析**

对代码进行 parse 之后，会生成 AST，通过 AST 能够理解代码结构，可以进行一些静态检查。

静态分析工具：

- linter 工具
- api 文档自动生成工具
- type checker 
- 压缩混淆工具
- js 解释器