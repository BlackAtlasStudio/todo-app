<template>
  <div class="main">
    <div class="info">
      <p>Complete Tasks: {{ todos.filter(todo => {return todo.done == true}).length }}</p>
      <p>Incomplete Tasks: {{ todos.filter(todo => {return todo.done == false}).length }}</p>
    </div>
    <todo v-for="(todo, index) in todos" v-bind:todo="todo" v-bind:key="index" v-on:complete-todo="completeTodo(todo)"></todo>
  </div>
</template>

<script type="text/javascript">
  import Todo from './Todo'

  export default {
    props: ['todos'],
    components: {
      Todo
    },
    methods: {
      completeTodo (todo) {
        const todoIndex = this.todos.indexOf(todo)
        this.todos[todoIndex].done = true
      }
    }
  }
</script>

<style scoped>
  .main {
    max-width: 60%;
    position: relative;
    left: 20%;
  }

  @media(max-width: 600px) {
    .main {
      max-width: 100%;
      left: 0%;
    }
  }
</style>
