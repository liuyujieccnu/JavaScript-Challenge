## 03 CSS Variable

### 任务目标

* 使用CSS变量

### 参考资料

[阮一峰：CSS 变量教程](http://www.ruanyifeng.com/blog/2017/05/css-variables.html)

### 其他知识点

#### CSS filter（滤镜）

* blur(px)

  给图片设置高斯模糊

* [其他参数](http://www.runoob.com/cssref/css3-pr-filter.html)

#### 事件`change`

* 该事件在表单元素的内容改变时触发( `<input>, <keygen>, <select>, 和 <textarea>`)。

#### 事件`mousemove`

* 鼠标被移动。
* 在鼠标移动过程中也可以实现相关的变化。

#### HTML5中的自定义数据属性`dataset`

* HTML5 中可以为元素添加非标准的自定义属性，只需要加上 data- 前缀，可以随便添加和命名。添加之后，可以通过元素的 dataset 属性来访问这些值，dataset 的值是 DOMStringMap 的一个实例化对象，其中包含之前所设定的自定义属性的“名-值”对。
* 应用举例

```html
<div id="day2-meal-expense" data-drink="coffee" data-food="sushi" data-meal="lunch">¥20.12</div>
```

```js
var expenseday2 = document.getElementById('day2-meal-expense');
var typeOfDrink = expenseday2.dataset.drink;//获取这个属性的值
```

* 注意使用是的驼峰命名法，如html中`data-meal-time`在JavaScript中获取应为`*.dataset.mealTime`
* [参考资料:HTML5自定义属性对象Dataset简介](http://www.zhangxinxu.com/wordpress/2011/06/html5自定义属性对象dataset简介/)

### 关于finished代码中的一些理解

#### 1.如何处理参数值（一个有 px 、另一个没有）

运用 dataset 储存后缀，有 px 后缀的标签中设置 <input data-sizing: px>：

```html
<input type="range" name="blur" min="0" max="25" value="10" data-sizing="px">
<input type="color" name="base" value="#8aa8af">
```

JS 中通过 dataset.sizing 来获取后缀值：

```js
const suffix = this.dataset.sizing || '';
此时 suffix 获取到的值，针对颜色为空，而针对长度类的则为 'px'。
```

#### 2.如何用 JavaScript 改变 CSS 属性值？

在 JavaScript 中 document.documentElement 即代表文档根元素。所以要改变全局的 CSS 变量，可以这样写：

```js
document.documentElement.style.setProperty('--base', '#fff');
```

#### 3.`document.documentElement`表示文档的根元素，对于HTML文档来说就是<html>。