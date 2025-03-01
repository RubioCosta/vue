<template>
  <section id="app-main">
    <ul>
      <li @click="handlerShowComponent('InfinityScroll')">INFINITY SCROLL</li>
      <li @click="handlerShowComponent('DragAndDrop')">DRAG AND DROP</li>
    </ul>
    <div v-show="typeSelected==='InfinityScroll'">
      <InfinityScroll />
      <br />
      <InfinityScroll />
    </div>
    <div v-show="typeSelected==='DragAndDrop'">
      <DragAndDrop />
    </div>
  </section>
</template>

<script setup>
  import { ref } from 'vue'; 

  // Components
  import InfinityScroll from './components/InfinityScroll/InfinityScroll.vue';
  import DragAndDrop from './components/DragAndDrop/DragAndDrop.vue';

  const typeSelected = ref('DragAndDrop');

  function handlerShowComponent(type) {
    typeSelected.value = type
  }
</script>

<style scoped>
  ul {
    display: flex;
    flex-direction: column;
    list-style-type: none;
    padding: 0;
  }

  li {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    background-color: #DDDDDD;
    height: 30px;
    max-width: 100%;
    margin: 4px;
    font-size: 1em;
    padding-left: 4px;
    cursor: pointer;
  }
  
  li:hover {
    background-color: #BBBBBB;
  }

</style>