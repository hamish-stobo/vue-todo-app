<template >
    <div class="add-todo-wrapper">
        <form @submit.prevent="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add a new todo item">
            <input type="submit" class="submit-btn">
        </form>
    </div>
</template>

<script>
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