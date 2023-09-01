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

const formatDate = (created_at) => {
  const options = { year: 'numeric', month: 'short', day: 'numeric' };
  return new Date(created_at).toLocaleDateString(undefined, options);
}

</script>

<template>
  <div class="container mx-auto px-4 ">
    <div class="article">
      <div v-if="loading == false" class="pt-5" v-for="(news, index) in newses" :key="index">
        <img :src="news.img" :alt="news.img">
        <p>{{news.title}}</p>
        <p>{{news.short}}</p>
      </div>

    <div v-else="loading" class="text-center mt-10">
      <h1 class="text-xl">Loading......</h1>
    </div>
  </div>

  </div>
</template>

<style scoped>

.article {
    display: flex;
    column-gap: 20px;
    border: 1p;
}

</style>