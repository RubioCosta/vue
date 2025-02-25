<template>
  <div 
    id="draggable-card-main" 
    draggable="true"
    @dragstart="handlerDragStart"
    @dragend="handlerDragEnd"
    @dragenter="handlerDragEnter"
    @dragleave="handleDragLeave"
    @dragover="handlerDragOver"
    @drop="handlerDrop"
  >
    {{ titleCard }}
  </div>
</template>

<script setup>
  // https://web.dev/articles/drag-and-drop?hl=pt-br
  // https://developer.mozilla.org/pt-BR/docs/Web/API/HTML_Drag_and_Drop_API

  const { 
    titleCard,
    handlerDragStart,
    handlerDrop
  } = defineProps([
    'titleCard',
    'handlerDragStart',
    'handlerDrop'
  ]);
  
  function handlerDragEnd(e) {
    e.target.style.opacity = 1;
  }
  
  function handlerDragEnter(e) {
    
  }
  
  function handleDragLeave(e) {
    e.target.style.backgroundColor = '#FFFFFF'
  }

  function handlerDragOver(e) {
    e.preventDefault();

    e.target.style.backgroundColor = '#000000'
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