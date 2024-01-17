<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts" />
    </div>
    <div v-else><Spiner /></div>
  </div>
</template>

<script>
import PostList from '../components/PostList.vue'
import getPosts from "../composable/getPosts"
import Spiner from '../components/Spiner.vue'

export default {
  name: 'Home',
  components: { PostList, Spiner },
  setup() { 
const {posts, error, load} = getPosts()
 load()
    
    return { posts, error,  }
  },
}
</script>

<style>
.home{
  max-width: 1200px;
  margin: 0 auto;
  padding: 10px;
}
</style>