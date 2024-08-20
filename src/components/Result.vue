<template>
  <p>Reaction time {{score}} ms</p>
  <p class="rank">{{rank}}</p>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){    // وقتی که کامپوننت داخل دام ایجاد شد یکسری قابلیت ها استفاده بشن
    if(this.score<250){
        this.rank = "nice, it was fast"
    }
    else if(this.score<400){
        this.rank = "not bad..."
    }
    else{
        this.rank = "you are to slow..."
    }
    }

}
</script>

<style>
.rank{
    font-size: 1.4em;
    color: #0faf78;
    font-weight: bold;
}
</style>