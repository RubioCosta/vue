<template>
  <div 
    :id="id"
    class="draggable-card-main"
    draggable="true"
    :data-custom-id="'box-card'"
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
    id,
    titleCard,
    handlerDragStart,
    handlerDragEnd
  } = defineProps([
    'id',
    'titleCard',
    'handlerDragStart',
    'handlerDragEnd'
  ]);

</script>

<style scoped>
  .draggable-card-main {
    border: 2px solid transparent;
    cursor: grab;
    max-width: 100%;
    height: 30px;
    background-color: #FFFFFF;
    border-radius: 5px;
    padding: 5px;
  }
</style>