<template>
  <div class="container">
    <div class="card side-card">
      <div class="info">
        <p>Complete Tasks: {{ todos.filter(todo => {return todo.done == true}).length }}</p>
        <p>Incomplete Tasks: {{ todos.filter(todo => {return todo.done == false}).length }}</p>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
  export default {
    props: ['todos']
  }
</script>

<style>
  .side-card {
    position: absolute;
    width: 15%;
  }
  .container {
    padding:10px;
  }
</style>
