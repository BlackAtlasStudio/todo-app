<template>
  <div class="container">
    <div class="card side-card">
      <div class="info">
        <p>Complete Tasks: {{ todos.filter(todo => {return todo.done == true}).length }}</p>
        <p>Incomplete Tasks: {{ todos.filter(todo => {return todo.done == false}).length }}</p>
      </div>
      <div class="radial">
        <div class="circle"></div>
        <div class="top-red"></div>
        <div class="bottom-green"></div>
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
    width: 15%;
    top: 5em;
    left: 1em;
    position: fixed;
  }

  .radial {
    width: 100%;
  }

  .circle {
    align-content: center;
    border-radius: 50%;
    width: 10em;
    height: 10em;
    background-color: #f00;
    margin: auto;
  }
</style>
