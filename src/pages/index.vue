<template>
  <b-container class="my-3">
    <PostForm :posts="posts"/>
    <Post v-for="post in posts" :post="post" :key="post.title" :comments="comments"/>
    <Comment v-if="show" />
  </b-container >
</template>


<script>
  import axios from "axios"
  const api= "http://localhost:4000/posts"

  export default {

    async fetch() {
      this.posts = await axios.get(api)
      .then((res) => {
        return res.data
        })

      this.comments = await axios.get("http://localhost:4000/comments")
      .then((res) => {
        return res.data
        })

    },

    data() {
      return {
        posts: [],
        comments: [],
        show: false
      }
    }
  }
</script>
