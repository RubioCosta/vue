<template>
  <div id="post-main">
    <img :src="pathImage" />
  </div>
</template>

<script setup>
  const { pathImage } = defineProps(['pathImage'])
</script>

<style>
  #post-main {
    margin: 5px;
    box-shadow: 1px 1px 5px #413838;
  }
  
  img {
    width: 100%;
    min-height: 100%;
  }
</style>