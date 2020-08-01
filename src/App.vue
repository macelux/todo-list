<template>
  <div id="app"> 
     <Todos v-bind:todos="todos"/>
  </div>
</template>

<script> 
import Todos from "./components/Todos";

export default {
  name: 'App',
  components: {
    Todos
  },
   data() {
     return {
       todos: [
         {
           id: 1,
           title: "Todo One",
           completed: true
         },
         {
           id: 2,
           title: "Todo two",
           completed: false
         },
         {
           id: 3,
           title: "Todo three",
           completed: false
         }
       ]
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
   font-family: Arial, Helvetica, sans-serif;
   line-height: 1.4;
 }
</style>
