<template>
  <div id="app">
    <Header />
    <AddTodo />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>

import Header from './components/layouts/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
import axios from 'axios';
export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo
  },
  data(){
    return{
      todos:[]
    }
  },
  methods:{
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode/todos/${id}`)
        .then(() => this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err =>  console.log(err));

    },
    addTodo(newTodo){
      const { title, completed } = newTodo;

      axios.post('https://jsonplaceholder.typicode/todos',{
        title,
        completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));

    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode/todos')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
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
  margin-top: 60px;
}

.btn{
  display: inline-block;
  border:none;
  background: #555;
  color:#fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover{
    background: #666;
}
</style>
