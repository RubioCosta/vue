<template>
  <section id="box-drag-drop-update">
    <div class="menu">
      <ul>
        <li v-for="item in itemsMenu">
          <input type="text" :value="item.title" @click="() => item.isEdit = true" :readonly="item.isEdit">
        </li>
      </ul>
      <button @click="handlerCreateDirectory">CRIAR DIRETÓRIO NOVO</button>
    </div>
    <div class="list-items">
      LIST ITEMS
    </div>
  </section>
</template>

<script setup>
  import { ref } from 'vue'

  const itemsMenu = ref([{id: 1, title: 'teste', isEdit: true}])

  function handlerEditItem(t) {
    console.log("aqui", t)
  }

</script>

<style scoped>
  #box-drag-drop-update {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 100%;
  }

  .menu, .list-items {
    padding: 5px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
    min-height: 100vh;
    box-sizing: border-box;
  }

  .menu {
    flex: 2;
    background-color: #1898E0;
  }

  .menu button {
    width: 100%;
    height: 30px;
    background-color: #DDDFFF;
    border: none;
    outline: none;
    border-radius: 5px;
    cursor: pointer;
    font-weight: 700;
  }

  .menu button:hover {
    background-color: #DDDDDF;
  }
  
  .list-items {
    flex: 7;
    background-color: yellow;
  }

  ul {
    width: 100%;
  }

  ul li {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    list-style: none;
    margin-bottom: 5px;
  }

  ul li:hover {

  }

  ul li input {
    padding-left: 5px;
    box-sizing: border-box;
    height: 30px;
    width: 100%;
    border: none;
    outline: none;
    cursor: pointer;
    border-radius: 5px;
    background-color: #FFFFFF;
    border-radius: 5px;
  }

</style>