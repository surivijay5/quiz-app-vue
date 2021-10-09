<template>
    <div class="result" v-if="selectedAnswers.length === totalQuestions">
        <div class="title">You got {{correctAnswers}} correct Answers!</div>
        <div class="desc">
            {{getDes()}}
        </div>
    </div>
</template>

<script>
export default {
    name:'Result',
    props: ['selectedAnswers', 'resultData', 'totalQuestions'],
    computed:{
        correctAnswers(){
            return this.selectedAnswers.filter(p => p).length
        },
    },
    methods:{
        getDes(){
            for(let data of this.resultData ?? []){
                if(this.correctAnswers >= data.min && this.correctAnswers <= data.max){
                    return data.desc
                }
            }
        }
    }
}
</script>

<style>

</style>