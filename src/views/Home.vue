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
import PostList from '@/components/PostList.vue'

export default {
  name: 'Home',
  components: {
    PostList
  },
  setup() {
    

    const showPosts = ref(true)

    return { 
      posts,
      error,
      showPosts,
    }
  }
}
</script>
