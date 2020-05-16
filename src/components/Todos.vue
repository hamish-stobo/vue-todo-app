<template>
    <div>
        <div v-bind:key="todo.title" v-for="todo in todos">
            <TodoItem class="todolist" v-bind:todo="todo" v-on:deleteTodoItem="$emit('deleteTodoItem', todo.id)"/>
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem'
    export default {
        name: 'Todos',
        components: {
            TodoItem
        },
        props: ["todos"]
    }
</script>

<style scoped>
    .todolist {
        color: white;
        background: rgba(112, 112, 112, 0.808);
        margin: 5px auto;
        border-radius: 10px;
        font-family: 'Courier New', Courier, monospace;
        max-width: 70%;
    }
</style>