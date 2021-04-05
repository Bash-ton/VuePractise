<template>
  <h1>Your score</h1>
  <div class="result">{{ resultMessage }}</div>
  <div class="resultComment">{{ reactionComment }}</div>
</template>

<script>
export default {
    props: ['result'],
    data() {
        return{
            reactionComment: "",
            resultMessage: ""
        }
    },
    mounted() {
        this.getReactionComment(),
        this.getResultMessage()
        
    },
    methods: {
        getReactionComment() {
            if(this.result < 300){
                this.reactionComment = "wow suuper fast!!"
            }else if(this.result < 400){
                this.reactionComment = "very fast, nice!"
            }else if(this.result < 700){
                this.reactionComment = "not good at all :/"
            }else{
                this.reactionComment = "wow that is so slow I was just going to stop counting..."
            }
        },
        getResultMessage() {
            if(this.result === "cheat"){
                this.resultMessage = "You pressed too early",
                this.reactionComment = "nice try"
            }else{
                 this.resultMessage = this.result + 'ms'
            }
        }
    },
  


}
</script>

<style>
    

</style>