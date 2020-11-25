<template>
  <div class="posts-container">
    <div v-for="post in posts" :key="post.id" class="post">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      posts: []
    }
  },
  created () {
    this.getPosts()
  },
  methods: {
    getPosts () {
      const config = {
        'Content-Type': 'application/json',
        'Access-Control-Allow-Origin': true
      }

      axios
        .get('http://localhost:3000/posts', config)
        .then(res => (this.posts = res.data))
        .catch(err => console.log(err))
    }
  }
}
</script>
