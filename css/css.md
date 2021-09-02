## 样式小tips

#### 1.css让文字平均铺满容器

效果：

![img](https://img-blog.csdnimg.cn/20200825143204373.png)

代码：

```html
div class="label">账号</div>
```

```css
.label {
  width: 60px;
  height: 31px;
  line-height: 31px;
  padding-right: 10px;
  text-align: justify;
}
 
.label::after {
  display: inline-block;
  width: 100%;
  content: "";
}
```

#### 2.文字超出是否换行样式总结

##### tips1:自动换行的处理方法`work-break`

- 语法【normal|break-all|keep-all】

  - normal   使用浏览器默认的换行规则。

  ```html
  <div>
      哗哗哗哗哗哗啦啦啦啦啦啦啦啦的的小雨滴，哒哒哒！嘟嘟嘟
      People may wonder why different words are used to describe these four countries: England, Wales, Scotland and Northern Ireland.
  </div>
  ```

  ```css
  <style>
      div {
          background-color: #f5f5f5;
          color: #353535;
          width: 100px;
          word-break: normal;
      }
  </style>
  ```

  ![image-20210421133749190](C:\Users\62624\AppData\Roaming\Typora\typora-user-images\image-20210421133749190.png)

  - break-all  允许在单词内换行

    ![image-20210421133711417](C:\Users\62624\AppData\Roaming\Typora\typora-user-images\image-20210421133711417.png)

  - keep-all 只能在半角空格或连字符处换行

  ![image-20210421133845565](C:\Users\62624\AppData\Roaming\Typora\typora-user-images\image-20210421133845565.png)

##### case1.文字超出部分显示“...”

有的时候出现只有内容超出隐藏效果，但是还没有超出...的效果，加上下面代码都可解决

display:block/inline-block/inline

1. 单行文本

```css
white-space: nowrap;
text-overflow:ellipsis; 
overflow: hidden; 

white-space: nowrap;    /*强制在一行显示*/
text-overflow:ellipsis; /*设置超出内容显示...*/
overflow: hidden;       /*一定不能少 超出的内容进行隐藏*/
```

2. 多行文本

```css
overflow: hidden;
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 2; 
```

## 伪类选择器

