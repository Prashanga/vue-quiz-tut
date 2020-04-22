<template>
  <div id="app">
    <Header :correct="numCorrect" :total="numTotal" />
    <div>
      <b-container class="bv-example-row">
        <b-row>
          <b-col sm="6" offset="3">
            <QuestionBox
              v-if="questions.length"
              :question="questions[index]"
              :next="next"
              :increment="increment"
            />
          </b-col>
        </b-row>
      </b-container>
    </div>
  </div>
</template>

<script>
import QuestionBox from "./components/QuestionBox"
import Header from "./components/Header"

export default {
  name: "App",
  components: {
    QuestionBox,
    Header,
  },
  data() {
    return {
      questions: [],
      index: 0,
      numCorrect: 0,
      numTotal: 0,
    }
  },
  methods: {
    next() {
      this.index++
    },
    increment(isCorrect) {
      if (isCorrect) {
        this.numCorrect++
      }
      this.numTotal++
    },
  },
  mounted: function() {
    fetch("https://opentdb.com/api.php?amount=10&category=17&type=multiple", {
      method: "get",
    })
      .then((res) => {
        return res.json()
      })
      .then((res) => {
        this.questions = res.results
      })
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
