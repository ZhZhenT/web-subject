# ES6、7、8...部分面试题汇总
---
### 1.箭头函数与普通函数（function）的区别是什么？构造函数（function）可以使用 new 生成实例，那么箭头函数可以吗？为什么？
   - **解析：**<br>
    1、函数体内的 this 对象，就是定义时所在的对象，而不是使用时所在的对象。<br>
    2、不可以使用 arguments 对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。<br>
    3、不可以使用 yield 命令，因此箭头函数不能用作 Generator 函数。<br>
    4、不可以使用 new 命令，因为：<br>
    没有自己的 this，无法调用 call，apply。<br>
    没有 prototype 属性 ，而 new 命令在执行时需要将构造函数的 prototype 赋值给新的对象的 `__proto__`<br>
    new 过程大致是这样的：<br>
```js
function newFunc(father, ...rest) {
    var result = {};
    result.__proto__ = father.prototype;
    var result2 = father.apply(result, rest);
    if (
        (typeof result2 === 'object' || typeof result2 === 'function') &&
        result2 !== null
    ) {
        return result2;
    }
    return result;
}
````


