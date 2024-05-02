<template>
  <ul class="todo-main">
    <MyItem 
      v-for="todoObj in todos" 
      :key="todoObj.id" 
      :todo="todoObj" 
      :checkTodo="checkTodo"
      :deleteTodo="deleteTodo"
    />
  </ul>
</template>

<script>
  import MyItem from '../components/MyItem.vue'
  export default {
    name:"MyList",
    components:{MyItem},
    props:['todos','checkTodo','deleteTodo'],
    //为了方便数据在各组件间传递，把数据放在了App组件时，然后再传回来
    // data() {
    //   return {
    //     // todos:[
    //     //   {id:'001', title:'吃饭', done:true},
    //     //   {id:'002', title:'睡觉', done:false},
    //     //   {id:'003', title:'打豆豆', done:true},
    //     //   {id:'004', title:'开车', done:true}
    //     // ]
    //   }
    // }
  }
</script>

<style scoped>
  /*main*/
  .todo-main {
    margin-left: 0px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding: 0px;
  }

  .todo-empty {
    height: 40px;
    line-height: 40px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding-left: 5px;
    margin-top: 10px;
  }
</style>
