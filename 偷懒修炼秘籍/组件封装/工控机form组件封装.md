#### 需求梳理

充分贯彻偷懒的思想，实现工控机中form组件封装，减少后续调整样式所花费的时间，以及后续写代码花费的时间

**类型**

- 布局方式：横   纵
- 操作方式：点击  展开  下拉
- 图标： 无  文字图标 图标
- 按钮方式： 无   按钮列表  切换按钮

**组件：**@/components/ipc/form-components/form-list

**配置：** setting

id: 取绑定的name，会关联到key中，不能重复

label：label名

placeholder：当value没有值的时候，默认显示placeholder

type：块的类型  取值：['block'，'select']

selectType：下拉选项类型  当type值为'select'时有效 取值：['date']  没有值时默认时下拉列表

selectList：下拉列表中的值，数组形式

value：值

flexDirection：布局方式，横向row、纵向column，取值：['column','row']

btn：按钮列表，数组