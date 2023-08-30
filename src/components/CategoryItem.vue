<script setup>
import {ref, onMounted} from 'vue';
import axios from 'axios';
const categories = ref([]);




// const fetchCountries = async () => {
//   try {
//     const response = await axios.get('https://basic-blog.teamrabbil.com/api/post-newest');
//     datas.value = response.data;
//   } catch (error) {
//     console.error('Error fetching data:', error);
//   }
// };

// onMounted(() => {
//   fetchCountries();
// });


const fetchCategories = async ()=>{
  try{
      let url = 'https://basic-blog.teamrabbil.com/api/post-categories';
      const response = await axios.get(url);
      categories.value = response.data;
      console.log(response.data);

  }catch(error){
    console.error('Error', error);
  }
}

onMounted(()=>{
  fetchCategories();
})




</script>
<template>
<h2>Category List:</h2>
  <ul>
    <li v-for="category in categories">{{ category.name }} || </li>
  </ul>
</template>

<style scoped>
  ul{
    display: flex;
  }
  li{
    margin-right: 10px;
  }
  h2{
    font-size: 25px;
    font-weight: bolder;
  }
</style>