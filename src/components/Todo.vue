<template>
  <div class="card">
    <div class="content">
      <div class="header">
        {{ todo.title }}
      </div>
      <div class="project">
        {{ todo.project }}
      </div>
      <div class="space"></div>
      <a class="todo-status green" v-show="todo.done">
        Completed
      </a>
      <a class="todo-status red" v-on:click="completeTodo(todo)" v-show="!todo.done">
        Incomplete
      </a>
      <div class="fa fa-pencil" aria-hidden="true"></div>
      <div class="fa fa-trash" aria-hidden="true"></div>
    </div>
  </div>
</template>

<script type="text/javascript">
  export default {
    props: ['todo'],
    methods: {
      completeTodo (todo) {
        this.$emit('complete-todo', todo)
      }
    }
  }
</script>

<style>
.card {
  border: 1px solid #888;
  border-radius: 10px;
  box-shadow: 0px 0px 5px #444;
  padding: 10px;
  margin: 10px;
}

.content {
  display: flex;
  flex-direction: row;
  align-content: center;
  justify-content: center;
}

.content>div {
  margin-left: 10px;
  display: flex;
  align-items: center;
}

hr {
  margin-top: 2px;
  margin-bottom: 5px;
}

.header {
  font-weight: bold;
  font-size: 1.2em;
  text-align: center;
}

.project {

}

.space {
  flex: 1;
}

.todo-status {
  border-radius: 5px;
  height: 2em;
  display: flex;
  align-items: center;
  justify-content: center;
  padding-left: 5px;
  padding-right: 5px;
}

.green {
  background-color: #5f5;
}

.red {
  background-color: #f55;
}

</style>
