<template>
  <div id="app">
    <Header />
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="6" offset="3">
          <QuestionBox :question="questions[index]" />
        </b-col>
      </b-row>
    </b-container>
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
    }
  },
  mounted() {
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
