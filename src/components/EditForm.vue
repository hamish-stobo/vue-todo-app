<template>
<div>
    <form class="edit-form" @submit.prevent="sendEditRequest">
        <textarea class="text-area" name="title" v-model="titleHere" />
        <button class="submit-btn">Submit</button>
    </form>
</div>
</template>

<script>
    export default {
        name: 'EditForm',
        props: ['title'],
        data() {
            return {
                titleHere: this.title
            }
        },
        methods: {
            sendEditRequest() {
                console.log('edit form, ', this.titleHere)
                this.$emit('sendEditReq', this.titleHere)
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