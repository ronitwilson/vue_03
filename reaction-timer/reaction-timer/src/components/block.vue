<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        click me
    </div>
    
</template>
<script>
export default {
    props: ['prop_timer_delay'],
    data() {
        return {
            showBlock: false,
            reactionTime: 0, 
            timer: null
        }
    },
    mounted() {
        console.log("the componenet is loaded")
        console.log("the prop timer is ", this.prop_timer_delay)
        setTimeout(() => {
            this.showBlock = true
            console.log("timer elapsed is ", this.prop_timer_delay)
            this.reactionTime = 0
            this.timer = setInterval(() => {
                this.reactionTime = this.reactionTime + 10
            }, 10)
        }, this.prop_timer_delay)
    },
    methods: {
        stopTimer() {
            clearInterval(this.timer)
            console.log("timer stopped your time is ", this.reactionTime)
            this.$emit('game_over', this.reactionTime)
        }
    }
}
</script>
<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #1587d3;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>
