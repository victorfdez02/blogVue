<template>
  <div>
    <Header />

    <div class="container">
      <div class="row">
        <Card v-for="post in posts" :key="post.id" :post="post" />
      </div>
    </div>
  </div>
</template>

<script setup>
import Header from './components/Header.vue'
import Card from './components/Card.vue'

import { ref, onMounted } from 'vue';

const posts = ref([]);

const pedirPosts = async () => {
  try {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts');
    const data = await res.json();
    posts.value = data;
  } catch (error) {
    console.error('Error fetching data:', error);
  }
};

onMounted(() => {
  pedirPosts();
});
</script>

<script>
import 'bootstrap/dist/css/bootstrap.min.css';
</script>
