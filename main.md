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
'23' < '3' //true
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

