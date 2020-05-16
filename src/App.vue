<template>
  <div>
    <Header />
    <AddTodo v-on:addTodo="addTodo"/>
    <Todos 
      v-bind:todos='todos' 
      v-on:sendEditRequest="sendEditRequest"
      v-on:deleteTodoItem="deleteTodoItem"
    />
  </div>
</template>

<script>
import Header from './components/layout/Header'
import AddTodo from './components/AddTodo'
import Todos from './components/Todos'
import axios from 'axios'
export default {
    name: 'app',
    components: {
      Header,
      AddTodo,
      Todos
    },
    data() {
      return {
        todos: []
    }
    },
    methods: {
      async sendEditRequest(editedTodo) {
        const { id, title, completed } = editedTodo
        console.log(editedTodo)
        try {
        await axios.put(`https://jsonplaceholder.typicode.com/todos/${id}`, {
          id,
          title,
          completed
        })
        this.todos = this.todos.map(item => {
          if(item.id === id) 
            item = editedTodo
        })
        } catch (err) {
          alert(err.message)
        }
      },  
      async deleteTodoItem(id) {
        try {
          await axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
          this.todos = this.todos.filter(todo => todo.id !== id)
        } catch (err) {
          alert(err.message)
        }
      },
      async addTodo(item) {
        const { title, completed } = item
        try {
          const res = await axios.post('https://jsonplaceholder.typicode.com/todos', {title, completed})
          this.todos = [...this.todos, res.data]
        } catch (err) {
          alert(err.message)
        }
      }
    },
    async created() {
      try {
        const res = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
        this.todos = res.data
      } catch(err) {
        alert(err.message)
      }
    }
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
