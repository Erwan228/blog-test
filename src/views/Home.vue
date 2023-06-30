<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
    <PostList v-if="showPosts" :posts="posts"/>
    </div>
    <div v-else>Loading...</div>
    <button @click="showPosts = !showPosts">toggle posts</button>
    <button @click="posts.pop()">Delete a post</button>
  </div>
</template>

<script>
import { ref } from 'vue'
import PostList from '@/components/PostList.vue'
import getPosts from '../composables/getPosts'
export default {
  name: 'Home',
  components: {
    PostList
  },
  setup() {
    const {posts, error, load} = getPosts()

    const showPosts = ref(true)

    load()

    return { 
      posts,
      error,
      showPosts,
    }
  }
}
</script>
