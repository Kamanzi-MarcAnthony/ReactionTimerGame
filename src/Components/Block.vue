<template>

    <div class="block" v-if="showBlock" @click="stopTimer">
        {{delay}}
    </div>

</template>

<script>

export default{
    props: ['delay'],
    data (){
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }

    },
    mounted(){
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            console.log()
        }, 
        this.delay)    
    },

    methods: {
        startTimer(){
            this.timer = setInterval(() =>{
                this.reactionTime += 10
            }, 10)

        },
        stopTimer(){
            clearInterval(this.timer)
            console.log("your reaction time is " + this.reactionTime)
            this.$emit('game-over', this.reactionTime)
        }
    }

}
</script>

<style scoped>
.block{
    width: 400px;
    border-radius: 20px;
    background: #460690FF;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}

</style>
