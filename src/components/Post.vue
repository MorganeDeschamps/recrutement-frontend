<template>

<div class="py-3 border-top" >
    <b-container>
        <div class="pb-3 border-bottom">
      <b-row class="py-3">
        <b-col>
            <b-card-text class="font-weight-bolder">{{post.title}}</b-card-text>
        </b-col>
        <b-col>
            <b-card-text class="font-weight-light font-italic"> / {{post.author}}</b-card-text>
        </b-col>
        <b-col>
            <b-card-text class="text-right"> • {{getDate(post.createdAt)}}</b-card-text>
        </b-col>
      </b-row>
    <b-text class="py-3">
            {{ post.body}}
    </b-text>


     <div class="d-flex justify-content-end">
         <b-button v-if="!show" @click="show = true" variant="primary">Répondre</b-button>
     </div>
    </div>
    </b-container>

    <CommentForm v-if="show" :post="post" :comments="comments"/>
  

  <Comment v-for="comment in commentsForThis" :key="comment.id" :comment="comment"/>
</div>

</template>

<script>
import axios from 'axios'

export default {
  props: {
      post: {
          type: Object,
          default: () => {}
      },
      comments: {
        type: Array,
        default: () => {}
      }
  },

  methods: {
      getDate(date) {
          let readableDate = new Date(date);
          return readableDate.toLocaleDateString()
      }

  },

  async fetch() {
    this.commentsForThis = await axios.get(`http://localhost:4000/posts/${this.post.id}/comments`)
    .then((res) => {
        return res.data
        })

    },
  
    data() {
      return {
        posts: [],
        commentsForThis: [],
        show: false
      }
    }
}
</script>
