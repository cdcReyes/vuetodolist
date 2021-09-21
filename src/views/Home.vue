<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo 
  },
  data() {
    return{
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
        axios.delete(`http://127.0.0.1:9000/todos/todolist/${id}`)

          .then(this.todos = this.todos.filter(todo => todo.id!== id))
          .catch(err => console.log(err))

      this.todos = this.todos.filter(todo => todo.id!== id);
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios.post('http://127.0.0.1:9000/todos/todolist/', {
        title,
        completed
      })
        .then( res => console.log(res.data.objects))
        .catch(err => console.log(err));

      this.todos = [...this.todos, newTodo];
    }
  },
  created() {
    axios
      .get('http://127.0.0.1:9000/todos/todolist/')
      .then(res => console.log(res.data.objects))
      .catch(err => console.log(err));
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
    font-family: Arial, Arial, Helvetica, sans-serif;
    line-height: 1.4;
    background-image: url('~@/assets/Untitledbg.svg');
    background-attachment: fixed;
    background-size: cover ;
  }

  .btn {
    display: inline-block;
    border: none;
    background: rgb(59, 66, 99);
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
    margin-left: 5em;
  }

  .btn:hover {
    background: #666;
  }
</style>
