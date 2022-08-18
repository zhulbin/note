# Array

## 1、数组的API

### 1.1、静态方法



#### 1.1.1、Array.of()

​		主要用于创建数组，内部依次参数表示返回数组的元素

#### 1.1.2、Array.from()

​		用于将一个类似数组(Object(内部必须存在length属性)，Arguments，...)或者可迭代对象(String，Map，Set，...)转化为一个数组，当内部第一个参数为数组时，即表示浅拷贝一个数组

#### 1.1.3、Array.isArray()

​		用于判断数组，返回一个boolean值



扩展 

创建数组的方法：

```js
// 1、使用构造函数创建
// Array === new Array
let arr = new Array()  // => [];
let arr1 = new Array(3) // => [, , ,] / [<3 empty items>]
let arr2 = new Array('3') // => ['3']
// 2、使用Array.of()创建
let arr3 = Array.of(3) // => [3]
let arr4 = Array.of(1,2,3) // => [1, 2, 3]
// 3、直接声明一个数组
let arr5 = [1, 2, 3] // => [1, 2, 3]
```



Array.from()：

Array.from 第一个参数接收类似数组、可迭代对象、数组，所谓的类似数组表示其内部属性必须存在length，可看作隐式转换为Array.prototype.length的值，同时 Array.from 可以看作 [].slice.call

```js
Array.from({length: 3}) // => [undefined, undefined, undefined]
Array.from({0: 'a', 1: 'b', 2: 'c', length: 3}) // => ['a', 'b', 'c']
```

Array.from 第二个参数表示通过第一个参数生成的新数组中的每一个元素都会执行该回调函数

```js
Array.from({length: 3}, (item, index) => index) // => [0, 1, 2]
```



判断数组：

判断数组的方法有：Array.isArray()，constructor，instanceof，Object.prototype.toString.call()

```js
let arr = [1, 2, 3];
Array.isArray(arr) // true
arr.constructor === Array // true
arr.instanceof Array // true
Object.prototype.toString.call(arr) === '[object Array]' // true
```



### 1.2、实例方法

#### 1.2.1、改变原数组的方法



##### 1.2.1.1、Array.prototype.splice()

​		通过添加/删除/替换元素修改数组，并返回这个数组

##### 1.2.1.2、Array.prototype.sort()

​		通过对数组元素的比较进行排序，并返回这个数组。

​		在没有参数时，默认按照字母排序，如果不是字符串时，会调用toString方法，将元素转化为字符串的Unicode位点，再进行比较。

​		在传入比较函数参数时，函数内部有两个参数a和b，通过比较a和b的大小进行排序：

```
a - b :
> 0 , a在前b在后
< 0 , b在前a在后
= 0 , 位置不变
sort内部传入参数为(a, b) => a - b 表示升序;
	内部传入参数为(a, b) => b - a 表示降序
```



##### 1.2.1.3、Array.prototype.pop()

​		删除数组末尾一个元素，并返回这个数组

##### 1.2.1.4、Array.prototype.push()

​		在数组末尾添加一个或多个元素，并返回这个数组

##### 1.2.1.5、Array.prototype.shift()

​		删除数组第一个元素，并返回这个数组

##### 1.2.1.6、Array.prototype.unshift()

​		在数组头部添加一个或多个元素，并返回这个数组

##### 1.2.1.7、Array.prototype.reverse()

​		反转数组元素，并返回这个数组

##### 1.2.1.8、Array.prototype.copyWithin()

​		ES6新增api，将指定数组元素复制到指定位置覆盖原数组元素，并返回这个数组

​		注：第二个参数和第三个参数可看作左闭右开

##### 1.2.1.9、Array.prototype.fill()

​		ES6新增api，填充数组

​		注：第二个参数和第三个参数可看作左闭右开



#### 1.2.2、不改变原数组的方法



##### 1.2.2.1、Array.prototype.slice()

​		浅拷贝指定长度的数组

​		注：第一个参数和第二个参数可看作左闭右开

##### 1.2.2.2、Array.prototype.join()

​		将一个数组/类数组对象的所有的元素通过传入的参数连接成一个字符串，不传入参数时使用"**,**"将其分隔

##### 1.2.2.3、Array.prototype.toString()

​		将数组元素转换成字符串

##### 1.2.2.4、Array.prototype.toLocaleString()

​		将数组元素转换成字符串，而转换过程中会将数组中的元素使用各自的toLocaleString() 转换成对应的字符串

##### 1.2.2.5、Array.prototype.indexOf()

​		通过传入元素值来找到数组对应第一个元素值的索引值，未找到则返回-1。第二个参数表示从数组元素的第几个元素开始寻找

##### 1.2.2.6、Array.prototype.lastIndexOf()

​		通过传入元素值从数组末尾开始找到数组相对应第一个元素值的索引值，未找到则返回-1。第二个参数表示从数组末尾第几个元素开始找

##### 1.2.2.7、Array.prototype.concat()

​		合并两个或多个数组，返回一个新的数组

##### 1.2.2.8、Array.prototype.includes()

​		ES7新增api，通过传入元素值来判断数组中是否包含该元素，返回一个boolean值，第二个参数表示从数组第几个元素开始寻找

​		它能够寻找NaN元素，能够弥补indexOf()不能查找NaN的缺陷。

##### 1.2.2.9、Array.prototype.flat()

​		ES6新增api，该方法会按照一个可指定的深度递归遍历数组，并将所有元素与遍历到的子数组中的元素合并为一个新数组返回

##### 1.2.2.10、Array.prototype.flatMap()

​		ES6新增api，该方法首先使用映射函数映射每个元素，然后将结果压缩成一个新数组。可以将其看作是map和深度为1的flat的结合体。

#### 1.2.3、数组遍历的方法

以下api遵循规则：

- 空数组不执行回调函数
- 当遇到空元素时，会跳过此次回调函数
- 遍历的次数在第一次进入循环时就会确认，再添加进入数组的元素不再参与遍历

##### 1.2.3.1、Array.prototype.forEach()

​		遍历一个数组，通过第一个参数对数组元素进行处理

​		注：forEach除了抛出异常外，没有办法中止或者跳出循环，只能return本次回调，再进行下一次回调。同时forEach总是返回undefined值。

##### 1.2.3.2、Array.prototype.map()

​		遍历一个数组，通过第一个参数对数组元素进行处理，需要return，返回一个新的数组

##### 1.2.3.3、Array.prototype.every()

​		检测数组中每一个元素是否满足回调函数中的条件，返回一个boolean值

​		注：当检测到数组有一个元素不满足条件，则不会再检测

##### 1.2.3.4、Array.prototype.some()

​		检测数组是否有满足判断条件的元素，返回一个boolean值

​		注：当检测到数组有一个元素满足条件，则不会再检测

##### 1.2.3.5、Array.prototype.filter()

​		检测数组通过条件的所有元素并返回这些元素组成一个新数组。

##### 1.2.3.6、Array.prototype.reduce()

​		数组每一个元素（从左至右）依次执行提供的reducer函数，每一次运行reducer函数都会将上一次的计算结果传入，最后将其汇总返回单个返回值，如果没有提供初始值则以数组的第一个元素和第二个元素传入reducer函数，提供初始值，则是初始值和第一个元素传入reducer函数。

reduce的高阶用法：https://juejin.cn/post/6844904063729926152#heading-20

##### 1.2.3.7、Array.prototype.reduceRight()

​		数组每一个元素（从右至左）依次执行提供的reducer函数，每一次运行reducer函数都会将上一次的计算结果传入，最后将其汇总返回单个返回值，如果没有提供初始值则以数组的数组倒数第一个元素和倒数第二个元素传入reducer函数，提供初始值，则是初始值和倒数第一个元素传入reducer函数。		

##### 1.2.3.8、Array.prototype.find()

​		ES6新增api，用于找到第一个符合条件的数组成员（从左至右），并返回该元素，如果没有数组满足条件的元素，则返回undefined

##### 1.2.3.9、Array.prototype.findIndex()

​		ES6新增api，用于找到第一个符合条件的数组成员（从左至右），并返回该元素的相应位置，如果没有数组满足条件的元素，则返回-1

##### 1.2.3.10、Array.prototype.findLast()

​		ES2022新增api，用于找到第一个符合条件的数组成员（从右至左），并返回该元素，如果没有数组满足条件的元素，则返回undefined

##### 1.2.3.11、Array.prototype.findLastIndex()

​		ES2022新增api，用于找到第一个符合条件的数组成员（从右至左），并返回该元素的相应位置，如果没有数组满足条件的元素，则返回-1

##### 1.2.3.12、Array.prototype.keys()

​		该方法返回一个新的Array Iterator对象，该对象包含数组中每个索引的键名，可使用for...of对其遍历

##### 1.2.3.13、Array.prototype.values()

​		该方法返回一个新的Array Iterator对象，该对象包含数组中每个索引的键值，可使用for...of对其遍历

##### 1.2.3.14、Array.prototype.entries()

​		该方法返回一个新的Array Iterator对象，该对象包含数组中每个索引的键-值对，可使用for...of对其遍历



扩展：

扩展运算符(...)结合数组使用

（1）数组的浅拷贝

```js
let arr = [1, 2, 3]
let newArr = [...arr];
```

（2）合并数组取代Array.prototype.concat()

```js
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];
let newArr = [...arr1, ...arr2] // => [1, 2, 3, 4, 5, 6]
```

（3）用于数组的解构

```js
let arr = [{name: 'yumc'}, 1, 2, 3, 4];
// 注意扩展运算符必须放在解构最后一位
const [obj, ...rest] = arr;
console.log(obj, rest) // => {name: 'yumc'} [1, 2, 3, 4]
```

（4）用于求数组的最大值

```js
let arr = [3, 7, 5, 10, 25, 1, 82, 9];
console.log(Math.max(...arr)) // => 82
```

（5）结合Set对数组去重

```js
let arr = [1, 2, 4, 4, 7, 1, 6, 3, 10]
let newArr = [...new Set(arr)] // => [1, 2, 4, 7, 6, 3, 10]
```



使用reduce求数组的最大值

```js
let arr = [3, 7, 5, 10, 25, 1, 82, 9];
arr.reduce((v, i) => v > i ? v : i); // => 82
// 同样使用reduceRight也可以用来取数组最大值
arr.reduceRight((v, i) => v > i ? v : i); // => 82
```



使用for...in for...of遍历数组

```js
let arr = [1, 2, 3]
for(let value of arr) {
	console.log(value)
}
for(let index in arr) {
	console.log(index, typeof index)
}
// 1
// 2
// 3
// 0 string
// 1 string
// 2 string
```

可以看出 for...of 遍历数组拿到数组的键值(value)，而for...in遍历数组拿到的是数组的键名(下标)，但是得注意的是这个值是string类型。



数组/对象的深拷贝

```js
function deepClone(target) {
	let map = new Map()
    function clone(data) {
        if(map.has(data)) return map.get(data)
        let result = Array.isArray(data) ? [] : {}
        map.set(data, result)
        for(let item in data) {
            let res = data[item]
            if(typeof res === 'object') {
				result[item] = clone(res)
			} else {
                result[item] = res
			}
		}
        return result
	}
    return clone(target)
}
```



