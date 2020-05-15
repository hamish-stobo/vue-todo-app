<template >
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title">
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
            addTodo(e) {
                e.preventDefault()
                const item = {
                    id: uuidv4(),
                    title: this.title,
                    completed: false
                }
                return item
            }
        }
    }
</script>

<style scoped>

</style>