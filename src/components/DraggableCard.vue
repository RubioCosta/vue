<template>
  <div 
    id="draggable-card-main" 
    draggable="true"
    @dragstart="handlerDragStart"
    @dragend="handlerDragEnd"
    ref="draggableCard"
  >
    {{ titleCard }}
  </div>
</template>

<script setup>
  import { ref } from 'vue';
  const { titleCard } = defineProps(['titleCard']);

  const draggableCard = ref(null);

  function handlerDragStart(e) {
    console.log("Aqui 1")
  }
  
  function handlerDragEnd(e) {
    console.log("Aqui 2")
  }
</script>

<style scoped>
  #draggable-card-main {
    cursor: grab;
    max-width: 100%;
    height: 30px;
    background-color: #FFFFFF;
    border-radius: 5px;
    padding: 5px;
  }
</style>