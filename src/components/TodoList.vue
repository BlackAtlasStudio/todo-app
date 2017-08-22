<template>
  <div class="main">
    <todo-create v-on:create-todo="createTodo"></todo-create>
    <todo
      v-for="(todo, index) in todos"
      v-bind:todo="todo"
      v-bind:key="index"
      v-on:complete-todo="completeTodo(todo)"
      v-on:delete-todo="deleteTodo(todo)"></todo>
  </div>
</template>

<script type="text/javascript">
  import Todo from './Todo'
  import TodoCreate from './TodoCreate'

  export default {
    props: ['todos'],
    components: {
      Todo,
      TodoCreate
    },
    methods: {
      completeTodo (todo) {
        const todoIndex = this.todos.indexOf(todo)
        this.todos[todoIndex].done = true
      },
      deleteTodo (todo) {
        const todoIndex = this.todos.indexOf(todo)
        this.todos.splice(todoIndex, 1)
      },
      createTodo (todo) {
        console.log('Creating Todo')
        this.todos.unshift(todo)
      }
    }
  }
</script>

<style scoped>
  .main {
    max-width: 60%;
    position: relative;
    left: 20%;
    padding: 10px;
  }

  @media(max-width: 600px) {
    .main {
      max-width: 100%;
      left: 0%;
    }
  }
</style>
