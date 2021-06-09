##  深入理解6个6
```javascript
    let i=0
    for(i=0;i<6;i++){
        setTimeout(()=>{console.log(i)},0)
    }  // 6 6 6 6 6 6
```
* setTimeout()方法用于在指定的毫秒数后调用函数或计算表达式；其意思是尽快，而不是马上

**解释** 因为setTimeout是一个异步任务，执行到这里的操作会被浏览器丢到另一个任务列表里去，浏览器这时候会继续执行for循环。每一次执行for循环的时候，setTimeout都执行一次，但是里面的函数没有被执行，而是被放到了任务列表里面，等待执行，for循环了6次，就放了6次，当主线程执行完成后，才进去任务列队里面执行。这时候因为for循环了6次，所以输出6个6.

**异步** 异步代码不等待结果，直接进行下面的代码，所以定时器只是开启了，而没有立即执行里面的代码，等到当前运行坏境的代码执行完之后再回来执行定时器里面的代码。总结：异步就是不等待结果的代码。

## 如何打印出(0,1,2,3,4,5)

### 方法一：let关键字
```javascript
    for(let i =0;i<6;i++){
        setTimeout(()=>{
            console.log(i)
        },0)
    }  // 0,1,2,3,4,5
```

**解释** 因为let变量的作用域只能在当前函数中，所以每次for循环生成的都是一个新的i,setTimeout里输出的i就是这个新的i，这个i是不会变化的，所以输出的就是正常的。

### 方法二：闭包
```javascript
    let i 
    for(i = 0;i < 6;i++){
        !function(i){
            setTimeout(()=>{
                console.log(i)
            },0)
        }(i)
    } // 0,1,2,3,4,5
```
* 声明匿名函数 function(value){} 包裹setTimeout()
* 然后再匿名函数前加上运算符`!`，防止生成新的全局变量
* 在匿名函数后加个()立即调用，并把`i`当作参数value传入匿名函数进行调用

### 方法三：利用setTimeout的第三个参数,将i传进去
```javascript
    let i 
    for(i = 0;i < 6;i++){
        setTimeout((value)=>{
            console.log(value)
        },0,i)
    }  // 0,1,2,3,4,5
```
**原理** 使用setTimeout的第三个参数可以将自身传给第一个参数也就是匿名函数function(value)中，作为所需要的参数value，value可默认不写而`i`共传入6次，（0，1，2，3，4，5），通过匿名函数即可打印出
通常不写第三个三处，如果默认不写第三个参数，则不会传入函数

### 方法四：const关键字
```javascript
    let i 
    for(i = 0;i<6;i++){
        const a = i
        setTimeout(()=>{
            console.log(a)
        })
    } // 0,1,2,3,4,5
```

## setTimeout的意思
```javascript
    setTimeout(fn(),1000)
    f2()
```
1000ms后尽快执行fn()，不代表马上执行，如f2()中写了10000行代码，需要花10秒执行完,那么,fn()会在10秒之后执行。