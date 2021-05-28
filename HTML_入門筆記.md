# html 入门笔记

html由Tim Berners-Lee发明


html起手应该写
```
文档类型 html
html标签，把en改为zh-CN
文件的字符编码 utf-8
标题
```

常用的标签有
```
h1-h6   标题
section 章节
article 文章
p       段落
header  头部
footer  腿部
main    主要内容
aside   旁支内容
div     划分
```

全局属性
```
class 为元素设置类标识，多个类名用空格分开，CSS和javascript可通过class属性获取元素
contenteditable 规定元素内容是否可编辑
hidden 表示一个元素是否与文档。样式上会导致元素不显示，但是不能用这个属性实现样式效果
id 元素id，文档内唯一(慎用，出现同样的id不会报错)
style 行内css样式
tabindex 设置元素可以获得焦点，通过tab可以导航
title 元素相关的建议信息
```

内容标签
```
ol+li  有序列表
ul+li  无序列表
dl+dt+dd 定义描述列表
pre 可以编辑自己想要的内容格式
hr 水平线
br 换行
a  超链接
em 把文本定义为强调的内容(倾斜)。
strong 把文本定义为语气更强的强调的内容(加粗)
code 用于表示计算机源代码或者其他机器可以阅读的文本内容。
q  短引用
blockquote 是使用来定义摘自另一个源的块引用，在该标签中的内容将会被从常规文本中分离出来，默认会表现为左右两侧缩进的文本，
```