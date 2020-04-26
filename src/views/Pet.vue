<template>
  <div>
    Name: {{ animal.name }}<br>
    Age: {{ animal.age }}<br>
    Breed: {{ animal.breed }}<br>
    Species: {{$route.params.species}}

  </div>

</template>

<script>
// @ is the relative path starting from root and is accessible from everywhere
import { mapState } from 'vuex'

export default {
  data() {
    return {
      animal: {}
    }
  },
  computed: {
    ...mapState([
      'cats',
      'dogs'
    ])
  },

  mounted() {
    const animal = this[this.$route.params.species][this.$route.params.id]
    this.animal = animal
  }

}

</script>
<style></style>
