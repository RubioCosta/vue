<template>
  <section id="drag-drop-main">
    <div 
      id="box-backlog"
      draggable="true" 
      @dragenter="handlerDragEnter" 
      @dragleave="handleDragLeave"
      @dragover="handlerDragOver"
      @drop="handlerDrop"
    >
      <DraggableCard 
        :titleCard="'Card 1'"
        :handlerDragStart="handlerDragStart"
        :handlerDragEnd="handlerDragEnd"
      />
    </div>
    <div 
      id="box-doing"
      draggable="true" 
      @dragenter="handlerDragEnter" 
      @dragleave="handleDragLeave"
      @dragover="handlerDragOver"
      @drop="handlerDrop"
    >
      <DraggableCard 
        :titleCard="'Card 2'"
        :handlerDragStart="handlerDragStart"
        :handlerDragEnd="handlerDragEnd"
      />
    </div>
    <div 
      id="box-done"
      draggable="true" 
      @dragenter="handlerDragEnter" 
      @dragleave="handleDragLeave"
      @dragover="handlerDragOver"
      @drop="handlerDrop"
    >
      <DraggableCard
        :titleCard="'Card 3'"
        :handlerDragStart="handlerDragStart"
        :handlerDragEnd="handlerDragEnd"
      />
    </div>
  </section>
</template>

<script setup>
  // https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/drop_event

  import { ref } from 'vue';
  import DraggableCard from './DraggableCard.vue';

  const currentCard = ref(null)

  function handlerDragStart(e) {
    e.target.style.opacity = .5;

    currentCard.value = e.target;

    e.dataTransfer.effectAllowed = 'move';
  }
  
  function handlerDragEnter(e) {
    /*const newElement = document.createElement('div')
    newElement.style.height = '300px'
    newElement.style.backgroundColor = '#00FF00'
    newElement.style.width = '100%'
    newElement.innerHTML = 'teste'
    e.target.appendChild(newElement)*/
  }

  function handleDragLeave(e) {
  }
  
  console.log('Aqui 2')
  function handlerDragOver(e) {
    e.preventDefault();
  }


  function handlerDragEnd(e) {
    currentCard.value = null;
    e.target.style.opacity = 1;
    e.target.style.backgroundColor = '#FFFFFF'
  }
  
  function handlerDrop(e) {
    e.preventDefault();

    if (e.target !== currentCard) {
      currentCard.value.parentNode.removeChild(currentCard.value)
      e.target.appendChild(currentCard.value)
    }
  }
  
</script>

<style scoped>
  #drag-drop-main {
    margin: 5px;
    display: flex;
    justify-content: center;
    align-items: center;
    column-gap: 4px;
  }

  #box-backlog, #box-doing, #box-done {
    display: flex;
    flex-direction: column;
    flex: 1;
    height: 300px;
    padding: 5px;
    border-radius: 5px;
    row-gap: 5px;
  }

  #box-backlog {
    background-color: #888888;
  }

  #box-doing {
    background-color: #AAAAAA;
  }

  #box-done {
    background-color: #DDDDDD;
  }
</style>
