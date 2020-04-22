<template>
  <div>
    <b-jumbotron>
      <template v-slot:lead>
        <div v-html="question.question"></div>
      </template>
      <hr class="my-4" />
      <b-list-group>
        <b-list-group-item
          v-for="(answer, index) in shuffledAnswers"
          :key="index"
          @click="selectAnswer(index)"
          v-html="answer"
          :class="{ selected: index === selectedIndex }"
        >
        </b-list-group-item>
      </b-list-group>

      <b-button
        variant="primary"
        @click="submitAnswer"
        :disabled="!selectedIndex && answered"
        >Submit</b-button
      >
      <b-button variant="success" @click="next">Next</b-button>
    </b-jumbotron>
  </div>
</template>

<script>
import _ from "lodash"
export default {
  props: {
    question: Object,
    next: Function,
    increment: Function,
  },
  data() {
    return {
      selectedIndex: null,
      correctIndex: null,
      shuffledAnswers: [],
      answered: false,
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
  watch: {
    question: {
      immediate: true,
      handler() {
        this.selectedIndex = null
        this.shuffleAnswers()
      },
    },
  },
  methods: {
    selectAnswer(index) {
      this.selectedIndex = index
    },
    shuffleAnswers() {
      let answers = [...this.answers]
      this.shuffledAnswers = _.shuffle(answers)
      this.correctIndex = this.shuffledAnswers.indexOf(
        this.question.correct_answer
      )
    },
    submitAnswer() {
      let isCorrect = false
      if (this.selectedIndex === this.correctIndex) {
        isCorrect = true
      }
      this.increment(isCorrect)
      this.answered === true
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

.selected {
  background-color: lightblue;
}

.correct {
  background-color: rgb(184, 223, 184);
}

.incorrect {
  background-color: rgb(231, 103, 103);
}

.btn:disabled {
  background-color: lightgrey;
  border: none;
}
</style>
