## Proxy 与双向绑定

## 组件化基础

### 对象与组件

- 对象
  - Properties
  - Methods
  - Inherit
- 组件
  - Properties
  - Methods
  - Inherit
  - Attribute
  - Config & State
  - Event
  - Lifecycle
  - Children

### attribute vs property

> attribute 强调描述性 一个人帅不帅啊
> property 强调从属关系 强调财产

```
// attributr
<my-component attribute="v" />
myComponent.getAttribute("a")
myComponent.setAttribute("a", "value")

// property
myComponent.a = "value"

// example1
<div class="cls1 cls2"></div>
<script>
  var div = document.getElementByTagName('div');
  div.className //cls1 cls2
</script>

// example2
<div class="cls1 cls2" style="color: blue"></div>
<script>
  var div = document.getElementByTagName('div');
  div.style //对象
</script>

// example3
<a href="//m.taobao.com"></a>
<script>
  var a = document.getElementByTagName('a');
  a.href // "http://m.taobao.com", 这个URL是resolve过的结果
  a.getAttribue('href') // "m.taobao.com"， 跟HTML代码中完全一致
</script>

// example4
<input value="cute" />
<script>
  var input = document.getElementByTagName('input');
  //若property没有设置，则结果是attribute
  input.value // cute
  input.getAttribute('value') //cute
  input.value = "hello"
  //若value属性已经设置，则attribute不变，property变化，元素上的实际效果是property优先

  input.value //hello
  input.getAttribute('value') //cute 有点像默认值的样子
</script>
```

### 如何设计组件状态 一般在设计组件体系的时候要考虑

| Markup set | JS set | JS Change | User Input Change | 属性      |
| ---------- | ------ | --------- | ----------------- | --------- |
| ❌          | ✔️      | ✔️         | ❓                 | Property  |
| ✔️          | ✔️      | ✔️         | ❓                 | Attribute |
| ❌          | ❌      | ❌         | ✔️                 | State     |
| ❌          | ✔️      | ❌         | ❌                 | config    |

#### 案例

## LifeStyle

created -> destroyed

- children content型children与template型children

```
<my-button>
  <img src="{{icon}}" />{{title}}
</my-button>

<my-list>
  <li>
    <img src="{{icon}}" />{{title}}
  </li>
</my-list>
```

## JSX 环境搭建

- 提前安装 webpack
- 安装 npm
- babel-loader