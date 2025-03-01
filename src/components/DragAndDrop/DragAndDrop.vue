<template>
  <section id='drag-drop-main'>
    <form @submit="handlerAddNewBoardColumn">
      <input type="text" placeholder="Descrição da coluna..." />    

    </form>
  </section>
</template>

<script setup>
  impotr

  function handlerAddNewBoardColumn(e) {
    e.preventDefault();
  }

</script>

<style scoped>
  #drag-drop-main {
    max-width: 100%;
    margin: 5px;
  }
</style>