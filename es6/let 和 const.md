## 基本用法
1. let 和 const声明的变量只在代码块内有效。
```angular2html
{
var p = 1;
let a = 10;
const b = 20;
}
a // ReferenceError: a is not defined
p // 1
```
2. for循环的计数器使用let命令，计数器只在循环体内有效
```angular2html
var a = [];
for(let i = 0; i < 10; i++){
 a[i] = function() {console.log(i);}
}
a[6](); // 6
console.log(i); // ReferenceError: i is not defined
```
3. 不存在变量提升
```angular2html
console.log(foo); // undefined  var声明的变量会有变量提升现象，变量在声明前使用值是undefined
bar foo = 2;
console.log(bar); // ReferenceError let声明的变量在声明前使用会报错
let bar = 2; 
```
4. 暂时性死区
```angular2html
bar tpm = 233;
if(true){
tpm = 'ab'; // ReferenceError 只要块级作用域内存在let命令，它所声明的变量就绑定了这个作用域，这里提前使用报错
let tmp;
}
typeof y; // undefined y没声明，typeof 返回undefined
typeof x; // ReferenceError 暂时性死区意味着typeof不在是一个百分之百的安全操作符
let x;
```
5. 不允许重复声明
```angular2html
function func(){
 let a = 1;
 var a = 10; //报错
}
function fn(arg){
let arg; //报错，函数内部不能重新声明参数
}
```
6. 块级作用域
```angular2html
function f1() {
let n = 5;
if(true){
let n = 10;
}
console.log(n); // 5
}
```
7. 块级作用域与函数声明  
es5规定，函数只能在顶层作用域和函数作用域中声明，不能在块级作用域中声明。  
es6 引入了块级作用域，明确允许在块级作用域之中声明函数。ES6 规定，块级作用域之中，函数声明语句的行为类似于let，在块级作用域之外不可引用。附录里规定浏览器的实现可以不遵守上面的规定，有自己的行为方式。
```angular2html
function f() {console.log('outer');}
(function(){
if(false) {
function f(){console.log('inner');}
}
f(); // 报错 浏览器实现块级作用域中声明函数类似var,会提升到作用域的头部
})();
```
8. const 声明一个只读常量，本质上const 保证的是保存数据的内存地址不变。
9. es6声明变量的六种方法 es5只有两种变量声明方法：var 和 function 命令。es6添加了let、const、import、class命令。
10. 顶层对象的属性，var 和function 生命的全局变量依旧是顶层对象的属性，而用let 和 const 声明的变量不再属于顶层对象的属性。
