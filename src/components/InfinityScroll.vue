<template>
  <section id="infinity-scroll-main" @scroll="addInfinityScroll">
    <div class="box-image" v-for="(post, index) in postsCurrent">
      <Loading :id="post.id" />
    </div>
  </section>
</template>

<script setup>
  import { onMounted, ref } from 'vue' 
  import Loading from './Loading.vue';

  const PACK_SIZE = 10;

  const postsCurrent = ref([])
  const postsStackTop = ref([])
  const postsStackBottom = ref([])
  const sequence = ref(1)
  const isLoading = ref(false)

  onMounted(async () => {
    getPackPosts() 
  })

  async function addInfinityScroll(e) {
    if (isLoading.value) return

    // Scroll on top
    if ((e.target.scrollTop < 20) && (postsStackTop.value.length > 0)) {
      postsStackBottom.value.unshift(...postsCurrent.value.splice(-PACK_SIZE));
      postsCurrent.value.unshift(...postsStackTop.value.splice(-PACK_SIZE));
      e.target.scrollTop = e.target.scrollHeight / 2;
      return
    }
    
    // Scroll on bottom
    if ((e.target.scrollHeight - (e.target.scrollTop + e.target.clientHeight)) < PACK_SIZE * 2 ) {
      
      if (postsStackBottom.value.length > 0) {
        postsCurrent.value.push(...postsStackBottom.value.splice(0, PACK_SIZE));
        postsStackTop.value.push(...postsCurrent.value.splice(0, PACK_SIZE));
        e.target.scrollTop = (e.target.scrollTop / 2) - (e.target.clientHeight / 2);
        return
      }
      
      await getPackPosts();

      if (postsCurrent.value.length > (PACK_SIZE * 2) ) {
        postsStackTop.value.push(...postsCurrent.value.splice(0, PACK_SIZE));
        e.target.scrollTop = (e.target.scrollTop / 2) - (e.target.clientHeight / 2);
      }
    }
  }

  async function getPackPosts(size = PACK_SIZE) {
    isLoading.value = true;

    for (let i = 0; i < size; i++) {
      postsCurrent.value.push({ id: sequence.value++ });
    }
    
    isLoading.value = false;
  }
</script>

<style>
  #infinity-scroll-main {
    max-width: 100%;
    height: 40vh;
    box-shadow: 1px 1px 3px #837e7e;
    margin: 5px;
    overflow-y: scroll;
  }
</style>