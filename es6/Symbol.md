## Symbol 数据类型
1. es6引入了一种新的原始数据类型Symbol,表示独一无二的值。
2. Symbol值通过Symbol()函数生成。
3. Symbol值不与其他类型的值进行计算，会报错。
```ecmascript 6
const sy1 = Symbol('foo');
const sy2 = Symbol('foo');
sy1 === sy2 // false
sy1.description // 'foo'
```
4. Symbol.for() 方法可以接受一个字符串作为参数，搜索全局环境看有没有以该参数为名称的Symbol值，如果有就返回这个Symbol值，没有就新建一个以该字符串为名称的Symbol值。
```ecmascript 6
const s1 = Symbol.for('foo');
const s2 = Symbol.for('foo');
s1 === s2; // true
```
Symbol.for() 生成的值会被登记到全局环境中供搜索，Symbol()生成的值则不会。  
5. Symbol.keyFor() 返回一个已登记的Symbol类型值的key。
```ecmascript 6
const s1 = Symbol.for('foo');
Symbol.keyFor(s1); // 'foo'
```