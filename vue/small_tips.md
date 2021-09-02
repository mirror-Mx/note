#### 为什么v-if和v-for不建议用在同一个标签？

在Vue2中，`v-for`优先级是高于`v-if`的，咱们来看例子

```js
<div v-for="item in [1, 2, 3, 4, 5, 6, 7]" v-if="item !== 3">
    {{item}}
</div>
复制代码
```

上面的写法是`v-for`和`v-if`同时存在，会先把7个元素都遍历出来，然后再一个个判断是否为3，并把3给隐藏掉，这样的坏处就是，渲染了无用的3节点，增加无用的dom操作，建议使用computed来解决这个问题：

```js
<div v-for="item in list">
    {{item}}
</div>

computed() {
    list() {
        return [1, 2, 3, 4, 5, 6, 7].filter(item => item !== 3)
    }
  }
```

#### 如何处理不需要响应式的数据（死数据）

在我们的Vue开发中，会有一些数据，从始至终都`未曾改变过`，这种`死数据`，既然`不改变`，那也就`不需要对他做响应式处理`了，不然只会做一些无用功消耗性能，比如一些写死的下拉框，写死的表格数据，这些数据量大的`死数据`，如果都进行响应式处理，那会消耗大量性能。

```js
// 方法一：将数据定义在data之外
data () {
    this.list1 = { xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx }
    this.list2 = { xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx }
    this.list3 = { xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx }
    this.list4 = { xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx }
    this.list5 = { xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx }
    return {}
 }
    
// 方法二：Object.freeze()
data () {
    return {
        list1: Object.freeze({xxxxxxxxxxxxxxxxxxxxxxxx}),
        list2: Object.freeze({xxxxxxxxxxxxxxxxxxxxxxxx}),
        list3: Object.freeze({xxxxxxxxxxxxxxxxxxxxxxxx}),
        list4: Object.freeze({xxxxxxxxxxxxxxxxxxxxxxxx}),
        list5: Object.freeze({xxxxxxxxxxxxxxxxxxxxxxxx}),
    }
 }
```

#### watch的属性及用途

当我们监听一个基本数据类型时：

```js
watch: {
    value () {
        // do something
    }
}
复制代码
```

当我们监听一个引用数据类型时：

```js
watch: {
    obj: {
       handler () { // 执行回调
           // do something
       },
       deep: true, // 是否进行深度监听
       immediate: true // 是否初始执行handler函数
    }
}
```

#### 父子组件生命周期顺序

父beforeCreate -> 父created -> 父beforeMount -> 子beforeCreate -> 子created -> 子beforeMount -> 子mounted -> 父mounted

#### 数据改变无法更新视图

**对象：**

对象新属性无法更新视图，删除属性无法更新视图，为什么？怎么办？

- 原因：`Object.defineProperty`没有对对象的新属性进行属性劫持

- 对象新属性无法更新视图：使用`Vue.$set(obj, key, value)`，组件中`this.$set(obj, key, value)`

- 删除属性无法更新视图：使用`Vue.$delete(obj, key)`，组件中`this.$delete(obj, key)`

**数组：**

直接arr[index] = xxx无法更新视图怎么办？为什么？怎么办？