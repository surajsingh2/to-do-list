<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <AddTodo  v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import AddTodo from './components/addTodo';
import Todos from './components/todos';
import axios from 'axios';
export default {
  name: 'App',
  components: {
    Todos,
    AddTodo
  },
  created() {
    this.gettodos();
  },
  data() {
    return {
      todos:[ ]
    }
  },
  methods : {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
       .then(this.todos = this.todos.filter(todo => todo.id !== id))
       .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
       .then(res => this.todos = [...this.todos, res.data])
       .catch(err => console.log(err));
    },
    gettodos() {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
        .then(res => this.todos = res.data)
        .catch(err => console.log(err));
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}

</style>
