<template>
  <div class="card">
    <div class="content">
      <div>
        <span>Title:</span><textarea rows="1" class="text-input" v-model="title" placeholder="Input Title..."></textarea>
      </div>
      <div>
        <span>Project:</span><textarea rows="1" class="text-input" v-model="project" placeholder="Input Project..."></textarea>
      </div>

      <div class="space"></div>
      <div>
        <i class="fa fa-plus button" aria-hidden="true" v-on:click="createTodo()"></i>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
  import { EventBus } from '../event-bus.js'

  export default {
    data () {
      return {
        title: '',
        project: ''
      }
    },
    methods: {
      createTodo () {
        if (this.title !== '') {
          this.$emit('create-todo', {title: this.title, project: this.project, done: false})
        } else {
          EventBus.$emit('error', 'Please specify at least a title for the Todo!')
        }
      }
    }
  }
</script>

<style>
  .text-input {
    font-size: 1.1em;
    margin: 5px;
    resize: none;
    border: 1px solid #888;
    box-shadow: 0px 0px 5px #aaa;
    padding: 5px;
  }

  .button {
    background-color: white;
    width: 1.5rem;
    height: 1.5rem;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
  }
</style>
