<template>
  <section id="infinity-scroll-main" @scroll="addInfinityScroll">
    <div class="box-image" v-for="(post, index) in postsCurrent">
      <Post :pathImage="post.url" />
      <Post :pathImage="post.url" />
    </div>
  </section>
</template>

<script setup>
  import { onMounted, ref } from 'vue' 
  import Post from './Post.vue';

  const PACK_SIZE = 10
  const postsCurrent = ref([])
  const postsStack = ref([])

  onMounted(async () => {
    getPackPosts() 
  })

  async function addInfinityScroll(e) {
    const heightScrollY = e.target.scrollHeight;
    const positionTop = e.target.scrollTop;
    const scrollClientView = e.target.clientHeight;

    if ((heightScrollY - (positionTop + scrollClientView)) < 80 ) {
      await getPackPosts()
    }
  }

  async function getPackPosts() {
    const promises = []

    for (let i = 0; i < PACK_SIZE; i++) {
      promises.push(getPost())
    }

    const listImages = await Promise.all(promises)

    postsCurrent.value.push(...listImages)
  }

  async function getPost() {
    const response = await fetch('https://picsum.photos/800/500')
    const { url } = response;

    return { url };
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

  .box-image {
    display: flex;
  }
</style>