<template>

    <b-container class="bv-example-row py-3 ">
    <b-row align-h="end">
        <b-col cols="5">{{ comment.body }}</b-col>
        <b-col cols="2" class="text-right"> • {{ getDate(comment.createdAt) }}</b-col>
    </b-row>
    </b-container>


</template>

<script>
export default {
    props: {
      comment: {
          type: Object,
          default: () => {}
      }
    },

    methods: {
      getDate(date) {
          let readableDate = new Date(date);
          return readableDate.toLocaleDateString()
      }

  },


    data() {
        return {
            show:false
        }
    }
}
</script>
