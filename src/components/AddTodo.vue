<template >
    <div class="add-todo-wrapper">
        <form @submit.prevent="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add a new todo item">
            <input type="submit" class="submit-btn">
        </form>
    </div>
</template>

<script>
import {v4 as uuidv4} from 'uuid'
    export default {
        name: 'AddTodo',
        data() {
            return {
                title: ''
            }
        },
        methods: {
            addTodo() {
                const item = {
                    id: uuidv4(),
                    title: this.title,
                    completed: false
                }
                this.$emit('addTodo', item)
                this.title = ''
            }
        }
    }
</script>

<style scoped>

    .add-todo-wrapper {
        max-width: 70%;
        margin: 0 auto;
    }

    form {
        display: flex;
        height: 3rem;
    }

    input[type="text"] {
        flex: 10;
    }

    input[type="submit"] {
        flex: 2;
    }
</style>