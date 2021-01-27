<template>
    <div>
        <form @submit="addTodoFunction">
            <input type="text" v-model="title" name="title" placeholder="Add your Todo here :-)">
            <input type="submit" value="Add +" class="btn">
        </form>
    </div>    
</template>
<script>
import {v4 as uuidv4} from 'uuid';
export default {
    name:"AddToDo",
    data(){
        return {
            title:''
        }
    },
    methods:{
        addTodoFunction(e){
            //The Event interface's preventDefault() method tells the user agent 
            //that if the event does not get explicitly handled, its default action 
            //should not be taken as it normally would be. 
            e.preventDefault();
            const newTodo ={
                id: uuidv4(),
                title: this.title,
                completed:false
            }
            //Sending up to parent through event
            //Generally, you use $emit() to notify the parent component that something changed. 
            this.$emit('add-todo', newTodo);

            //clearing:
            this.title='';
        }
    }
}
</script>
<style scoped>
    form {
        display:flex;
    }
    input[type="text"]{
        flex: 10;
        padding:5px
    }
    input[type="submit"]{
        flex:2;
    }
</style>
