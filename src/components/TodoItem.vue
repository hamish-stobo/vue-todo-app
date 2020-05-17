<template>
    <div class="flex-wrapper">
        <p v-if="todo.id !== editBtnId" class="list-item" v-bind:class="{'is-complete':todo.completed}">
            <input type="checkbox" v-bind:checked="todo.completed" v-on:change="markComplete"/>
            {{todo.title}}
        </p>
        <div class="edit-form-wrapper" v-else>
            <EditForm v-bind:title="todo.title" v-on:sendEditReq="passUpEditedObj" />
        </div>
        <button class="edit-btn" @click="displayEditForm(todo.id)">Edit</button>
        <button class="del-btn" v-on:click="$emit('deleteTodoItem', todo.id)">x</button>
    </div>
</template>

<script>
import EditForm from './EditForm'
    export default {
        name: 'TodoItem',
        components: {
            EditForm
        },
        props: ['todo'],
        methods: {
            markComplete() {
                this.todo.completed = !this.todo.completed
            },
            displayEditForm(id) {
                if(!this.editBtnId || this.editBtnId !== id) {
                    this.editBtnId = id
                } else {
                    this.editBtnId = null
                }
            },
            passUpEditedObj(title) {
                const { id, completed } = this.todo
                const editedTodo = {
                    id,
                    title,
                    completed
                }
                console.log('todo item, ', editedTodo)
                this.$emit('send-edit-request', editedTodo)
                this.editBtnId = null
            }
        },
        data() {
            return {
                editBtnId: null
            }
        }
    }
</script>

<style scoped>
    .flex-wrapper {
        display: flex;
        flex-flow: row nowrap;
    }

    .edit-form-wrapper {
        flex: 10;
    }

    .list-item {
        padding: 10px 0 10px 10px;
        background: rgba(112, 112, 112, 0.808);
        border-radius: 10px;
        flex: 10;
    }

    .is-complete {
        text-decoration: line-through;
    }

    .edit-btn {
        background: rgba(58, 201, 101, 0.863);
        border: none;
        border-radius: 10px;
        color: white;
        width: 60px;
        height: 42px;
    }
    .edit-btn:hover {
        cursor: pointer;
        background: rgba(26, 168, 69, 0.863);
    }
    
    .del-btn {
        border-radius: 10px;
        color: white;
        background: rgba(209, 10, 10, 0.671);
        border: 0;
        font-weight: bold;
        font-size: 1.05rem;
        padding: 4px 9px;
        width: 40px;
        height: 42px;
    }

    .del-btn:hover {
        background:rgba(153, 23, 23, 0.726);
        cursor: pointer;
    }
</style>