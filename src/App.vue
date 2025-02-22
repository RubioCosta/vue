<template>
  <section>
    <InfinityScroll />
    <br />
    <InfinityScroll />
  </section>
</template>

<script >
  import InfinityScroll from './components/InfinityScroll.vue';

  export default {
    name: 'App',
    components: {
      InfinityScroll
    }
  }
</script>