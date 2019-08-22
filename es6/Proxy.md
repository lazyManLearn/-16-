## 概述
Proxy 用于修改某些操作的默认行为，等于在语言层面做出修改，所以属于一种元编程，即对编程语言进行编程。  
Proxy可以理解成，在目标对象之前架设一层拦截，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外层的访问进行过滤和改写。
```ecmascript 6
var obj = new Proxy({}, {
  get: function(target, key, receiver) {
    console.log(`getting ${key}`);
    return Reflect.get(target, key, receiver)
  },
  set: function(target, key, value, receiver) {
    console.log(`setting ${key}`);
    return Reflact.set(target, key, value, receiver);
  }
});// 这里对一个空对象架设了拦截，重新定义了属性的读取和设置行为
obj.count = 1; // setting count
++ obj.count;
// getting count
// setting count
// 2
```