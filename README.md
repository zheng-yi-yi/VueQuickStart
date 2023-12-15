# VueQuickStart

# 一、前言

> 本文档用于记录Vue的快速入门知识点。
>
> - 视频教程：[黑马程序员vue前端基础教程-4个小时带你快速入门vue](https://www.bilibili.com/video/BV12J411m7MG)

官方文档：[Vue.js - 渐进式 JavaScript 框架 | Vue.js](https://cn.vuejs.org/)

![image-20231215165604113](images/README/image-20231215165604113.png)


# 二、内容

## 2.1 Vue 基础

### （1）简介

`Vue`其实就是一个框架，也是一个生态。我们来看官方的定义：

> **Vue (发音为 /vjuː/，类似 view) 是一款用于构建用户界面的 JavaScript 框架。它基于标准 HTML、CSS 和 JavaScript 构建，并提供了一套声明式的、组件化的编程模型，帮助你高效地开发用户界面。无论是简单还是复杂的界面，Vue 都可以胜任**。

简单的说，`Vue` 是一款流行的前端 `JavaScript` 框架，它通过双向数据绑定将视图与数据模型关联起来。`Vue`主要特点是易学易用，具有高效的性能和扩展性，支持组件化开发，提供了丰富的指令和插件，能够快速构建交互丰富的`Web`应用程序。

`Vue`的核心是响应式系统，它能够自动追踪数据变化并更新视图。通过使用指令和组件，`Vue`提供了丰富的功能， 例如条件渲染、循环渲染、事件处理、样式绑定等。 `Vue`还提供了一套完整的路由和状态管理机制，可以帮助开发者更好地组织代码和管理状态。

---

**`Vue` 的两个核心功能**：

- **声明式渲染**：`Vue` 基于标准 `HTML` 拓展了一套模板语法，使得我们可以声明式地描述最终输出的 `HTML` 和 `JavaScript` 状态之间的关系。

- **响应性**：`Vue` 会自动跟踪 `JavaScript` 状态并在其发生变化时响应式地更新 `DOM`。

---

### （2）第一个 Vue 程序

源代码：[Teaching Case/1-Vue-base.html](https://github.com/zheng-yi-yi/VueQuickStart/blob/main/Teaching%20Case/1-Vue-base.html)

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Vue基础</title>
</head>

<body>
  <div id="app">
    {{ message }}
  </div>
  <!-- 开发环境版本，包含了有帮助的命令行警告 -->
  <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
  <script>
    var app = new Vue({
      el: "#app",
      data: {
        message: "Hello World"
      }
    })
  </script>
</body>

</html>
```


以上是一个简单的 `Vue.js` 示例，知识要点如下：

```html
<div id="app">
  {{ message }}
</div>
```

这段代码在页面中创建一个具有`id`为`"app"`的`div`元素，用于 `Vue` 实例的挂载点。

双大括号 `{{ message }}` 是 `Vue` 的模板语法，表示在这个位置显示Vue实例中的 `message` 数据。

```javascript
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

通过`CDN`引入`Vue.js`库，这里使用的是开发版本。

> - 开发版本（Unminified）：包含了详细的警告和调试信息，文件相对较大。这个版本适用于开发阶段，方便开发者进行调试和定位问题。
> - 生产版本（Minified）：经过压缩和优化，去除了警告和调试信息，文件体积较小。这个版本适用于部署到生产环境，以提高页面加载速度。
> 一般来说，在开发阶段使用开发版本进行调试和开发，而在部署到生产环境时使用生产版本以获得更好的性能和较小的文件体积。

```javascript
var app = new Vue({
  el: "#app",
  data: {
    message: "Hello World"
  }
})
```

- `var app = new Vue({})`：创建一个`Vue`实例对象，该实例对象包含`el`、`data`等属性。
- `el: "#app"`：指定`Vue`实例挂载到页面上的元素，这里是`id`为`"app"`的`div`。
- `data: { message: "Hello World" }`：定义`Vue`实例的数据，这里有一个名为`message`的数据项，初始值为`"Hello World"`。
整个流程是，Vue实例被创建并挂载到id为"app"的div上，然后模板语法`{{ message }}`会将`message`的值显示在页面上。

这个例子简单地演示了`Vue`的基本用法，通过数据绑定实现了页面内容的动态更新。

---


### （3）el 挂载点

`Vue`实例的作用范围主要由`el`选项指定，它表示`Vue`实例将挂载到哪个`DOM`元素上。`Vue`会管理这个指定的元素及其内部的后代元素。当`Vue`实例被创建并挂载后，它会对该`DOM`元素及其后代元素进行数据绑定和渲染。

`el` 选项的值可以是任何合法的`CSS`选择器。比如使用类选择器：


不过，使用`ID`选择器是一种常见的做法，因为`ID`在`HTML`文档中应该是唯一的，这可以确保`Vue`实例只会挂载到页面上的特定元素上。
另外需要注意的是，我们不能将`Vue`实例挂载到`body`或`html`等根元素上。这是行不通的。


---



### （4）data 数据

在`Vue`实例中，我们使用`data`选项来定义数据。

`data`选项中定义的可以是任何`JavaScript`有效的数据类型，包括基本类型（如字符串、数字、布尔值等）和复杂类型 （如对象、数组等）。这些数据可以在模板中进行渲染，并通过`Vue`的响应式系统实现数据绑定。

举一个例子，我们定义如下数据：

```javascript
var app = new Vue({
    el: "#app",
    data: {
        message: 'Hello Vue!',
        number: 42,
        isActive: true,
        user: {
            name: 'John',
            age: 25
        },
        fruits: ['apple', 'banana', 'orange']
    }
});
```

页面如下：

```html
<div id="app">
    <p>{{ message }}</p>
    <p>{{ user.name }} is {{ user.age }} years old.</p>
    <p>{{ isActive }}</p>
    <ul>
        <li>{{ fruits[0] }}</li>
        <li>{{ fruits[1] }}</li>
        <li>{{ fruits[2] }}</li>
    </ul>
</div>
```


总的来说，在模板中渲染复杂类型数据时，遵循`JavaScript`语法即可。使用`{{ }}`插值语法来引用数据，使用`.`来访问对象的属性等。


## 2.2 Vue 指令

### （1）v-text | 文本插值

> **`v-text` 指令用于更新元素的文本内容**。


`v-text` 指令通过设置元素的 `textContent` 属性来工作，因此它将覆盖元素中所有现有的内容。

```html
<span v-text="msg"></span>
<!-- 等同于 -->
<span>{{msg}}</span>
```

后者使用 **“Mustache”** 语法（又称差值表达式，即双大括号`{{}}`），同样可以替换指定内容，同时每次 `msg` 属性更改时它也会同步更新。另外，指令内部支持写表达式。

---

### （2）v-html

> **`v-html`指令用于更新元素的 innerHTML**。


`v-html`指令的作用是设置元素的`innerHTML`，其内容中有`html`结构的话会被解析为相应标签，而 `v-text` 指令无论内容是什么，都只会解析为文本。

```html
<div v-html="html"></div>
```

需要注意的是，`v-html` 的内容直接作为普通 `HTML` 插入时，`Vue` 模板语法是不会被解析的。双大括号会将数据解释为纯文本，而不是 `HTML`。若想插入 `HTML` ，你需要使用 `v-html` 指令。

> 安全警告!
> 在网站上动态渲染任意 `HTML` 是非常危险的，因为这非常容易造成 `XSS` 漏洞。请仅在内容安全可信时再使用 `v-html`，并且永远不要使用用户提供的 `HTML` 内容。

---

### （3）v-on

> **`v-on` 指令用于给元素绑定事件监听器**。


`v-on` 指令的作用是为元素绑定事件。事件名不需要写`on`，同时，该指令可以简写为`@`。

注意，绑定的方法定义在`methods`属性中，方法内部通过`this`关键字访问定义在`data`中的数据。


举个例子：

```html
<div id="app">
    <button @click="doThis">点击</button> count : {{count}}
    <!-- 
        原始写法为：
        <button v-on:click="doThis"></button>
    -->
</div>
```

接着编写方法：

```javascript
var app = new Vue({
    el: "#app",
    data: {
        count: 0
    },
    methods: {
        doThis: function () {
            this.count++;
        }
    }
});
```

效果如下：
