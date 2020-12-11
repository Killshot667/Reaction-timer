<template>
  <div class="block" v-if="showBlock" :style="{ margin: margin_t + 'px' + ' ' + margin_l + 'px' }" @click = "stopTimer">
      CLICK ME!!
  </div>
</template>

<script>
export default {
    props : ['delay','margin_t','margin_l'],
    data() {
        return{
        showBlock : false,
        timer : null,
        reactionTime : 0,
        }
    },
    mounted(){
        
        setTimeout(() => {
            this.showBlock = true;
            this.reactionTime = 0;
            console.log(this.reactionTime);
            this.startTimer();
           

            
        },this.delay)

    },
    methods : {
        startTimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10;
                
            }, 10);
        },
        stopTimer() {
            clearInterval(this.timer);
            console.log(this.reactionTime);
            this.showBlock = false;
            this.$emit("over",this.reactionTime);

        }
        
    }


}
</script>

<style>
.block {
    width:200px;
    border-radius: 10px;
    background: aquamarine;
    text-align: center;
    padding: 50px 0;
    border-style: solid;
    border-color:darkgreen;
    
}

</style>