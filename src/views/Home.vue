<template>
  <div id="app">  
     <AddTodo v-on:add-todo="addTodo" />
     <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script> 
import Todos from "../components/Todos"; 
import AddTodo from '../components/add-todo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos, AddTodo
  },
   data() {
     return {
       todos: []
     }
   },
   methods: {
     deleteTodo(id) { 
       axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
       .then(() => this.todos = this.todos.filter(todo => todo.id !==id))
        .catch(err => console.log(err));

       //this.todos = this.todos.filter(todo => todo.id !=id);
     },
     addTodo(newTodo){
       const { title, completed} = newTodo; // using destructuring to pul out the data

       // make a post request
       axios.post('https://jsonplaceholder.typicode.com/todos', {
         title, 
         completed
       })
       .then(res =>  this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
       //this.todos = [...this.todos, newTodo]
     }
   },

   created() {
     // getting data from api
     axios.get('https://jsonplaceholder.typicode.com/todos?_limit=7')
     .then(res => this.todos = res.data)
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
   font-family: Arial, Helvetica, sans-serif;
   line-height: 1.4;
 }
</style>
