<template>
  <div>
    <b-jumbotron>
      <template v-slot:lead>Some wuedstione</template>
      <hr class="my-4" />
      <p>List of answers</p>
      <b-button variant="primary" href="#">Submit</b-button>
      <b-button variant="primary" href="#">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    question: String,
  },
}
</script>

<style></style>
