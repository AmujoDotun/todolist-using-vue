<template>
  <div id="app">
    <Header />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>

import Header from './components/layouts/Header';
import Todos from './components/Todos';
export default {
  name: 'App',
  components: {
    Header,
    Todos
  },
  data(){
    return{
      todos:[
        {
          id: 1,
          title: "Todo one",
          completed: true
        },
        {
          id: 2,
          title: "Todo Two",
          completed: false
        },
        {
          id: 3,
          title: "Todo Three",
          completed: true
        }
      ]
    }
  },
  methods:{
    deleteTodo(id){
        this.todos = this.todos.filter(todo => todo.id !== id)
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
  margin-top: 60px;
}
</style>
