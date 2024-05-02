# todolist

## nanoid
在电脑上安装了nanoid
在Myheader组件里使用了nanoid

## 组件间传递数据

### 注意

数据在哪，操作数据的方法就在哪

### 父传子
```
父：
传
<MyHeader :addTodo="addTodo"/>

子：
接
props:['addTodo'],
```

### 子传父
父组件定义一个函数，子组件来调用这个函数
项目里的例子是添加任务：
```
父：
定义
addTodo(todoObj) {
    this.todos.unshift(todoObj)
}
传
<MyHeader :addTodo="addTodo"/>

子：
接
props:['addTodo'],
调用
add(e){
    const todoObj = {id:nanoid(), title:e.target.value, done:false} 
    this.addTodo(todoObj)
}
```
### 爷传孙

先传给父，再由父会给子


## 勾选框的问题

vue只能监测数据的浅层变化，例如：
原数据：let obj = {a:1,b:2}
只能监测到 obj = {a:100,b:200} 这种整个对象改变了（obj地址改变了）
不能监测到 obj = {a:2,b:2} 这种内属性地址改变

**所以要更改勾选框属性值时不能用v-model，虽然没有报错，看着功能正常,但是违反了原则，因为修改了props，props是只读属性**