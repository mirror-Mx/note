#### 问题：在edge浏览器下，在输入框中输入/会出现浏览器开始键入弹框

![image-20211012132716794](C:\Users\62624\AppData\Roaming\Typora\typora-user-images\image-20211012132716794.png)

解决思路：

1.增加输入框属性或样式关闭输入框该事件

2.全局输入框加入该方法关闭所有输入框该事件

3.由于只有edge浏览器中有该问题，仅在浏览器是edge浏览器时，增加判断

代码：

在项目初始化，`app.vue`中加入

```vue
mounted() {
    this.focusListener()
},
methods: {
    // 监听获取焦点事件
    focusListener() {
      var ua = window.navigator.userAgent
      if (ua.indexOf('Edg/') > 0) {
        window.addEventListener('focus', function(e) {
          e = e || window.event
          if (e.target.nodeName === 'INPUT') {
            e.target.setAttribute('aria-autocomplete', 'both')
          }
        }, true)
      }
    }
}
```

