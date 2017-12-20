### `for...in` 与 `for...of`

`for...in` 迭代的是对象/数组的key,【会遍历所有的可枚举属性，包括原型）<br>
**更适合遍历对象的键名，**
```javascript
Array.prototype.method = function(){
    console.log(this.length);
}
var array = [1,2,3,4,5];
for(var i in array) // 可以用hasOwnProperty方法辨别某属性是否是该对象的实例属性
{                      // if(array.hasOwnProperty(key))
    console.log(array[i]);  
}
/* 输出
1 2 3 4 5
ƒ (){
    console.log(this.length);
}*/
```
`for...of`遍历数组内的元素值
```javascript
Array.prototype.method=function(){
　　console.log(this.length);
}
var array=[1,2,4,5,6,7]
array.name="数组";
for (var value of array) {
  console.log(value);
}
// 输出 1 2 3 4 5 6 7
```

### forEach

forEach()方法对数组的**每个元素**执行一次提供的函数

```js
array.forEach(callback(currentValue, index, array){
  // do something (from MDN)
}, this);
```
【注意】:<br>
1. 返回值是 `undefined`, `forEach` 遍历的范围在第一次调用 `callback` 前就会确定。调用`forEach` 后添加到数组中的项不会被 `callback` 访问到<br>

【注意】: <br>
1. 没有办法中止或者跳出forEach循坏，除了抛出一个异常。`如果正在测试一个数组里的元素是否符合某条件，且需要返回一个布尔值`，那么使用`Array.every`或是`Array.some`、<br>
2. `find()`、 `findIndex()`可以用于真值测试的提早终止

### every
测试数组的所有元素是否都通过了指定函数的测试。(不会改变原数组)

```js
arr.every(callback[, thisArg]);
```
```js
function isBigEnough(element, index, array) {
  return (element >= 10);
}
var passed = [12, 5, 8, 130, 44].every(isBigEnough);
// passed is false
passed = [12, 54, 18, 130, 44].every(isBigEnough);
// passed is true
```

### some 
与every区别。 `some()` 方法测试数组中的某些元素是否通过由提供的函数实现的测试。
只要一个通过测试了，就返回`true` 反之返回 `false`

### find 
返回数组中满足提供的测试函数的第一个元素的`值`。否则返回 `undefined`

### findIndex
返回数组中第一个找到的元素的索引，而不是其值，否则返回`-1`

### indexOf
返回在数组中可以找到一个给定元素的第一个索引，如果不存在，则返回`-1`

### includes
用来判断一个数组是否包含一个指定的值，如果是，酌情返回 true或 false。






### 【参考】
[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array)
