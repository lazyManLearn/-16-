## Set
es6提供了新的数据结构Set,类似于数组，但是成员的值都是唯一的，没有重复的值。  
Set本身是一个构造函数，用来生成Set数据结构。
```ecmascript 6
const s = new Set();
[2,3,5,4,5,2].forEach(x => s.add(x));
for (let i of s) {
  console.log(i);
}
//2 3 5 4
```
Set函数可以接受一个数组（或者具有iterator接口的其他数据结构）作为参数来初始化。
```ecmascript 6
const set = new Set([1,2,3,4,4]);
[...set]; // [1,2,3,4]
set.size; // 4
```
Set实例的属性和方法
```ecmascript 6
const s = new Set();
s.add(1).add(2).add(2);
s.size; // 2
s.has(1); // true
s.has(3); // false
s.delete(1);
s.has(1); // false
```
Set的遍历操作keys()、values()、entries()、forEach()
```ecmascript 6
const set = new Set(['red', 'green', 'blue']);
for(let item of set.keys()) {
  console.log(item);
}
// red
// green
// blue
for (let item of set.values()) {
  console.log(item);
}
// red
// green
// blue
for (let item of set.entries()) {
  console.log(item);
}
// ['red', 'red']
// ['green', 'green']
// ['blue', 'blue']
```
## WeakSet
WeakSet结构和Set类似，也是不重合值的集合。但是WeakSet的成员只能是对象。WeakSet中对象都是弱引用，即垃圾回收机制不考虑WeakSet 对该对象的引用，也就是说，如果其他对象都不再引用该对象，那么垃圾回收机制会自动收回该对象所占用的内存，不考虑该对象还存在于WeakSet之中。
## Map
javascript的对象，本质上是键值对的集合，传统上只能字符串做键。Map数据结构的键是各种类型的值都可以。
```ecmascript 6
const m = new Map();
const o = {p: 'hi'};
m.set(o, 'content');
m.get(o); // 'content'
m.delete(o);
m.has(o); // false
const map = new Map([['name','张三'], ['title','Author']]); //接收数组做参数
map.size; // 2
map.has('name'); // true
map.get('name'); // '张三'
map.get('aaa'); // undefined
map.clear(); // 清空所有的成员
```
Map的遍历方法keys()、values()、entries()、forEach();
```ecmascript 6
const map = new Map([['f','yes'],['t','no']]);
for(let key of map.keys()) {
  console.log(key);
}
// 'f'
// 't'
for(let value of map.values()) {
  console.log(value);
}
// 'yes'
// 'no'
for (let item of map.entries()) {
  console.log(item[0],item[1]);
 
}
// 'f' 'yes'
// 't' 'no'
```
## WeakMap
WeakMap结构和Map结构类似，区别是WeakMap只接受对象作为键名（null除外），WeakMap的键名指向的对象，不计入垃圾回收机制。这种设置有助于防止内存泄露。


