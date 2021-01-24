<!-- Main App Component-->
<template>
<div id="app">
  <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
</div>
</template>

<script>
import Todos from './components/Todos';

export default {
  name: 'App',
  components: {
      Todos
  },
  data(){ 
    return {
      todos:[
        {
          id:1,
          title:"first ToDo",
          completed:true
        },
         {
          id:2,
          title:"second ToDo",
          completed:false
        },
        {
          id:3,
          title:"third ToDo",
          completed:false
        },
      ]
    }
  },
  methods:{
    deleteTodo(id){
      console.log(id);
      //Filterin the ID.
      this.todos = this.todos.filter(todo=> todo.id !== id);
    }
  }
}
</script>

<style>
*{
  box-sizing:border-box;
  margin:0;
  padding:0;  
}
body{
  font-family: Arial, Helvetica, sans-serif;
  color: rgb(46, 45, 45);
  line-height:1.4;
}
</style>
