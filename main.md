# 语言基础

## 加法操作符

+ 如果有任一方是对象，则调用其```[Symbol.toPrimitive]```方法取得表示它的数值，如果对象没有 ```[Symbol.toPrimitive]```方法，则调用其```valueOf()```方法，如果对象没有 ```valueOf```方法，则调用其```toString()```方法获取字符串。

```js
class Fo{
     [Symbol.toPrimitive](){
         return 'toPrimitive'
     }
     valueOf(){
         return 'valueOf'
     }
     toString(){
         return 'toString'
     }
}
let fo = new Fo()
console.log(3 + fo)
```



## 减法操作符

+ 如果有任一方是对象，则调用其```[Symbol.toPrimitive]```方法取得表示它的数值，如果对象没有 ```[Symbol.toPrimitive]```方法，则调用其```valueOf()```方法，如果对象没有 ```valueOf```方法，则调用其```toString()```方法获取字符串，然后把字符串使用```Number()```转化为树枝进行计算。

```js
class Fo{
     [Symbol.toPrimitive](){
         return '3'
     }
     valueOf(){
         return '2'
     }
     toString(){
         return '1'
     }
}
let fo = new Fo()
console.log(3 - fo)

```



## 关系操作符

+ 如果两方都是字符串，则逐个比较字符串中对应字符的编码

```js
'23' < '3' //true，因为'2'的ASCII码小于'3'的ASCII码
```



## 变量声明

### 使用```var```声明变量

+ 在使用```var```声明变量时，变量会被自动添加到最近的上下文中，如果变量未经声明就初始化了，则变量会自动添加到全局上下文中

```js
function fn(a, b){
	var sum = a + b
	return sum
}
let result = fn(1, 2)
console.log(sum) //报错：sum 在这里不是有效变量
```

```js
function fn(a, b){
	sum = a + b
	return sum
}
let result = fn(1, 2)
console.log(sum) //3
```



# 基本引用类型

## String

+ 字符串编码可以参考[关于编码的那些事——前端应该了解的字符编码](https://mp.weixin.qq.com/s/Zh1jp_YvRr0RAE1fm4XbJw)
+ EcmaScript提供了3个从字符串中提取子字符串的方法，分别为```slice()```、```substr()```和```substring()```，这3种方法都接受2个参数，第一个参数表示子字符串开始的位置，对于```slice()```和```substring()```而言，第二个参数表示子字符串结束的位置（即该位置之前的字符串都会被提取出来），对于```substr()```而言，第二个参数表示子字符串的长度。任何情况下，省略第二个参数意味着提取到字符串末尾。如果传入的参数为负数，则```slice()```会把负数加上字符串长度变为正数，```substring()```会把负数变为0，而```substr()```的第一个负参数会加上字符串长度变为正数，第二个负参数变为0。特别的，```substring(a, b)```在a大于b的情况下等价于```substring(b, a)```。

```js
let str = 'Hello world'
console.log(str.slice(3)) // 'lo world'
console.log(str.substr(3)) // 'lo world'
console.log(str.substring(3)) // 'lo world'
console.log(str.slice(3, 7)) // 'lo w'
console.log(str.substr(3, 7)) // 'lo worl'
console.log(str.substring(3, 7)) // 'lo w'
console.log(str.slice(-3)) // 'rld'
console.log(str.substr(-3)) // 'rld'
console.log(str.substring(-3)) // 'Hello world'
console.log(str.slice(3, -4)) // 'lo w'
console.log(str.substr(3, -4)) // ''
console.log(str.substring(3, -4)) // 'Hel' 等价于 str.substring(0, 3)
```





