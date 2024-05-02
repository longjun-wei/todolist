<template>
  <div class="todo-footer" v-show="total">
    <label>
      <!-- <input type="checkbox" :checked="isAll" @change="checkAll"/> -->
      <!-- 简写 -->
      <input type="checkbox" v-model="isAll"/>
    </label>
    <span>
      <span>已完成{{ doneTotal }}</span> / 全部{{ todos.length }}
    </span>
    <button class="btn btn-danger" @click="clearAll">清除已完成任务</button>
  </div>
</template>

<script>
  export default {
    name:"MyFooter",
    props:['todos','checkAllTodo','clearAllTodo'],
    computed: {
      total(){
        return this.todos.length
      },
      // isAll(){
      //   return this.doneTotal === this.total && this.total > 0
      // }
      isAll: {
        get(){
          return this.doneTotal === this.total && this.total > 0
        },
        set(value){
          this.checkAllTodo(value)
        }
      },
      doneTotal(){
        // let i = 0
        // this.todos.forEach((todo) => {
        //   if(todo.done) i++
        // })

        // 高端写法
        /*第一次循环的pre用的是reduce方法的第二个参数0 
            第二次的pre用的是第一个方法参数的内部的返回值，如果不加return，则pre是undeifned
            current是todos数组的item
            reduce方法结束会返回琴结果*/
        //  const x = this.todos.reduce((pre, current)=>{
        //   console.log('@', pre, current) 
        //   return pre + (current.done ? 1 : 0) 
        //   //这里是先打印再返回所以控制台的结果少一行
        // }, 0)
        // return x

        //简写
        return this.todos.reduce((pre, todo) => pre + (todo.done ? 1 : 0), 0)
      }
    },
    methods: {
      // 简写了不需要
      // checkAll(e){
      //   this.checkAllTodo(e.target.checked)
      // },
      clearAll(){
        this.clearAllTodo()
      }
    }
  }
</script>

<style scoped>
  /*footer*/
  .todo-footer {
      height: 40px;
      line-height: 40px;
      padding-left: 6px;
      margin-top: 5px;
    }

    .todo-footer label {
      display: inline-block;
      margin-right: 20px;
      cursor: pointer;
    }

    .todo-footer label input {
      position: relative;
      top: -1px;
      vertical-align: middle;
      margin-right: 5px;
    }

    .todo-footer button {
      float: right;
      margin-top: 5px;
    }
</style>
