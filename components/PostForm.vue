<template>
  <form @submit="createPost">
    <div>
      <label for="title">Title</label>
      <input type="text" name="title" v-model="title" />
    </div>
    <div>
      <label for="body">Body</label>
      <textarea name="body" v-model="body" />
    </div>
    <button>
      Submit
    </button>
  </form>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      title: '',
      body: ''
    }
  },
  methods: {
    createPost (e) {
      e.preventDefault()

      const post = { title: this.title, body: this.body }
      console.log(post)

      axios
        .post('http://localhost:3000/posts', post)
        .then(res => console.log(res))
        .catch(err => console.log(err))
    }
  }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

form div {
  margin: 40px 0;
  display: flex;
  align-items: center;
}

form label {
  margin-right: 20px;
}

form input {
  border: 1px solid blue;
  border-radius: 5px;
}

form textarea {
  border: 1px solid blue;
  border-radius: 5px;
}

form button {
  background: blue;
  color: #fff;
  padding: 20px;
  border-radius: 10px;
}
</style>
