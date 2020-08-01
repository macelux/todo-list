<template>
    <div>
       <div v-bind:key="todo.id" v-for="todo in todos">
          <TodoList v-bind:todo = "todo"/>
       </div>
    </div>
</template>

<script>
import TodoList from './TodoList';

export default {
    name: "Todos",
    props: ["todos"],
    components: {
        TodoList
    }
}
</script>

<style scoped>

</style>

