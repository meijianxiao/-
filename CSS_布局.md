# CSS_布局

## float布局
1. folat被设计出来的初衷是为了实现文字环绕效果。
2. 被设置了float的元素会自动成为块级元素，display的表现形式为`block`，自动脱离文档流，并且其父元素会发生塌陷，即高度为0。
3. 一排设置了`float:left`的元素。当第一行没有足够的空间时，元素会从右往左开始，如果第一列右边第一个元素的高度最小，则元素会排列在右一的下方，如果右二比右一的高度小，那么元素会排在右二下方，以此类推。
4. 第二行元素的垂直位置受到上一行高度最高的元素影响。换个说法就是，第二行的位置以上一行高度最大的元素为准平行排列。
5. clear属性规定元素的哪一侧不允许其他浮动元素。设置clear属性的元素只会影响它本身，而不是它旁边的元素。例如：块1和块2均为`float:left`，两个块水平紧挨着排列，想让块2去下一行，应该设置块1的属性值为：`clear:right`

在子元素上加`float:left`和`width`
在父元素上加`clearfix`
```css
.clearfix{
    content:"";
    display:block;
    clear:both
}
```

## flex布局
### flex container
让一个元素变成flex容器
```css
container{
    display:flex;/*or inline-flex*/
}
```

1.flex-direction 属性决定了项目的排列方式
```css
.container{
    flex-direction:row | row-reverse | column | column-reverse;
    /*  row（默认）：项目横向排列，方向由左向右

        row-revserse：项目横向排列，方向由右向左

        column：项目纵向排列，方向由上到下

        column-severse：项目纵向排列，方向由下到上*/
}
```

2.flex-wrap属性 决定了项目排列满屏，是否换行
```css
.container{
    flex-wrap:nowrap | wrap | wrap-reverse;
    /*  nowrap（默认）：不换行

        wrap:换行，第一行在上面

        wrap-reverse：换行，第一行在下面*/
}
```

3.flex-flow 属性是flex-direction属性和flex-wrap属性的简写。
```css
flex-flow：<flex-direction> <flex-wrap>
```
默认 flex-diretion：row nowrap；


4.justify-content:决定了项目在主轴上的对齐方式
```css
.container{
    justify-content:flex-start | flex-end | center | space-between | space-around
    /*  flex-start（默认）：左对齐

        fle-end：右对齐

        center：居中排列

        space-between：两端对齐，项目之间的间隔都相等

        space-around：每个项目的左右间隔都相等（每一个项目都被空白包围，且左右间隔相等）*/
}
```

5.align-items属性 决定了项目在交叉轴上的对齐方式
```css
.container{
    align-items:flex-start | flex-end | center | baseline | stretch
    /*  flex-start:上对齐

        flex-end：下对齐

        center：居中对齐

        baseline：项目的第一行文字的基线对齐

        stretch（默认）：如果项目没有设置固定高度或设置为auto，项目则占满整个屏幕*/
}
```

6.align-content属性 决定了多根轴线的对齐方式
 注意：若轴线只有一根则该属性不会起作用
 ```css
.container{
    align-content:flex-start | flex-end | center | space-around | space-between | stretch
    /*  flex-start :与交叉轴的起点对齐，以上边界排列

        flex-end：与交叉轴的终点对齐，以下边界排列

        center：与交叉轴的中点对齐，中间排列

        space-around：每根轴线的两侧间隔相等

        space-between：与上边界与下边界两端对齐，且每根轴线的间隔相等

        stretch（默认）：轴线占满交叉轴*/
}
 ```

 ## grid布局
成为container
 ```css
.container{
    display:grid | inline-grid;
}
 ```

 布局行和列
 ```css
.container{
    grid-template-columns:40px 50px auto  50px 40px;
    grid-template-rows:25% 100px auto;
    /*grid-template-columns属性定义每一列的列宽，
      grid-template-rows属性定义每一行的行高。*/
}
 ```

 repeat()函数
 ```css
.container{
    grid-template-columns:repeat(4,25%);
    grid-template-rows:repeat(4,25%)
}
 ```

 auto-fill关键字
 ```css
 .container {
  grid-template-columns: repeat(auto-fill, 100px);
}
 ```

 fr关键字
 ```css
 .container {
  grid-template-columns: 1fr 1fr;
  /* 表示两个相同宽度的列*/
  grid-template-columns: 150px 1fr 2fr;
  /* 表示第一列的宽度为150像素，第二列的宽度是第三列的一半*/
}
```

grid-template-areas属性
```css
.container {
  grid-template-columns: 100px 100px 100px;
  grid-template-rows: 100px 100px 100px;
  grid-template-areas: 'a b c'
                       'd e f'
                       'g h i';
   /*上面代码先划分出9个单元格，然后将其定名为a到i的九个区域，分别对应这九个单元格。*/
}
```

布局实例
```css
grid-template-areas: "header header header"
                     "main main sidebar"
                     "footer footer footer";
  /* 顶部是页眉区域header，底部是页脚区域footer，中间部分则为main和sidebar。*/
```