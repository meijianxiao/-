# jQuery的设计思想
jQuery的主要设计思想就是，选择某个网页元素，然后使用相对于DOM操作对其进行某种简化操作，jQuery的实质就是一个封装的DOM库

## jQuery如何获取元素
* css选择器获取元素
  ```javascript
    $(document) // 选择整个文档对象
    $('#test') // 选择id为test的网页元素
    $('div.myClass') // 选择class为myClass的div元素
    $('input[name=first]')  // 选择name属性等于first的input元素
  ```
* jQuery特有的表达式获取元素
  ```javascript
    $('a:first') // 选择网页中第一个a元素
    $('tr:odd') // 选择表格的奇数行
    $('#myFrom:input') // 选择表单中的input元素
    $('div:visible') // 选择可见的div元素
    $('div:gt(2)') // 选择所有的div元素，除了前三个
    $('div:animated') // 选择当前处于动画状态的div元素
  ```
## jQuery的链式操作
jQuery选中网页元素以后，可以对它进行一系列操作，并且所有操作可以连接在一起，以链条的形式写出来
`$(.div).addClass('.red').text().find('h2')`
这样以点连起来的连续调用就称为链式调用，它的设计原理是把jQuery中的函数返回为这个对象，然后这个对象又包含jQuery的所有方法，这样就可以实现链式调用

## jQuery中如何创建元素
只要把新元素直接传入jQuery的构造函数就行了
```javascript
    $('<div>我是被创建的元素</div>')
    $('<h2>我是被创建的元素</h2>')
    $('<div><h2>我是被创建的元素</h2></div>')
```

## jQuery中如何移动元素
* `.insertAfter()`和`.after()`: 在现存元素的外部，从外面插入元素
* `.insertBefore()`和`.before()`:  在现存元素的外部，从前面插入元素
* `.appendTo()`和`.append()`: 在现存元素的内部，从后面插入元素
* `.perpendTo()`和`.prepend()`: 在现存元素的内部，从前面插入元素

## jQuery中如何修改元素的属性
这里运用了重载的设计模式
+ `.attr(name,value)`和`.attr(name)`: 两个参数是设置属性，一个参数是获取属性值
+ `.text()`和`.text(string)`: 无参数是获取文本，一个参数是写入文本
+ `.html()`和`.html(string)`: 无参数是获取html元素，一个参数的写入html元素

## jQuery中如何实现JS中各函数对象prototype里的方法
- `$.trim()` 去除字符串两端的空格
- `$.each()` 遍历一个数组或对象
- `$.inArray()` 返回一个值在数组中的索引位置，如果改值不在数组中，则返回-1
- `$.grep()` 返回数组中符合某种标准的元素
- `$.extend()` 将多个对象，合并到第一个对象
- `$.makeArray()` 将对象转化为数组
- `$.type()` 判断对象的类别(函数对象，日期对象，数组对象，正则对象等)
- `$.isArray()` 判断某个参数是否为数组
- `$.isEmptyObject()` 判断某个对象是否为空
- `$.isFunction()` 判断某个参数是否为函数
- `$.isPlainObject()` 判断某个参数是否为用'{}'或'new Object'建立的对象
- `$.support()` 判断浏览器是否支持某个特性

## jQuery中的事件操作
+ `.blue()`表单元素失去焦点
+ `.change()` 表单元素的值发生变化
+ `.click()` 鼠标点击
+ `.dblclick()` 鼠标双击
+ `.focus()` 表单元素获得焦点
+ `.focusin()` 子元素获得焦点
+ `.focusout()` 子元素失去焦点
+ `.hover()` 同时为mouseenter和mouseleave事件指定处理函数
+ `.keydown()` 按下键盘(长时间按键，只返回一个事件)
+ `.keypress()` 按下键盘(长时间按键，将返回多个事件)
+ `.keyup()` 松开键盘
+ `.load()` 元素加载完毕
+ `.mousedown()` 按下鼠标
+ `.mouseenter()` 鼠标进入(进入子元素不触发)
+ `.mouseleave()` 鼠标离开(离开子元素不触发)
+ `.mousemove()` 鼠标在元素内部移动
+ `.mouseout()` 鼠标离开(离开子元素也触发)
+ `.mouseover()` 鼠标进入(进入子元素也触发)
+ `.mouseup()` 松开鼠标
+ `.ready()` DOM加载完成
+ `.resize()` 浏览器窗口的大小发生改变
+ `.scroll()` 滚动条的位置发生变化
+ `.select()` 用户选中文本框中的内容
+ `.submit()` 用户递交表单
+ `.toggle()` 根据鼠标点击的次数，依次运行多个函数`.unload()`用户离开页面

