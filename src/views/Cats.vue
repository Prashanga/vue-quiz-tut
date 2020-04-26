<template>
  <div>
    <PetTable species="cats" :pets="cats" />
  </div>
</template>

<script>
// @ is the relative path starting from root and is accessible from everywhere
import { mapState } from 'vuex'
import PetTable from '@/components/PetTable.vue'

export default {
  components: {
    PetTable
  },
  data() {
    return {

    }
  },
  computed: {
    ...mapState([
      'cats'
    ])
  }
}
</script>

<style></style>
