<template>
  <div>
    <Header />
    <AddTodo v-on:addTodo="addTodo"/>
    <Todos v-bind:todos='todos' 
    v-on:deleteTodoItem="deleteTodoItem"/>
  </div>
</template>

<script>
import Header from './components/layout/Header'
import AddTodo from './components/AddTodo'
import Todos from './components/Todos'
export default {
    name: 'app',
    components: {
      Header,
      AddTodo,
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
      },
      addTodo(item) {
        this.todos = [...this.todos, item]
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

.submit-btn {
  display: inline-block;
  background: rgb(44, 44, 44);
  color: white;
  border: none;
}

.submit-btn:hover {
  background: rgb(75, 75, 75);
}
</style>
