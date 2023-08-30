<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const datas = ref([]);
//https://documenter.getpostman.com/view/9518923/2s946mZ9Zw
const fetchCountries = async () => {
  try {
    const response = await axios.get('https://basic-blog.teamrabbil.com/api/post-newest');
    datas.value = response.data;
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};

onMounted(() => {
  fetchCountries();
});


</script>

<template>
<h1>Our Latest News:</h1>
  <div class="grid grid-cols-1 grid-rows-1 md:grid-cols-3 mt-20">
  <div class="mr-4 block rounded-lg bg-white shadow-[0_2px_15px_-3px_rgba(0,0,0,0.07),0_10px_20px_-2px_rgba(0,0,0,0.04)] dark:bg-neutral-700" v-for="data in datas">
    <div class="p-6">
      <div class="bg-indigo-300 ...">
        <img class="object-cover h-48 w-96" :src="data.img">
      </div>
      <h5  class="mb-2 text-xl font-medium leading-tight text-neutral-800 dark:text-neutral-50">Title: {{ data.title }}</h5>
      <p class="mb-4 text-base text-neutral-600 dark:text-neutral-200">Des:{{ data.short }}</p>
      <button class="bg-blue-500 hover:bg-blue-400 text-white font-bold py-2 px-4 rounded"><a href="" class="text-white">Visit More</a></button>
    </div>
  </div>

  
</div>



</template>

<style scoped>

</style>
