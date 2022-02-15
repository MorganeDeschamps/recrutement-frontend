<template>
  <div class="mb-3">
    <b-form @submit="formSubmit" v-if="show">
      <b-form-group id="input-group-1">
        <b-form-input
          id="input-1"
          v-model="form.author"
          placeholder="Pseudo"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2">
        <b-form-input
          id="input-2"
          v-model="form.title"
          placeholder="Titre publication"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3">
        <b-form-textarea
          id="textarea"
          v-model="form.body"
          placeholder="Message"
          rows="5"
          max-rows="8"
        ></b-form-textarea>
      </b-form-group>

      <div class="d-flex justify-content-end">
        <b-button  type="submit" variant="primary">Publier</b-button>
      </div>
    </b-form>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    props: {
      posts: {
          type: Array,
          default: () => {}
      }
    },

    data() {
      let idNumber = this.posts.length + 1;

      return {
        form: {
          id: `${idNumber}`,
          author: '',
          title: '',
          body: '',
          createdAt: `${new Date().toISOString()}`
        },
        show: true
      }
    },
    methods: {
    async formSubmit() {
      await axios.post('http://localhost:4000/posts', {
        id: this.form.id,
        author: this.form.author, 
        title: this.form.title,
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

