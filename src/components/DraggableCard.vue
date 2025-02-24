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
    ref="draggableCard"
  >
    {{ titleCard }}
  </div>
</template>

<script setup>
  // https://web.dev/articles/drag-and-drop?hl=pt-br
  // https://developer.mozilla.org/pt-BR/docs/Web/API/HTML_Drag_and_Drop_API

  import { ref } from 'vue';
  const { titleCard } = defineProps(['titleCard']);

  const draggableCard = ref(null);

  function handlerDragStart(e) {
    // console.log("Iniciando o processo de Draggable.")
    e.target.style.opacity = .1;

    e.dataTransfer.effectAllowed = 'move';
    e.dataTransfer.setData('text/html', draggableCard.value.innerHTML)
  }
  
  function handlerDragEnd(e) {
    // console.log("Finalizando o processo de Draggable.")
    draggableCard.value.style.opacity = 1;
  }
  
  function handlerDragEnter(e) {
    // console.log("Dentro do elemento de Dropped.")
  }
  
  function handleDragLeave(e) {
    draggableCard.value.style.backgroundColor = '#FFFFFF'
    // console.log("Saindo do elemento de Dropped.")
  }

  function handlerDragOver(e) {
    e.preventDefault();

    draggableCard.value.style.backgroundColor = '#000000'
    // console.log("Quando o elemento estiver sobre o elemento de Dropped.")
  }

  function handlerDrop(e) {
    e.preventDefault(); // Retirar o o comportamento padrão do navegador para quedas.

    console.log("Aqui 1: ", draggableCard.value)
    console.log("Aqui 2: ", e.target)
    if (draggableCard.value !== e.target) {
      draggableCard.value = e.target;
      e.target = e.dataTransfer.getDate('text/html')
    }

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