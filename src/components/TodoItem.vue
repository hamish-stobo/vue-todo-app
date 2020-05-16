<template>
    <div>
        <p class="list-item" v-bind:class="{'is-complete':todo.completed}">
            <input type="checkbox" v-bind:checked="todo.completed" v-on:change="markComplete"/>
            {{todo.title}}
            <button class="del-btn" v-on:click="$emit('deleteTodoItem', todo.id)">x</button>
        </p>
    </div>
</template>

<script>
    export default {
        name: 'TodoItem',
        props: ['todo'],
        methods: {
            markComplete() {
                this.todo.completed = !this.todo.completed
            }
        }
    }
</script>

<style scoped>
    .list-item {
        padding-right: 20px;
        vertical-align: middle;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .del-btn {
        float: right;
        border-radius: 50%;
        color: white;
        background: rgba(209, 10, 10, 0.671);
        border: 0;
        font-weight: bold;
        cursor: pointer;
        font-size: 1.05rem;
        padding: 4px 9px;
    }

    .del-btn:hover {
        background: rgba(59, 59, 59, 0.808)
    }
</style>