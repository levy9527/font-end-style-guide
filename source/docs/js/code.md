title: 代码规范
---

## 编码规范

统一团队的编码规范，有助于代码的维护。本章是传统意义上的 `Style Guideline`，目的是统一一些相对主观化的代码风格。

### 单行代码块

在单行代码块中使用空格

*不推荐*

```js
function foo () {return true}
if (foo) {bar = 0}
```

*推荐*

```js
function foo () { return true }
if (foo) { bar = 0 }
```

### else 关键字要与花括号保持在同一行

*推荐*
````js
if (condition) {
  // ...
} else {
  // ...
}
````

*不推荐*
````js
if (condition)
{
  // ...
}
else
{
  // ...
}
````

### 变量和函数命名使用驼峰式命名

*推荐*
```js
  function my_function () { }
  
  let my_var = 'hello'          
```

*不推荐*

```js  
  function myFunction () { }
 
  let myVar = 'hello'           
```


### 不允许有多余的行末逗号

*不推荐*

```js
let foo = {
  name: 'foo',
}
```

*推荐*

````js
let foo = {
  name: 'foo'
}
````

### 逗号空格

逗号前后的空格可以提高代码的可读性
> 团队约定在逗号后面使用空格，逗号前面不加空格。

*不推荐*

```js
let foo = 1,bar = 2
let foo = 1 , bar = 2
let foo = 1 ,bar = 2
```

*推荐*

```js
let foo = 1, bar = 2
```

### 始终将逗号置于行末

*不推荐*

```js
let foo = 1
,
bar = 2

let foo = 1
, bar = 2

let foo = ['name'
          , 'age']
```

*推荐*

```js
let foo = 1,
    bar = 2

let foo = ['name',
            'age']
```

### 在对象的计算属性内，禁止使用空格

*不推荐*

```js
obj['foo' ]
obj[ 'foo']
obj[ 'foo' ]
```

*推荐*

```js
obj['foo']
```

### 拖尾换行

在非空文件中，存在拖尾换行是一个常见的 `UNIX` 风格，它的好处是可以方便在串联和追加文件时不会打断 `Shell` 的提示。在日常的项目中，保留拖尾换行的好处是，可以减少版本控制时的代码冲突。

*不推荐*

```js
function func () {
  // do something
}
```

*推荐*

```js
function func () {
  // do something
}
  // 此处是新的一行
```

### 函数调用

为了避免语法错误，团队约定在函数调用时，禁止使用空格

*不推荐*

```js
fn ()
fn
()
```

*推荐*

```js
fn()
```

### 使用两个空格进行缩进

### 对象字面量的键值缩进

> 团队约定对象字面量的键和值之间不能存在空格，且要求对象字面量的冒号和值之间存在一个空格

*不推荐*

```js
let obj = { 'foo' : 'haha' }
```

*推荐*

```js
let obj = { 'foo': 'haha' }
```

### 构造函数首字母大写

在 JavaScript 中 `new` 操作符用来创建某个特定类型的对象的一个实例，该类型的对象是由一个构造函数表示的。由于构造函数只是常规函数，唯一区别是使用 `new` 来调用。

*不推荐*

```js
let fooItem = new foo()
```

*推荐*

```js
let fooItem = new Foo()
```

### 无参的构造函数调用时要带上括号

*不推荐*

```js
let person = new Person
```

*推荐*

```js
let person = new Person()
```

### 点号操作符须与属性需在同一行

*不推荐*

```js
 console.
    log('hello')
 
```

*推荐*

```js 
  console
    .log('hello')
```

### 不允许有连续多行空行

空白行对于分离代码逻辑有帮助，但过多的空行会占据屏幕的空间，影响可读性。

*不推荐*

```js
let a = 1



let b = 2
```

*推荐*

```js
let a = 1

let b = 2
```

### 禁止使用链式赋值

链式赋值容易造成代码的可读性差

*不推荐*

```js
let a = b = c = 1
```

*推荐*

```js
let a = 1,
    b = 1,
    c = 1
```

### 变量声明

JavaScript 允许在一个声明中，声明多个变量。

> 团队约定在声明变量时，推荐分组申明变量

*不推荐*

```js
let a, b, c, d = 'constant'
```

*推荐*

```js
let a, b, c

const d = 'constant'
```

### 分号

JavaScript 在所有类 C 语言中是比较独特的，它不需要在每个语句的末尾有分号。在很多情况下，JavaScript 引擎可以确定一个分号应该在什么位置然后自动添加它（自动分号插入 (ASI)）。

相关参考 ：[semi](http://eslint.org/docs/rules/semi)

#### 不要使用分号
*推荐*

```js
window.alert('hi')
```
*不推荐*

```js
window.alert('hi');
```

#### 不要使用 (, [, or ` 等作为一行的开始。在没有分号的情况下代码压缩后会导致报错，而坚持这一规范则可避免出错。

*推荐*
```js
;(function () {
  window.alert('ok')
}())
```

*不推荐*
```js
(function () {
  window.alert('ok')
}())
```

### 码块收尾要添加空格

*不推荐*

```js
if (a){
  b()
}

function a (){}

```

*推荐*

```js
if (a) {
  b()
}

function a () {}
```

### 函数括号前要加空格

当格式化一个函数，函数名或 function 关键字与左括号之间允许有空白。命名函数要求函数名和 function 关键字之间有空格，但是匿名函数要求不加空格。

*不推荐*

```js
function func(x) {
  // ...
}
```

*推荐*

```js
function func (x) {
  // ...
}
```

### 操作符前后都需要添加空格

*不推荐*

```js
let sum = 1+2
```

*推荐*

```js
let sum = 1 + 2
```

### 不要定义未使用的变量

```js
function myFunction () {
  let result = something()   // ✗ avoid
}
```

### 多行 if 语句的的括号不能省

*推荐*

```js
if (options.quiet !== true) console.log('done')

// 或者

if (options.quiet !== true) {
  console.log('done')
}

```

*不推荐*

```js
if (options.quiet !== true)
  console.log('done')
```

### 不要丢掉异常处理中err参数

*推荐*

```js
run(function (err) {
  if (err) throw err
  window.alert('done')
})
```

*不推荐*

```js
run(function (err) {
  window.alert('done')
})
```

### 用 throw 抛错时，抛出 Error 对象而不是字符串

*推荐*

```js
throw new Error('error')
```
*不推荐*

```js
throw 'error'
```

### catch 中不要对错误重新赋值

*推荐*

```js
try {
  // ...
} catch (e) {
  const newVal = 'new value' 
}
```
*不推荐*

```js
try {
  // ...
} catch (e) {
  e = 'new value'           
}
```


### 对象中定义了存值器，一定要对应的定义取值器

*推荐*

```js
let person = {
  set name (value) {
    this._name = value
  },
  get name () {        
    return this._name
  }
}
```

*不推荐*

```js
let person = {
  set name (value) {  
    this._name = value
  }
}
```

### 子类的构造器中一定要调用 super

```js
class Dog extends Mammal {
  constructor () {
    super()
  }
}
```

### 同一模块有多个导入时一次性写完

*不推荐*

```js
import { myFunc1 } from 'module'
import { myFunc2 } from 'module'
```

*推荐*

```js
import { myFunc1, myFunc2 } from 'module'

```

### 不要使用 eval()

*不推荐*

```js
eval( "var result = user." + propName )
```

*推荐*

```js
let result = user[propName]
```

### 注意隐式的 eval()

*不推荐*

```js
setTimeout("alert('Hello world')") 
```

*推荐*

```js
setTimeout(function () { alert('Hello world') }) 
```

### 不要扩展原生对象

*不推荐*

```js
Object.prototype.age = 21 
```

### 不要省去小数点前面的0

*不推荐*

```js
const discount = .5 
```

*推荐*

```js
const discount = 0.5 
```

### 禁止使用 __iterator__

*不推荐*
```js
Foo.prototype.__iterator__ = function () {}
```

### 禁止使用 Function 构造器

*不推荐*

```js
let sum = new Function('a', 'b', 'return a + b')
```

*推荐*

```js
function sum(a, b) {
  return a + b
}
```

### 禁止使用 Object 构造器

*不推荐*

```js
let config = new Object()

```

*推荐*

```js
let config = {}

```

### 禁止使用 Array 构造器

*不推荐*

```js
let arr = new Array()

```

*推荐*

```js
let arr = []

```

### 禁止使用 Symbol 构造器

*不推荐*

```js
const foo = new Symbol('foo')

```

*推荐*

```js
const foo = Symbol('foo')
```

### 禁止使用 new require

*不推荐*

```js
const myModule = new require('my-module')
```

*推荐*

```js
const AppHeader = require('app-header')
const appHeader = new AppHeader()
```

### 禁止使用原始包装器

*不推荐*

```js
const message = new String('hello')
```

*推荐*

```js
const message = 'hello'
```

### 使用 getPrototypeOf 来替代 __proto__

*不推荐*

```js
const foo = obj.__proto__ 
```

*推荐*

```js
const foo = Object.getPrototypeOf(obj)
```

### 使用 this 前请确保 super() 已调用

```js
class Dog extends Animal {
  constructor () {
    this.legs = 4     // ✗ avoid
    super()
  }
}
```

### 不要使用 undefined 来初始化变量

*不推荐*

```js
let name = undefined  
```

*推荐*

```js
// good
let name
name = 'value'

// better 
let name = 'value'
```

### 禁止使用 with

```js
with (val) {...}
```

### 对象属性换行时注意统一代码风格

*不推荐*

```js
const user = {
  name: 'Jane Doe', age: 30,
  username: 'jdoe86'           
}
```

*推荐*

```js
const user = { name: 'Jane Doe', age: 30, username: 'jdoe86' } 
 
// 或者
const user = {
  name: 'Jane Doe',
  age: 30,
  username: 'jdoe86'
}  
```

### 注释首尾留空格

*不推荐*
```js
//comment
/*comment*/ 
```

*推荐*
```js
// comment
/* comment */
```

### 检查 NaN 的正确姿势是使用 isNaN()

*推荐*
```js
if (isNaN(price)) { }
```

### yield * 中的 * 前后都要有空格

*不推荐*
```js
yield* increment()
```

*推荐*
```js
yield * increment()
```


### BOM

Unicode 字节顺序标记 (BOM) 用来指定代码单元是高字节序还是低字节序。也就是说，是高位在前还是低位在前。UTF-8 不需要 BOM 来表明字节顺序，因为单个字节并不影响字节顺序。

相信不少同学遇到过 BOM 的坑，这里不多说了，切记不要使用 windows 的记事本改代码！
