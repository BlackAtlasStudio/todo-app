<template>
  <div id="app">
    <title-bar v-bind:titlebar="titlebar"></title-bar>
    <todo-list-stats v-bind:todos="todos"></todo-list-stats>
    <todo-list v-bind:todos="todos"></todo-list>
  </div>
</template>

<script>
import TodoList from './components/TodoList'
import TitleBar from './components/TitleBar'
import TodoListStats from './components/TodoListStats'
import { EventBus } from './event-bus.js'

EventBus.$on('error', function (message) {
  console.log(message)
})

export default {
  name: 'app',
  components: {
    TitleBar,
    TodoList,
    TodoListStats
  },
  data () {
    return {
      titlebar: 'Todo App',
      todos: [{
        title: 'Todo A',
        project: 'Project A',
        done: false
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: false
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: true
      }]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #444;
}

body {
  margin: 0px;
}
</style>
