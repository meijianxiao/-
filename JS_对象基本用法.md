- [js 对象基本用法](#js-对象基本用法)
  - [声明对象的两种语法](#声明对象的两种语法)
  - [如何删除对象的属性](#如何删除对象的属性)
  - [如何查看对象的属性](#如何查看对象的属性)
  - [如何修改或增加对象的属性](#如何修改或增加对象的属性)
    - [修改或增加属性](#修改或增加属性)
    - [修改或增加共有属性](#修改或增加共有属性)
    - [修改隐藏属性](#修改隐藏属性)
  - ['name' in obj和obj.hasOwnProperty('name')的区别](#name-in-obj和objhasownpropertyname的区别)


# js 对象基本用法

　　对象是一个包含相关数据和方法的集合(通常由一些变量和函数组成，我们称之为对象里面的属性和方法)

## 声明对象的两种语法
```javascript
    let obj = {'name':'frank','age':15}
    let obj = new Object({'name':'frank'})
```
两种写法都可以，第二种更加规范
* 键名是字符串，不是标识符，可以包含任意字符
* 引号可以省略，但键名还是字符串，省略之后就只能写标识符

## 如何删除对象的属性
delete obj.xxx 或delete obj['xxx']
　　如果使用undefined，属性名还在，属性值为undefined
```javascript
    let obj = {age:18}
    obj.age = undefined
    obj // {age:undefined}
```
　　如果使用delete obj.age,age以及其属性值都没了
```javascript
    let obj = {age:18}
    delete obj.age // true
    obj // {}  属性名以及属性值都没了
```
* 注意，删除一个不存在的属性，delete不会报错，返回true
* delete命令只能删除对象本身的属性，无法删除继承的属性

## 如何查看对象的属性
* 查看一个对象的自身所有属性
```javascript
    let obj = {name:'jack',age:20}
    Object.keys(obj) // ["name", "age"]
```

* 查看一个对象自身+共有属性
```javascript
    let obj = {name:jack,age:19}
    console.dir(obj) // [age:20,name:'jack',__proto__:Object]
```

* 判断一个属性是自身的还是共有的

　　obj.hasOwnProperty('age')
如果返回的是true就是自身的，反之false就是共有的


## 如何修改或增加对象的属性
### 修改或增加属性
* 直接赋值
```javascript
    let obj = {name:'jack'}
    obj.name = 'jack'
    obj['name'] = 'jack'
    obj['na'+'me'] = 'jack'
    let key = 'name'
    obj[key] = 'jack'
```
* 批量赋值
```javascript
    Object.assign(obj,{name:'tom',age:12})
```
### 修改或增加共有属性
```javascript
    obj.__proto__.toString='xxx'
    Object.prototype.toString = 'xxx'
```
一般来说，不要修改原型，会引起很多问题

### 修改隐藏属性
* 不推荐使用__proto__
```javascript
    let obj = {name:'jack'}
    let obj2 = {name:'tom'}
    let common = {kind:'human'}
    obj.__proto__ = common
    obj2.__proto__ = common
```
* 推荐使用Object.create
```javascript
    let obj = Object.create(common)
    obj.name = 'jack'
    let obj2 = Object.create(common)
    obj2.name = 'tom'
```

## 'name' in obj和obj.hasOwnProperty('name')的区别
```javascript
    'toString' in obj  // true  in是查看，但并不知道是自身的还是共有属性
    obj.hasOwnProperty('toString') // false  说明toString不是自身属性
    let obj = {name:'jack',age:12}
    obj.hasOwnProperty('name') // true
    obj.hasOwnProperty('toString') // false
```
* 'xxx' in obj 并不知道查看的是自身属性还是共有属性
* obj.hasOwnProperty('xxx')查看的是自身的属性