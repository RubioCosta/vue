<template>
  <section id="drag-drop-main">
    <div class="box-backlog">
      <DraggableCard 
        :titleCard="'Card 1'"
        :handlerDrop="handlerDrop"
        :handlerDragStart="handlerDragStart"
      />
    </div>
    <div class="box-doing">
      <DraggableCard 
        :titleCard="'Card 2'"
        :handlerDrop="handlerDrop"
        :handlerDragStart="handlerDragStart"
      />
    </div>
    <div class="box-done">
      <DraggableCard -
        :titleCard="'Card 3'"
        :handlerDrop="handlerDrop"
        :handlerDragStart="handlerDragStart"
      />
    </div>
  </section>
</template>

<script setup>
  import DraggableCard from './DraggableCard.vue';

  function handlerDragStart(e) {
    console.log("Start");
    e.target.style.opacity = .1;
  }
  
  function handlerDrop(e) {
    e.preventDefault();
    console.log("Drop");
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

  .box-backlog, .box-doing, .box-done {
    flex: 1;
    height: 300px;
    padding: 5px;
    border-radius: 5px;
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
