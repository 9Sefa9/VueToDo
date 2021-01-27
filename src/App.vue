<!-- Main App Component-->
<template>
<div id="app">
  <Header />
  <AddTodo v-on:add-todo="addTodo"/>
  <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
</div>
</template>

<script>
import Todos from './components/Todos';
import Header from './components/layout/Header';
import AddTodo from './components/AddTodo';
export default {
  name: 'App',
  components: {
      Todos,
      Header,
      AddTodo
  },
  data(){ 
    return {
      todos:[]
    }
  },
  methods:{
    deleteTodo(id){
      console.log(id);
      //Filterin the ID.
      this.todos = this.todos.filter(todo=> todo.id !== id);
    },
    addTodo(newTodo){
      this.todos = [...this.todos, newTodo];
    }
  },
  //created() is a special function . Equivalent to React's ComponentDidMount() function
  created(){
    let fetchedData = async () => {
        let prms = await fetch("https://jsonplaceholder.typicode.com/todos?_limit=5");
        let res = await prms.json();
        this.todos = res;
    };
    fetchedData();
 
  // (async ()=>{console.log(await fetchedData())})();
    
    //fetch("https://jsonplaceholder.typicode.com/todos").then(func=>func.json()).then(jsonData => console.log(jsonData));
  
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

.btn{
  display: inline-block;
  border:none;
  background: rgb(156, 255, 90);
  color: rgb(255, 255, 255);
  padding: 10px 20px;
  cursor:pointer;
}
.btn:hover{
  background: linear-gradient(#e66465, #9198e5);
}
</style>
