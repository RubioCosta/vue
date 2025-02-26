<template>
  <div 
    id="draggable-card-main" 
    draggable="true"
    @dragstart="handlerDragStart"
    @dragend="handlerDragEnd"
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
    handlerDragEnd
  } = defineProps([
    'titleCard',
    'handlerDragStart',
    'handlerDragEnd'
  ]);

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