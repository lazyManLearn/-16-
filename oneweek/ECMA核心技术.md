## 变量提升
* 函数提升的等级比变量高
```
  alert(a); // 输出函数a
  function a () {}
  var a = 5;
  alert(a); // 5
  a(); // 报错
```
* this 的指向问题，箭头函数声明事this已经确定
```
  this.a = 20;
  var test = {
  a: 40,
  init: function() {
    console.log(this.a); // 40
    function go() {
        'use strict'; // 严格模式下this => undefined
        console.log(this.a);
    }
    // go(); // 严格模式下报错
    return go;
  }
  }
  test.init();
  // result = test.init();
  // result(); //非严格模式输出20，严格模式报错
```
* 表达式对函数有保护作用
```
    {
     function yideng(){
         yideng = 1;
         return yideng;
     }
     yideng();
     console.log(typeof yideng); // number
    }
    console.log(typeof yideng); // function
```