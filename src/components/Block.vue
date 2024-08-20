<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
    props:['delay'],
    data(){
        return{
            showBlock: false,
            timer: null,
            reactionTimer: 0
        }
    },
    mounted(){
       // console.log('success')
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
        }, this.delay);
    },
    updated(){
       // console.log("component update")
    },
    unmounted(){
       // console.log("component unmounted")
    },
    methods: {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTimer += 10
            }, 10);
        },
        stopTimer(){
            clearInterval(this.timer)
            console.log(this.reactionTimer)
            this.$emit('end', this.reactionTimer) //برای فرستادن دیتا از فرزند به والد

        }
    }
}
</script>

<style>
.block{
    width: 400px;
    color: white;
    background-color: rgb(124, 206, 2);
    text-align: center;
    margin: 40px auto;
    padding: 100px 0;
    border-radius: 20px;
    cursor: pointer;
}
</style>