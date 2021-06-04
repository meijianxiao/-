# js的基本语法

## 表达式
　　一个表达式返回一个值，js中的一个短语，js解释器将会计算出一个结果。程序中的常量是最简单的一类表达式。变量名也是一种简单的表达式，它的值就是赋值给变量的值
　　1. 在javascript中所有表达式都有返回值(如果没有返回值就是undefined)，这个返回值就可以继续作为表达式的一部分。大多数语言表达式的定义为
　　　　1. 字面量(例如1，2，3，'abc')
　　　　2. 运算符 表达式(一元，比如!true)
　　　　3. 表达式 运算符 表达式(二元，比如1+2)
　　　　4. 表达式1 ? 表达式2 : 表达式3(三元，a>b?a:b)
　　　　5. 左括号 表达式 右括号( (1+2))
　　　　6. 表达式(参数列表)(函数调用)
　　　　7. 函数表达式：(function(){return 'abc'}())  //abc

　　2. 用","串联，但是返回的是后面的值
　　　　1. var a = "1","2"  //"2"
　　　　2. a  // "1"

## 语句
　　js整句或命令。js语句是以分号结束：表达式计算出一个值，但语句用来自行以使某件事发送。“使某件事发生”的一个方法是计算带有副作用的表达式
　　1. 语句有：
　　　　1. 函数声明
　　　　2. 变量声明(var a=1是声明和赋值)
　　　　3. for语句、if语句、while语句、switch语句、return、try catch
　　　　4. 但是javascript还有一种函数表达式，它的形式跟函数声明一模一样。如果写function fn(){return 0;}是函数声明，而写var a = function fn(){return 0;}等号后面的就是函数表达式

　　2. 用";"来分割语句
　　3. eval是个语句
　　　　1. eval('{foo:222}') //222
　　　　2. eval('({foo:222})') //{foo:222}

## 标识符
　　标识符就是一个名称。该名称可以用来命名变量、函数或属性，或者用作javascript代码中某些循环语句中的跳转位置的标签。
　　在javascript中，主要规范如下：
　　　　1. 标识符第一个字符必须是字母、下划线`_`或者`$`，其后的字符可以是字母、数字或下划线、美元符号
　　　　2. 自定义的标识符不能喝javascript中的关键字及保留字同名，但可以包含关键字或保留字
　　　　3. 标识符不能包含空格
　　　　4. 标识符不能包含+、-、@、#等特殊字符
　　　　5. 由多个单词组成的复合标识符命名主要有两种方式
　　　　　　*. 一是使用下划线链接各个单词，每个单词全部小写，例如：dept_name
　　　　　　*. 二是使用驼峰式，其中又分大驼峰和小驼峰。大驼峰的格式是每个单词的首字母大写，其余字母小写，例如：DeptName;小驼峰的格式是第一个单词全部小写，第二个单词开始的每个单词首字母大写，例如：deptName

　　合格标识符示例：
　　```
　　user_name
　　userName
　　_name
　　$name
　　ab
　　ab123q33204
　　```
　　非法标识符示例：
　　```
　　1a //第一个字符不能为数字
　　a b  // 不能包含空格
　　a@b //包含特殊符号
　　while  //关键字
　　```

## if else语句
　　当条件成立的时候会执行if陈述句里的程式，而不成立时则执行另外一个陈述式
    语法
    ```javascript
    if (condition)        
    {       
        当条件为 true 时执行的代码      
    }        
    else        
    {        
        当条件不为 true 时执行的代码        
    }   
    ```


    ### if...else if...else
　　语法
    ```javascript
    if (condition1)       
    {        
        当条件 1 为 true 时执行的代码       
    }       
    else if (condition2)       
    {        
        当条件 2 为 true 时执行的代码      
    }        
    else        
    {        
    当条件 1 和 条件 2 都不为 true 时执行的代码        
    }
    ```

## while 循环
　　while循环会在指定条件为真时循环执行代码块
　　语法
　　```javascript
     while (条件)
    {
    需要执行的代码
    }
　　```
    ### do/while
    do/while循环是while循环的变体。该循环会在检查条件是否为真之前执行一次代码块，然后条件为真的话，就会重复这个循环
    语法
    ```javascript
     do
    {
    需要执行的代码
    }
    while (条件);
    ```

## for循环
　　循环可以将代码执行指定的次数
　　语句
　　```javascript
    for (语句 1; 语句 2; 语句 3)        
    {        
    被执行的代码块        
    }
　　```
　　语句1(代码块)开始前执行的starts。
　　语句2 定义运行循环(代码块)的条件
　　语句3在循环(代码块)已被执行之后执行

## break 和 Continue
　　break 语句用于跳出循环
　　continue用于跳过循环中的一个迭代
　　### break语句
　　```javascript
　　for (i=0;i<10;i++)
    {
    if (i==3)
        {
        break;
        }
    console.log(i) ;
    } // 0 1 2 
　　```
　　### continue语句
　　```javascript
    for (i=0;i<=10;i++)
    {
    if (i==3) continue;
    console.log(i);
    } // 0 1 2 4 5 6 7 8 9 10
　　```

## label语句
　　又称标记语句.作用是在语句前面加个可以引用的标识符。相当于将一条语句存储在一个变量里面,类似函数的函数名.
　　label语句一般与break和continue或代码块一起使用.
　　### 与break一起使用
　　```javascript
    for(var i=0;i<10;i++){
        for(var j=0;j<10;j++){
        if(i == 2){
        //do something
        break;
        }
        }
    }
    console.log(i);//10
    outFor: for(var i=0;i<10;i++){
        for(var j=0;j<10;j++){
        if(i == 2){
            //do something
            break outFor;
        }
        }
    }
    console.log(i);//10
　　```
　　在第一个for循环中,当外循环执行到第三次,即i=2的时候,break将内层for循环结束;i继续增加;所以最后i一直增加到10;在第二个for循环中,使　　用label语句将外层循环添加标记"outFor",当执行到i=2时,break outFor;实现将外层循环结束.所以i为2.也就实现了双重for循环中,在内层循　　环结束掉外层循环.弥补了单纯的break只能结束所在for循环的不足.

　　### 与continue一起使用
　　```javascript
    for(var i=0;i<10;i++){
        for(var j=0;j<10;j++){
        if(i == 2){
            continue;
            }
        }
        console.log(0);//10次
    }
    outFor: for(var i=0;i<10;i++){
        for(var j=0;j<10;j++){
        if(i == 2){
            continue outFor;
        }
        }
        console.log(0);//9次
    }
　　```
　　第一个for循环中continue结束的是内层的for循环,外层for循环继续执行,所以每次外层的循环都会打印一次0,一共打印10次.第二个for循环中,　　continue结束的外层循环,所以会少执行一次打印,一共打印9次.

　　### 与代码块一起使用
　　给代码块添加标记,并在某一阶段break;相当于函数的return.
　　```javascript
    foo: {
        console.log('进入代码块');
        break foo;
        console.log('break后不执行');
    }
    console.log('代码块外的打印');
    //进入代码块
    //代码块外的打印
　　```