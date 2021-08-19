# ES6 新特性汇总

## 一、解决原有语法的缺陷和不足

### 1、let: 块级作用域，没有变量提升

用途：for 循环的计数器(for 循环内部 let 声明的变量同样拥有块级作用域)；循环事件绑定不必采用闭包形式

```javascript
for (let i = 0; i < 3; i++) {
  let i = "foo";
  console.log(i);
}
```

### 2、const:恒量/常量；声明后不能修改内存地址，可修改属性成员

最佳实践：不用 var,主用 const，配合 let

## 二、对原有语法的增强

### 1、数组的解构：根据数组对应的位置提取对应的值赋给对应的变量

```javascript
let arr = [1, 2, 3];
let [x, y, z] = arr;
```

如果未取到对应的值，赋值"undefined"
可以用...运算符

```javascript
var [x, ...other] = arr;
```

可以设置默认值

```javascript
var [x = "0", y, z] = arr;
```

用途：字符串截取

```javascript
const str = "http://www.baidu.com?titile=article";
var [, strParam] = str.split("?");
```

### 2、对象的解构：根据属性名提取

```javascript
const obj = { name: "zdd", age: 18 };
const { name, age } = obj;
```

如果想换一个变量名&添加默认值

```javascript
const { name: objName = "www", age } = obj;
```

应用场景：代码简化

```javascript
const { log } = console;
log("hh");
```

### 3、模板字符串：字符串增强

1. 可换行
2. 可使用插值表达式添加变量，变量也可以替换为可执行的 js 语句

```javascript
let str = `生成一个随机数：${Math.random()}`;
```

标签模板字符串，标签相当于一个自定义函数，自定义函数的第一个参数是被差值表达式截取的数组

```javascript
// 标签模板字符串
const name = "www";
const isMan = true;
const tagFn = function (strings, name, isMan) {
  let sex = isMan ? "man" : "woman";
  return strings[0] + name + strings[1] + sex + strings[2];
};
const result = tagFn`hey, ${name} is a ${isMan}.`;
```

### 4、字符串的扩展方法

1. includes
2. startWith
3. endsWith

### 5、函数参数增强：参数默认值

只有当参数为不传或传入 undefined 时使用默认值

```javascript
const fn = function (x = 1, y) {
  console.log(x);
  console.log(y);
};
fn();
```

### 6、...操作符：收起剩余数据、展开数组

收取剩余参数：取代 arguments, arguments 是一个类数组，...操作符是一个数组类型，可以使用数组方法
1、仅使用一次
2、放在参数最后

```javascript
const fn = function (x, ...y) {
  console.log(y.slice(0));
};
fn(1, 2, 3, 4, 5);
```

展开数组

```javascript
const spreadArr = [1, 2, 3, 4];
console.log(...spreadArr);
console.log.apply(this, spreadArr); //es5代替方案
```

### 7、箭头函数：简化写法

箭头函数的 this 指向上级作用域

```javascript
const name = "tony";
const person = {
  name: "tom",
  say: () => console.log(this.name),
  sayHello: function () {
    console.log(this.name);
  },
  sayHi: function () {
    setTimeout(function () {
      console.log(this.name);
    }, 500);
  },
  asyncSay: function () {
    setTimeout(() => console.log(this.name), 500);
  },
};
person.say(); //tony
person.sayHello(); //tom
person.sayHi(); //tony
person.asyncSay(); //tom
```

### 8、对象字面量的增强

1、如果 key 与 value 变量名相同，省略：value
2、省略函数：function
3、计算属性：[Math.random()]

```javascript
const bar = "bar";
const obj = {
  bar,
  fn() {
    console.log("1111");
  },
  [Math.random()]: "123",
};
console.log(obj);
```

## 三、新增对象、全新的方法、全新的功能

### 1、Object.assign():合并多个对象，第一个参数就是最终的返回值，如果对象的属性名相同，后面的覆盖前面的

用途：赋值对象，给 options 属性赋默认值

```javascript
let objA = {
  a: "aa",
  b: "bb",
};
let objB = {
  b: "dd",
  c: "ee",
};
let result = Object.assign({}, objA, objB);
result.a = "cc";
console.log(objA, result); //{a: "aa", b: "bb"} {a: "cc", b: "dd", c: "ee"}
```

### 2、Object.is():判断两个值是否相等，返回布尔值

用途：es5 中，对于 0 的判断不区分正负值，-0 == +0 返回 true，NaN == NaN 返回 false,Object.is()规避了这些问题

```javascript
Object.is(+0, -0); //false
Object.is(NaN, NaN); //true
```

### 3、Proxy:代理对象

基本用法

```javascript
const person = {
  name: "www",
  age: "20",
};
const personProxy = new Proxy(person, {
  get(target, key) {
    return target[key] ? target[key] : "default";
  },
  set(target, key, value) {
    target[key] = value % 2 ? value : 99;
  },
});
console.log(person.xxx); // undefined
console.log(personProxy.xxx); // default
console.log(personProxy.age); //20
personProxy.age = 100;
console.log(personProxy); //{name: "www", age: 99}
```

## 四、全新的数据结构和数据类型

### 1、class 类

es5 写法

```javascript
function People(name) {
  // 设置实例属性
  this.name = name;
}
// 设置实例的共享方法
People.prototype.sayHi = function () {
  console.log(this.name);
};
let p = new People("tom");
p.sayHi();
```

使用 class 更容易理解，结构清晰

```javascript
class People {
  constructor(name) {
    this.name = name;
  }
  say() {
    console.log(this.name);
  }
}
const p = new People("tony");
p.say();
```

类的继承

```javascript
class People {
  constructor(name) {
    this.name = name;
  }
  say() {
    console.log(this.name); //tom，在子类的sayAge中调用
  }
}
class Worker extends People {
  constructor(name, age) {
    super(name);
    this.age = age;
  }
  sayAge() {
    super.say();
    console.log(this); // Worker {name: "tom", age: 18}
    console.log(this.age); // 18
  }
}
const p = new Worker("tom", 18);
p.sayAge();
```

### 2、set 数据结构：可以理解为集合，不重复

```javascript
const s = new Set();
s.add(1).add(2).add(3);
console.log(s); //{1, 2, 3}
console.log(s.size); // 3
const arr = [1, 2, 3, 2, 4];
console.log([...new Set(arr)]); //[1,2,3,4]
```

### 3、map 数据结构

es5 中的对象 key 只能是字符串，map 的 key 可以是任意数据类型，可以通过 get,set,has 等操作 map

```javascript
const m = new Map();
const tom = { name: "99" };
m.set(tom, 90);
console.log(m.get(tom));
m.forEach((value, key) => {
  console.log(value, key);
});
```

### 4、Symbol 新的数据结构，唯一值

用途：防止全局对象中，某个属性名重名，产生冲突；定义私有属性，外部访问不到，且遍历不到

```javascript
const s = Symbol("描述");
console.log(s);
const obj = {
  [Symbol("私有属性")]: "11",
};
console.log(obj); //obj对象Symbol('私有属性')这个属性外部访问不到
console.log(Object.keys(obj)); //[]
console.log(Object.getOwnPropertySymbols(obj)); //[Symbol(私有属性)]

const s1 = Symbol.for("111");
const s2 = Symbol.for("111");
console.log(s1 === s2); //true
```

### 5、for ... of 遍历

es5 中，使用 for ... in 遍历键值对结构数据，使用 forEach 遍历数组
es6 中新增了 set,map 数据结构，for...of 是用来统一遍历拥有某一种特性的数据结构（可迭代）

```javascript
const arr = [1, 2, 3];
for (const item of arr) {
  // 遍历数组
  console.log(item);
}
const s = new Set();
s.add(1).add(2).add(3);
for (const item of s) {
  // 遍历set结构
  console.log(item);
}
const m = new Map([
  ["name", "昵称"],
  ["title", "标题"],
]);
for (const [key, value] of m) {
  // 遍历map结构
  console.log(key);
  console.log(value);
  console.log(m.get(key));
}

const newSet = new Set([
  ["name", "昵称"],
  ["title", "标题"],
]);
const newMap = new Map(newSet);
for (const [key, val] of newMap) {
  // 遍历set初始化后的map结构
  console.log(key);
  console.log(val);
}

const obj = {
  name: "ttt",
  age: "19",
};
for (const [key, val] of obj) {
  // 遍历对象报错 Uncaught TypeError: obj is not iterable
  console.log(key, val);
}
```
