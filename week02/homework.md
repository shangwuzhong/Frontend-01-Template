### 随堂练习

编写带括号的四则运算产生式

```javascript
<Number> ::= "0" | "1" | "2" | ..... | "9";
<DecimalNumber> ::= "0" | (("1" | "2" | ..... | "9") <Number>*)
<AdditiveExpression> ::= <DecimalNumber> | <AdditiveExpression> "+" <DecimalNumber>
<LogicalExpression> ::= <AdditiveExpression> |
	<LogicalExpression> "||" <AdditiveExpression> |
  <LogicalExpression> "&&" <AdditiveExpression>
<PrimaryExpression> ::= <DecimalNumber> |
	"(" <LogicalExpression> ")"
	带括号的乘除法表达式
	<MultiplicativeExpression> ::= <PrimargExpression> |
		<MultiplicativeExpression> "*" <PrimargExpression> |
		<MultiplicativeExpression> "/" <PrimargExpression>
```

### 课后作业

1. 写一个正则表达式 匹配所有的Number直接量

   ```javascript
   /^-?[0-9]\d*$|(0x)?[0-9a-fA-F]+|0?[0-7]*|^-?([1-9]\d*\.\d*|0\.\d*[1-9]\d*|0?\.0+|0)$/
   ```

2. 写一个 UTF-8 Encoding 的函数

   ```javascript
   function UTF8Encoding(string) {
     return string
       .split('')
       .map((str) => `\\u${str.charCodeAt().toString(16)}`)
       .join('')
   }
   ```

3. 写一个正则表达式，匹配所有的字符串直接量，单引号和双引号

   ```javascript
   /?:[^"]|\.)*"|'(?:[^']|\.)*|^[\u4E00-\u9FA5A-Za-z0-9]+$/
   ```

   