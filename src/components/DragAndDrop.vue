<template>
  <section id="drag-drop-main">
    <div class="box-backlog">

    </div>
    <div class="box-doing">

    </div>
    <div class="box-done">

    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
  #drag-drop-main {
    margin: 5px;
    background-color: black;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 2;
  }

  .box-backlog, .box-doing, .box-done {
    flex: 1;
    height: 300px;
  }

  .box-backlog {
    background-color: #888888;
  }

  .box-doing {
    background-color: #AAAAAA;
  }

  .box-done {
    background-color: #DDDDDD;
  }

</style>
