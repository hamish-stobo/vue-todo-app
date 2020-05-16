<template>
<div>
    <form class="edit-form">
        <textarea class="text-area" name="title" v-model="title" />
        <button class="submit-btn">Submit</button>
    </form>
</div>
</template>

<script>
    export default {
        name: 'EditForm',
        props: ['todo'],
        data() {
            return {
                title: this.todo.title
            }
        }
    }
</script>

<style scoped>
    .edit-form {
        height: 42px;
        display: flex;
    }

    .text-area {
        height: 100%;
        min-width: 200px;
        display: inline-block;
        flex: 10;
    }

    .submit-btn {
        height: 100%;
        min-width: 60px;
        float: right;
    }
    .submit-btn:hover {
        cursor: pointer;
    }
</style>