<script setup>
  import { ref,reactive,onMounted } from 'vue'
  import axios from 'axios'

  const newses = ref(null)
  const loading = ref(true)

  async function getNews(){
    let res = await axios.get('https://basic-blog.teamrabbil.com/api/post-list/2')
    newses.value = res.data
    loading.value = false
  }

  onMounted(()=>{
    getNews()
  });

</script>

<template>
  <div class="container mx-auto px-4 ">
    <div v-if="loading == false" class="pt-5" v-for="(news, index) in newses" :key="index">
      <img :src="news.img" :alt="news.img">
    </div>

    <div v-else="loading" class="text-center mt-10">
      <h1 class="text-xl">Loading......</h1>
    </div>
  </div>
</template>

<style scoped>

</style>