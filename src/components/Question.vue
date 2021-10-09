<template>
    <div class="questions-ctr">
        <div class="progress">
            <div class="bar"></div>
            <div class="status">{{id}} out of {{totalQuestions}} questions answered</div>
        </div>
        <div class="single-question" v-if="question">
            <div class="question">{{question.q}}</div>
            <div class="answers">
                <div class="answer" v-for="answer in question.answers" :key="answer" @click="selectedAnswer(answer.is_correct)">
                    {{answer.text}}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'Question',
    props:['question', 'currentId', 'totalQuestions'],
    emits:['selectedAnswer'],
    computed:{
        id(){
            return parseInt(this.currentId) >=  this.totalQuestions ? this.totalQuestions : parseInt(this.currentId) + 1
        }
    },
    methods:{
        selectedAnswer(result){
            this.$emit('selectedAnswer', result)
        }
    },
    data(){
        return {
            
        }
    }

}
</script>

<style>

</style>