# week03学习总结
##### 有效数字

判断数字符号

```
function sign(number) {
	if(1/number === Infinity) {
    return 1;
  }
  if(1/number === -Infinity) {
    return -1;
  }
  return number / Math.abs(number);
}
```

浮点数尽量不要做算数运算，考虑精度丢失的影响。

#### Expression

##### Left Handside & Right Handside

 Left Handside (赋值操作的目标) Reference 引用

 Right Handside (赋值操作的来源)

##### Left Handside

运算符

表达式树结构 => 表达式优先级

- Member

  ```
  a.b
  a[b]
  foo`string` // styles-compontents
  super.b
  super[b]
  new.target // 判断函数是否是new调用
  new Foo()
  ```

- New

  new Foo

- Call

  ```
  foo()
  super()
  foo()[b]
  foo().b
  foo()`string`
  ```

##### Right Handside

- Update

  ```
  a++
  a--
  --a
  ++a
  ```

- Unary

  ```
  delete a.b
  void 0; // 生成undefined
  typeof a
  +a
  -a
  ~a
  !a // !!a 转换为boolean值
  await a
  ```

- Exponental

  **

- Multiplicative

  \* / %

- Additive

  - - 

- Shift

  << >> >>>

- Relationship

  < > <= >= instanceof in

- Equality

  ```
  ==
  !=
  ===
  !==
  ```

- Bitwise 位运算

  & ^ |

- Logical

  && ||

  短路逻辑

  ```
  a && b  a为true时，b才会执行
  a || b  a或b为true，a或b才会执行
  ```

- Conditional

  ? :

##### 类型转换

- 基础类型

  - Undefined
  - Boolean
  - String
  - Number
  - Null
  - Symbol
  - BigInt
  - Object

- 装箱拆箱

  * 装箱：基础类型 => 包装类型 `Boolean String Boolean ...`

  * 拆箱：包装类型(Object) => 基础类型, 会优先调用`valueOf toString toPrimitive`进行转换

- 类型的判断

  - typeof
  - Obejct.prototype.toString.call
  - instanceof

- 隐式转换发生的场景

  - Left Handside Right Handside

    > 左右取值，转换为原始值，如果转换后的值存在string, 则进行toString后拼接。否则按toNumber处理

  - ==

    >  优先按照number处理

  - if

    > 优先按照boolean处理

  - 数学运算符

    > 优先转换非number为number

## Atom

### Grammar 语句

* 简单语句 -- 语句最基本的组成单位

  * ExpressionStatement

    ```
    a = 1 + 2;
    ```

  * EmptyStatement

    ```
    ;
    ```

  * DebuggerStatement

    ```
    debugger;
    ```

  * ThrowStatement

    ```
    throw a;
    ```

  * ContinueStatement

    ```
    continue label1;
    ```

  * BreakStatement

    ```
    break label2;
    ```

  * ReturnStatement

    ```
    return 1 + 2;
    ```

* 组合语句

  * BlockStatement -- 逐条执行StatementList

    * [[ type ]]: normal -- 遇到非正常语句不执行
    * [[ value ]]: --
    * [[ target ]]: --

    ```
    {
    	a:1;
    }
    ```

  * IfStatement

  * SwitchStatement

  * IterationStatement

    * while
    * do while
    * for -- block 内部相当于自作用域
    * for in -- 循环属性
    * for of -- 循环属性的值，要符合Iterator格式

  * WithStatement

  * LabelledStatement

  * TryStatement

    * [[ type ]]: return
    * [[ value ]]: --
    * [[ target ]]: label

    ```
    try {
    
    } catch () {
    
    } finally {
    
    }
    ```

* 声明

  * FunctionDeclaration

    ```
    function foo() {} //函数声明 
    var o = function foo() {} // 函数表达式
    ```

  * GeneratorDeclaration

    ```
    function* foo() {
    	yield 1;
    }
    let g = foo();
    g.next().value;
    ```

  * AsyncFunctionDeclaration

    ```
    async function foo() {
      await xxx;
    }
    ```

  * AsyncGeneratorDeclaration

    ```
    async function* gen() {
      await xxx;
    }
    ```

  * VariableStatement

    ```
    var let const
    ```

  * ClassDeclaration

    ```
    class foo {}
    ```

  * LexicalDeclaration

### Runtime

* Completion Record -- 完成记录
  * [[ type ]]: normal, break, continue, return, or throw
  * [[ value ]]: Types -- 7种类型
  * [[ target ]]: label
* Lexical Environment

##### 预处理/变量提升

```
var a = 2;
void function() {
  a = 1;
  return;
  var a; // const a
}()
```

var变量声明和函数声明会预处理。

var值预处理声明部分

函数预处理整体

##### 作用域

函数的执行上下文

在多层作用域中进行LHS和RHS操作，直到找到为止，形成作用域链

#### Object

**状态 行为 唯一性**

架构合理性： 封装(内聚) 复用 解耦

面向对象子系统： 继承

多态？

##### 基于类的面向对象 Object-Class

- 基类
- interface
- mixin

##### Prototype

##### 抽象对象时，应该遵循‘行为改变状态’的原则，行为改变自身状态。不应该按照语言描述的行为进行设计。

##### Object in JavaScript

- Property

  - Key
    - Symbol
    - String
  - Value
    - Data Property
      - [[value]]
      - writable
      - emumerable
      - configurable
    - Accessor Property
      - get
      - set
      - emumerable
      - configurable

- [[Prototype]]

  原型链

##### Object API

- 基础API

  `{} . [] Object.defineProperty`

- 原型API

  `Object.create Object.setPrototypeOf Object.getPrototypeOf`

- 基于类的面向对象API(模拟)

  `new class extends`

- 基于原型的面向对象API

  `new function prototype`