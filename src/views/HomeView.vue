<script setup>
  import { ref,reactive,onMounted } from 'vue'
  import axios from 'axios'

  const newses = ref(null)
  const loading = ref(true)

  async function getNews(){
    let res = await axios.get('https://basic-blog.teamrabbil.com/api/post-newest')
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
      <div v-if="loading == false" class="blog-grid" v-for="(news, index) in newses" :key="index">
        <img :src="news.img" :alt="news.img">
        <div class="padding-5">
        <strong>{{news.title}}</strong>
        <p>{{news.short}}</p>
        </div>
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
  flex-wrap: wrap;
  row-gap: 40px;
}
.blog-grid {
    background-color: rgba(220, 220, 220, 0.362);
    width: 32%;
    box-shadow: 1px 1px 3px gainsboro;
}
.article strong {
  padding: 10px 0;
  line-height: 1.5em;
  display: block;
}
.padding-5 {
  display: block;
  padding: 10px;
}
nav {
  margin-top: 30px;
}
</style>