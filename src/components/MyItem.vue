<template>
  <li>
      <label>                                     
        <input type="checkbox" :checked="todo.done" @change="handleCheck(todo.id)"/>
        <span>{{todo.title}}</span>
      </label>
      <button class="btn btn-danger" @click="handleDelete(todo.id)">删除</button>
    </li>
</template>

<script>
  export default {
    name:"MyItem",
    //声明接收todo对象
    props:['todo','checkTodo','deleteTodo'],
    methods: {
      handleCheck(id){
        //通知App组件将对应的todo对象的done值取反
        this.checkTodo(id)
      },
      handleDelete(id){
        if(confirm('确定删除吗')){
          //
          this.deleteTodo(id)
        }
      }
    }

  }
</script>

<style scoped>
  /*item*/
  li {
      list-style: none;
      height: 36px;
      line-height: 36px;
      padding: 0 5px;
      border-bottom: 1px solid #ddd;
    }

    li label {
      float: left;
      cursor: pointer;
    }

    li label li input {
      vertical-align: middle;
      margin-right: 6px;
      position: relative;
      top: -1px;
    }

    li button {
      float: right;
      display: none;
      margin-top: 3px;
    }

    li:before {
      content: initial;
    }

    li:last-child {
      border-bottom: none;
    }

    /* 鼠标悬浮高亮 */
    li:hover {
      background-color: #ddd;
    }

    /* 鼠标悬浮时显示删除按钮 */
    li:hover button{
      display: block;
    }
</style>
