<template>
  <div>
    <div v-if="posts">
      <post-card v-for="post in posts" :key="post.id" :post="post"></post-card>
    </div>
    <div v-else>Loading..</div>
  </div>
</template>

<script>
import axios from 'axios';
import PostCard from './components/PostCard.vue';

export default {
  data() {
    return {
      posts: null,
    };
  },
  name: 'App',
  components: {
    PostCard
  },
  methods: {
    fetchDataFromApi() {
      axios.get('http://localhost:8000/posts')
      .then(response => {
        this.posts = response.data.data;
      })
      .catch(error => {
        console.log('Ada yang salah nih: ' + error);
      })
    }
  },
  mounted() {
    this.fetchDataFromApi()
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>
