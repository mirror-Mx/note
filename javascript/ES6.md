## `Object.assign()`

assign  --    分配，指派，赋值

#### 1.基本用法

用法：`Object.assgin(目标对象，源对象1，源对象2...)`

`Object.assign`方法用于对象的合并，将原对象(`sourse`)的所有可枚举属性，复制到目标对象(target)。

```javascript
const target = { a:1 }
const sourse1 = { b:2 }
const soutse2 = { c:3 }

Object.assign(target, sourse1, sourse2)
target  // { a:1, b:2, c:3 }
```

https://www.jianshu.com/p/d5f572dd3776