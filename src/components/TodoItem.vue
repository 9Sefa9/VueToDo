<template>
<!-- we are binding a class to "{'is-complete':CONDITION}"-->
    <div class='todo-item' v-bind:class="{'is-complete':todo.completed}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
        </p>
    </div>
</template>

<script>
export default{
    name:"TodoItem",
    props: ["todo"],
    data(){
        return{
        todoMarkComplete : this.todo
        }
    },
    methods: {
        markComplete(){
        this.todoMarkComplete.completed = !this.todoMarkComplete.completed;
        }
    }
}
</script>

<style scoped>
    .todo-item{
        background:#ffb489;
        padding:10px;
        border-bottom: 1px #000000 ridge;
    }

    .is-complete {
        text-decoration:line-through;
    }
    .del {
        background: #dd0000;
        color:rgb(255, 255, 255);
        border:none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor:pointer;
        float:right;
    }
</style>