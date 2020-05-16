<template>
    <div>
        <div class="todolist" v-bind:key="todo.title" v-for="todo in todos">
            <TodoItem v-bind:todo="todo" v-on:send-edit-request="passUpEditObj" v-on:deleteTodoItem="$emit('deleteTodoItem', todo.id)"/>
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
        props: ["todos"],
        methods: {
            passUpEditObj(obj) {
                this.$emit('send-edit-request', obj)
            }
        }
    }
</script>

<style scoped>
    .todolist {
        color: white;
        margin: 5px auto;
        font-family: 'Courier New', Courier, monospace;
        max-width: 80%;
    }
</style>