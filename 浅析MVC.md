# MVC(Model-View-Controller)

Model: 数据模型，负责操作所有的数据
View: 视图，负责所有UI界面
Controller: 控制器，负责其他

```javascript
// 数据放在m
const m = {
    data:{},
    create:{增加数据},
    delete:{删除数据},
    update(data):{
        Object.assign(m.data,data) // 用新数据替换旧数据
    },
    get:{获取数据}
}
```

```javascript
// 视图放在v
const v = {
    el:null，// 要刷新的元素
    html: ,  // 显示在页面上的内容
    init(container){v.el = $(container)},
    render(){} // 刷新页面
}
```
```javascript
// 负责其他
const c = {
    init(){
        v.init()  // 初始化View
        v.render() // 第一次渲染页面
        c.autoBindEvents() // 事件的自动绑定
        eventBus.on('m:update',()=>{v.render()}) // 当eventsBus触发'm:update'使View刷新    
    }，
    events:{},// 事件以哈希表的方式记录存储
    method(){
        data = 新数据
        m.update(data)
    },
    autoBindEvents(){} // 自动绑定事件
}
```

# EventBus 有哪些 API ,是做什么用的

1. EventBus 基本的 api 有 on (监听事件)，trigger(emit) (触发事件)，off (取消监听)方法
2. 用于模块间的通讯，View 组件层面，父子组件，兄弟组件通信都可以使用 eventBus 处理

```javascript
// 触发事件，事件名不能有空格
eventBus.trigger('m:update')
// 监听事件
eventBus.on('m:update',()=>{
    v.render(m.data)
    localStorage.setItem("x",m.data)
})
```
可以用 jquery 引入
```javascript
    const eventBus = $({windwo})
```

# 表驱动编程是做什么的

1. 表驱动法是一种编程模式(scheme)——从表里面查找信息而不使用逻辑语句(if和case)
2. 表驱动编程是一种很重要的编程思想，它的理念是从大量相似的代码中抽取出本质的东西，组成哈希表，利用表进行编程，以减少重复代码
3. 事实上，凡是能通过逻辑语句来选择的事物，都可以通过查表来选择。对简单的情况而言，使用逻辑语句更为容易和直白。但随着逻辑链的越来越发杂，查表法也就愈发显得更具吸引力
```javascript
    const c = {
        events:{   // 哈希表
            'click #add1':'add',
            'click #minus1':'minus',
            'click #mul2':'mul',
            'click #divide2':'divide'
        },
        add() {
            m.update({n: m.data.n + 1})
        },
        minus() {
            m.update({n: m.data.n - 1})
        },
        mul() {
            m.update({n: m.data.n * 2})
        },
        div() {
            m.update({n: m.data.n / 2})
        },
        autoBindEvents(){
            for(let key in c.events){
            const value = c[c.events[key]]
            const spaceIndex = key.indexOf(' ')
            const part1 = key.slice(0,spaceIndex)
            const part2 = key.slice(spaceIndex+1)
            v.el.on(part1,part2,value)  //通过遍历哈希表监听事件
        }
    }
}
```

# 模块化

模块化能够帮助开发者拆分和组织代码，随着前端技术飞速的发展，代码量也越来越大，就需要对代码进行很好的管理，而模块化能够帮助开发者解决命名冲突、管理依赖、提高代码的可读性、代码解耦以及提高代码的复用性。