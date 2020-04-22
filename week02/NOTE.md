# week02学习总结
# 编程语言通识

## 按语法分类

* 非形式语言
  * 中文，英文

* 形式语言（乔姆斯基谱系）
  * 0型 无限制文法
    * ? ::= ?
  * 1型 上下文相关文法
    * ?<A>? ::= ?<B>?
  * 2型 上下文无关文法
    * <A> ::= ?
  * 3型 正则文法
    * <A> ::= <A>?
    * <A> ::= ?<A> x

### BNF（巴斯科-诺尔范式）

* <符号> ::= <使用符号的表达式> 
  * "" 引号内为终结符
  * <> 尖括号内为非终结符

```
"a"

"b"

<Program> ::= "a"+ | "b"+

递归
<Program> ::= <Progarm> "a"+ | <Program> "b"+

整数连加
	定义Number
<Number> ::= "0" | "1" | "2" | ..... | "9"
	定义十进制数
	tip1: 直接是 0
	tip2: 以1-9开头，后面任意数字
<DecimalNumber> ::= "0" | (("1" | "2" | ..... | "9") <Number>*)
	定义加法
<AdditiveExpression> ::= <DecimalNumber> | <AdditiveExpression> "+" <DecimalNumber>
	定义乘法
<MultiplicativeExpression> ::= <DecimalNumber> |
	<MultiplicativeExpression> "*" <DecimalNumber> |
		添加支持除法
		<MultiplicativeExpression> "/" <DecimalNumber>
	用乘法定义加法
<AdditiveExpression> ::= <MultiplicativeExpression> |
	<AdditiveExpression> "+" <MultiplicativeExpression> |
		添加支持减法
		<AdditiveExpression> "-" <MultiplicativeExpression>

<LogicalExpression> ::= <AdditiveExpression> |
	<LogicalExpression> "||" <AdditiveExpression> |
  <LogicalExpression> "&&" <AdditiveExpression>
  
<PrimaryExpression> ::= <DecimalNumber> |
	"(" <LogicalExpression> ")"
	带括号的乘除法表达式
	<MultiplicativeExpression> ::= <PrimargExpression> |
		<MultiplicativeExpression> "*" <PrimargExpression> |
		<MultiplicativeExpression> "/" <PrimargExpression>
		
用正则实现DecimalNumber
<DecimalNumber> ::= /0|[1-9][0-9]*/
```

### 形式语言的用途

* 数据描述语言
* 编程语言

### 形式语言-表达方式

* 声明式语言
* 命令型语言

## 图灵完备性

* 命令式 -- 图灵机
  * goto
  * if 和 while

* 声明式 -- lambda
  * 递归
  * 分治

## 类型系统

* 动态与静态
* 强类型与弱类型（有隐式转换的都是弱类型）
* 复合类型
  * 结构体
  * 函数签名
* 子类型
  * 逆变/协变

### Unicode

#### Blocks

```
<script>
for (let i = 0; i < 128; i++) {
	console.log(String.fromCharCode(i));
	document.write(i + "<span style = background-color:lightgreen>" + String.fromCharCode(i) + "</span><br>");
}
</script>
```

* InputElement
  * WhiteSpace 空格
    * <Tab> 制表符
    * <VT> 垂直制表符
    * <FF>
    * <NBSP> no-break space
  * LineTerminator 换行
    * <LF> Line Feed 换行
    * <CR> Carrige Return 回车
    * <LS> Line Separator 不常用
    * <PS> Paragraph Separator 不常用
  * Comment 注释 
    * //
    * /* */
  * Token 
    * IdentifierName
      * Keywords 关键字
      * Identifier
      * Future reserved Keywords: enum
    * Punctuator 符号
    * Literal 直接量
      * Number
        * 存储 Uint8Array、Float64Array
      * String
        * Character
        * Code Point
        * Encoding
          * unicode编码 - utf
            * utf-8 可变长度 （控制位的用处）
        * Grammar
          * `''`、`""`、``` `
      * Boolean
      * Null
      * Undefined
      * Symbol
      * Object