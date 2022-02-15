<template>
  <div>
    <b-form @submit="formSubmit" v-if="show">
      <b-form-group id="input-group-3">
        <b-form-textarea
          id="textarea"
          v-model="form.body"
          placeholder="Message"
          rows="3"
          max-rows="5"
        ></b-form-textarea>
      </b-form-group>

      <b-button type="submit" variant="primary">Publier</b-button>
    </b-form>
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

    data() {
      let idNumber = this.comments.length + 1;

      return {
        form: {
          id: `${idNumber}`,
          body: '',
          createdAt: `${new Date().toISOString()}`
        },
        show: true
      }
    },
    methods: {
    async formSubmit() {
      await axios.post(`http://localhost:4000/posts/${this.post.id}/comments`, {
        id: this.form.id,
        body: this.form.body,
        createdAt: this.form.createdAt
      })
      .then(response => {
        console.log(response)
      })
      .catch(err => {
        console.log(err)
      })
    }
  }
  }
</script>

