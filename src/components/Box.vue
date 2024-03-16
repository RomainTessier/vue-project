<template>
  <div class="box" v-if="showbox" @click="endTimer" >
    Clik me
  </div>
</template>

<script>
 export default {
    props: ['delay'],
    data(){
      return{
        timer:0,
        showbox: false,
        reactionTime: 0
      }
    },
    mounted(){
      setTimeout(() => {
        this.showbox = true
        this.startTimer()
      }, this.delay)
    },
    methods:{
      startTimer(){
        this.timer = setInterval(() => {
          this.reactionTime+=10
        },10)
      },
      endTimer(){
        clearInterval(this.timer)
        this.$emit('end', this.reactionTime)
      }    
    }
  }
</script>

<style>
  .box{
    width: 20vw;
    height: 20vh;
    background-color: #7dc76e;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 20px;
    color: #fff;
  }
</style>