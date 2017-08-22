<template>
  <div>
    <div class="full-header">
      <h1 class="title">{{ titlebar }}</h1>
    </div>
    <div class="header-space"></div>
  </div>
</template>

<script type="text/javascript">
  export default {
    props: ['titlebar']
  }
</script>

<style scoped>
  .full-header {
    width: 100%;
    box-shadow: 0px 2px 5px #aaa;
    position: fixed;
    background-color: white;
    z-index: 1000;
  }

  .title {
    text-align: center;
    font-weight: 100;
    font-size: 3em;
  }

  h1 {
    margin: 0px;
    vertical-align: middle;
  }

  .header-space {
    height: 4em;
  }
</style>
