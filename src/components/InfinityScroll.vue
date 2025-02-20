<template>
  <section id="infinity-scroll-main" v-on:scroll="addInfinityScroll">
    <div v-for="(item, index) in list">
      <Loading :key="index" />
    </div>
  </section>
  <section id="infinity-scroll-main" v-on:scroll="addInfinityScroll">
    <div v-for="(item, index) in list">
      <Loading :key="index" />
    </div>
  </section>
</template>

<script>
  import Loading from './Loading.vue';
  export default {
    name: 'InfinityScroll',
    components: {
      Loading
    },
    data() {
      return {
        list: [{}]
      }
    },
    methods: {
      addInfinityScroll(e) {
        const heightScrollY = e.target.scrollHeight;
        const positionTop = e.target.scrollTop;
        const scrollClientView = e.target.clientHeight;

        if ((heightScrollY - (positionTop + scrollClientView)) < 60 ) this.list.push({})
      }
    }
  }
</script>

<style>
  #infinity-scroll-main {
    max-width: 100%;
    height: 48vh;
    box-shadow: 1px 1px 3px #837e7e;
    margin: 5px;
    overflow-y: scroll;
  }
</style>