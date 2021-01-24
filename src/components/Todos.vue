<template>
    <div>
        <!-- looping in the todos props -->
        <div v-bind:key="todo.id" v-for="todo in todos">
            <!--individual "todo" item in todos will be applied in TodoItem as prop -->
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"/>
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    name:"Todos",
    components:{
        TodoItem
    },
    props:["todos"]
}
</script>

<style scoped>

</style>
