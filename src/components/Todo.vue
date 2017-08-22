<template>
  <div class="card">
    <div class="content" v-show="!isEditing">
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
      <div class="fa fa-pencil" aria-hidden="true" v-on:click="edit()"></div>
      <div class="fa fa-trash" aria-hidden="true" v-on:click="deleteTodo(todo)"></div>
    </div>
    <div class="content" v-show="isEditing">
      <div><textarea rows="1" class="input" v-model="todo.title" v-bind:placeholder="todo.title"></textarea></div>
      <div><textarea rows="1" class="input" v-model="todo.project" v-bind:placeholder="todo.project"></textarea></div>
      <div class="space"></div>
      <div class="fa fa-check" aria-hidden="true" v-on:click="updateTodo(todo)"></div>
    </div>
  </div>
</template>

<script type="text/javascript">
  export default {
    data () {
      return {
        isEditing: false
      }
    },
    props: ['todo'],
    methods: {
      edit () {
        this.isEditing = true
      },
      updateTodo (todo) {
        this.isEditing = false
        this.$emit('update-todo', todo)
      },
      completeTodo (todo) {
        this.$emit('complete-todo', todo)
      },
      deleteTodo (todo) {
        this.$emit('delete-todo', todo)
      }
    }
  }
</script>

<style>
.input {
  font-size: 1.1em;
  margin: 5px;
  resize: none;
  border: 1px solid #888;
  box-shadow: 0px 0px 5px #aaa;
  padding: 5px;
}

.card {
  border: 1px solid #888;
  border-radius: 0px;
  box-shadow: 0px 0px 5px #aaa;
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
