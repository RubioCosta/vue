<template>
  <section id="board-main">
    <div 
      id="box-backlog"
      :data-custom-id="'box-main'"
      draggable="true" 
      @dragenter="handlerDragEnter" 
      @dragleave="handleDragLeave"
      @dragover="handlerDragOver"
      @drop="handlerDrop"
    >
      <DraggableCard 
        :titleCard="'Card 1'"
        :id="'card1'"
        :handlerDragStart="handlerDragStart"
        :handlerDragEnd="handlerDragEnd"
      />
    </div>
    <div 
      id="box-doing"
      :data-custom-id="'box-main'"
      draggable="true" 
      @dragenter="handlerDragEnter" 
      @dragleave="handleDragLeave"
      @dragover="handlerDragOver"
      @drop="handlerDrop"
    >
      <DraggableCard 
        :titleCard="'Card 2'"
        :id="'card2'"
        :handlerDragStart="handlerDragStart"
        :handlerDragEnd="handlerDragEnd"
      />
    </div>
    <div 
      id="box-done"
      :data-custom-id="'box-main'"
      draggable="true" 
      @dragenter="handlerDragEnter" 
      @dragleave="handleDragLeave"
      @dragover="handlerDragOver"
      @drop="handlerDrop"
    >
      <DraggableCard
        :titleCard="'Card 3'"
        :id="'card3'"
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
  const currentParentNode = ref(null)
  const isShowTemplate = ref(false)

  function handlerDragStart(e) {
    e.target.style.opacity = .5;

    currentCard.value = e.target;

    e.dataTransfer.effectAllowed = 'move';
  }
  
  function handlerDragEnter(e) {

    if (e.target.dataset.customId !== 'box-card-template') removePlaceholderCard();
    
    if (currentCard.value?.id === e.target.id || 
    (e.target.querySelectorAll('[data-custom-id="box-card"]').length === 1 ) &&
    (e.target.querySelectorAll('[data-custom-id="box-card"]')[0].id === currentCard.value.id) ||
    e.target.dataset.customId === 'box-card-template') {
      return;
    }

    if (e.target.dataset.customId === 'box-card') {
      e.target.parentNode.insertBefore(getTemplateCard(), e.target);
      isShowTemplate.value = true;
    }

    if (e.target.dataset.customId === 'box-main') {
      e.target.appendChild(getTemplateCard());
      isShowTemplate.value = true;
    }

    if (currentParentNode.value) return
    currentParentNode.value = e.target;

  }

  function handleDragLeave(e) {
    currentParentNode.value = null;
    
    if (currentCard.value?.id === e.target.id || 
    (e.target.querySelectorAll('[data-custom-id="box-card"]').length === 1 ) &&
    (e.target.querySelectorAll('[data-custom-id="box-card"]')[0].id === currentCard.value.id)) {
      return;
    }

    if (e.target.dataset.customId !== 'box-card-template' && isShowTemplate.value) {
      isShowTemplate.value = false;
      return
    }

    if (e.target.dataset.customId === 'box-card-template') {
      e.target.parentNode.removeChild(e.target);
    }

    if (e.target.dataset.customId === 'box-card') {
      const element = e.target.parentNode.querySelectorAll('[data-custom-id="box-card-template"]');

      if (!element.length) return;

      e.target.parentNode.removeChild(element[element.length - 1]);

      isShowTemplate.value = false;
    }
    
    if (e.target.dataset.customId === 'box-main') {
      const element = e.target.querySelector('[data-custom-id="box-card-template"]');

      if (!element) return;

      e.target.removeChild(element[element.length - 1]);

      isShowTemplate.value = false;
    }
  }
  
  function handlerDragOver(e) {
    e.preventDefault();
  }


  function handlerDragEnd(e) {
    currentCard.value = null;
    currentParentNode.value = null;

    if (e.target.dataset.customId === 'box-card') {
      document.querySelectorAll('[data-custom-id="box-card"]').forEach((el) => {
        el.style.border = '2px solid transparent';
      });
    }

    removePlaceholderCard();

    e.target.style.opacity = 1;
    e.target.style.backgroundColor = '#FFFFFF'
  }
  
  function handlerDrop(e) {
    e.preventDefault();

    console.log(currentCard.value?.dataset.customId, e.target.dataset.customId)

    if (e.target.dataset.customId !== 'box-main' && e.target.dataset.customId !== 'box-card-template') return;

    if (currentCard.value?.dataset.customId === e.target.dataset.customId) {
      currentParentNode.value = null;
      return; 
    }


    currentCard.value.parentNode.removeChild(currentCard.value);


    if (e.target.dataset.customId === 'box-card-template') {
      console.log(currentCard.value);
      console.log(e.target);
      e.target.parentNode.insertBefore(currentCard.value, e.target);
      e.target.parentNode.removeChild(e.target);
    } else {
      e.target.appendChild(currentCard.value);
    }
  }

  function getTemplateCard() {
    const template = document.createElement('div');
    template.style.height = '50px';
    template.style.width = '100%';
    template.style.backgroundColor = '#FFEEEE';
    template.setAttribute('data-custom-id', 'box-card-template');

    return template;
  }

  function removePlaceholderCard() {
    document.querySelectorAll('[data-custom-id="box-card-template"]').forEach((el) => {
      el.parentNode.removeChild(el);
    });
  }
  
</script>

<style scoped>
  #board-main {
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
