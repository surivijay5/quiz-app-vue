<template>
<div class="ctr">
    <Question  :question="currentQuestion" :currentId="currentQuestionId" :totalQuestions="questions.length" @selectedAnswer="selectedAnswer"></Question>
    <Result :selectedAnswers="selectedAnswers" :resultData="result" :totalQuestions="questions.length"></Result>
    <button type="button" class="reset-btn" @click="reset">Reset</button>
</div>
</template>

<script>

import Question from './components/Question.vue'
import Result from './components/Result.vue'
import quizAppData from './quizAppData.js'

export default {
  name: 'App',
  components: {
    Question,
    Result
  },
  computed:{
    currentQuestion(){
      return this.questions[this.currentQuestionId]
    }
  },
  data(){
    return{
      currentQuestionId : 0,
      questions: quizAppData.questions,
      result: quizAppData.results,
      selectedAnswers: []
    }
  },
  methods:{
    reset(){
      this.currentQuestionId = 0
      this.selectedAnswers = []
    },
    selectedAnswer(result){
      if(this.currentQuestionId < this.questions.length){
        this.currentQuestionId++
        this.selectedAnswers.push(result)
      }
    }
  }
}
</script>

<style>

</style>
