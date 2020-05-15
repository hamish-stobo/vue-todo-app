<template>
  <div>
    <Header />
    <Todos v-bind:todos='todos' 
    v-on:deleteTodoItem="deleteTodoItem"/>
  </div>
</template>

<script>
import Header from './components/layout/Header'
import Todos from './components/Todos'
export default {
    name: 'app',
    components: {
      Header,
      Todos
    },
    data() {
      return {
        todos: [
        {
          id: 1,
          title: 'Mop the floor',
          completed: false
        },
        {
          id: 2,
          title: 'Dust the living room',
          completed: true,
        },
        {
          id: 3,
          title: 'Wash the cat',
          completed: false
        }
      ]
    }
    },
    methods: {
      deleteTodoItem(id) {
        this.todos = this.todos.filter(todo => todo.id !== id)
      }
    },
  }
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, Helvetic, sans-serif;
  line-height: 1.4;
  width: 100%;
  padding: 0 10px;
}
</style>
