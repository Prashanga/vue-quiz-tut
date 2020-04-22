<template>
  <div>
    <b-jumbotron>
      <template v-slot:lead>
        <div v-html="question.question"></div>
      </template>
      <hr class="my-4" />
      <b-list-group>
        <b-list-group-item
          v-for="(answer, index) in answers"
          :key="index"
          @click="selectAnswer(index)"
          v-html="answer"
        >
        </b-list-group-item>
      </b-list-group>

      <b-button variant="primary" href="#">Submit</b-button>
      <b-button variant="success" @click="next" href="#">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
export default {
  props: {
    question: Object,
    next: Function,
  },
  data() {
    return {
      selectedIndex: null,
    }
  },
  computed: {
    answers() {
      let answers = [
        ...this.question.incorrect_answers,
        this.question.correct_answer,
      ]
      return answers
    },
  },
  methods: {
    selectAnswer(index) {
      this.selectedIndex = index
    },
  },
}
</script>

<style scoped>
.btn {
  margin: 10px 10px;
}

.list-group-item:hover {
  background-color: #eee;
  cursor: pointer;
}
</style>
