### 浏览器工作原理

#### 排版

- 本堂课以flex布局为例，分析了浏览器如何进行排版
- Main Axis 主轴
- Cross Axis 交叉轴
- flex-direction: row column
- mainSize mainStart mainEnd mainSign mainBase
- crossSize crossStart crossEnd crossSign CrossBase
- 整体分为四步

- 第一步：准备工作，进行主轴交叉轴预处理
- 第二步：收集元素进行
- 第三步：计算主轴
- 第四步：计算交叉轴

#### 绘制

- npm i images
- 第一步：绘制单个元素
- 第二步：绘制DOM

### 重学CSS

- 总论

#### 第一步：CSS语法的研究

- CSS2.1的语法
- BFC 块级格式化上下文

##### CSS总体结构

- @charset
- @import
- rules
  - @media
  - @page
  - rule

#### 第二步：CSS@规则的研究

- @namespace
- @supports
- @document
- @font-face
- @keyframes
- @viewport
- @counter-style

#### 第三步：CSS Rule 规则

- selector

- selector_group

- combinator

- simple_selector

  - type

  - - 

  - # 

  - .

  - []

  - :

  - ::

- Declaration
  - key
    - property
    - variable
  - value