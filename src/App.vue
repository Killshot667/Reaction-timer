<template>
<h1>
  Reaction Timer</h1>
  <h4 class="text-muted">Test your reflexes!</h4>
  <br>
  <button class="btn btn-primary" type="button" data-toggle="collapse" style="margin-bottom:10px" data-target="#collapseExample" aria-expanded="false" aria-controls="collapseExample">
    Info
  </button>

  <br>
  
  <div class="collapse" id="collapseExample">
  <div class="card card-body border border-primary" style="width:50%; margin:auto; background-color:#03fcec">
   This is a raction timer to test your reaction speed. Once you press start, after a few seconds(which is random by the way), a box will appear in a random location in the red box below,which you will
  have to click . The faster you click, the better. Happy clicking!! 
  </div>
  </div>

  <br>
  <button type="button" class="btn btn-outline-success btn-lg starting" @click="start" :disabled="isPlaying">{{readyMessage}}</button>

  <br><br>
  <Result v-if="showResult" :score="score" />

  <div class="card body" style="height:30rem;width:80%;margin:auto;border-color:#fc0318;">
    <Block v-if="isPlaying" :delay="delay" :margin_l="margin_l" :margin_t="margin_t" @over = "gameOver"/>
    
  </div>
  
  
  <br>

</template>

<script>

import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  components: {
    Block,Result,
  },
  data() {
    return {
      isPlaying : false,
      delay : 2000,
      readyMessage : "Start",
      margin_l : 330,
      margin_t : 5,
      showResult : false,
      score : null,

    }
  },
  methods : {
    start(){
      this.delay = 2000 + Math.random()*4000;
      this.isPlaying = true;
      this.showResult = false;
      this.readyMessage = "Get Ready"
      this.margin_t = Math.floor(5+Math.random()*330)
      this.margin_l = Math.floor(5+Math.random()*990)
    },
    gameOver(reactionTime){

      this.score = reactionTime;
      this.showResult = true;
      this.isPlaying = false;

    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button.starting:disabled {
  opacity: 0.2;
  cursor: not-allowed;
}
 
</style>
