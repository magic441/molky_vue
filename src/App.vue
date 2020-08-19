<template>
  <div id="app">
    <div id="main">
      <DispNumber :number="score_1p" @changeCalcModal="changeCalcModal($event, true)"/>
      <DispNumber :number="score_2p" @changeCalcModal="changeCalcModal($event, false)"/>
      <img id="popup" src="/img/svgs/popup.svg">
      <CalcModal :showContent="showContent" :score="score_tmp" @changeCalcModal="changeCalcModal($event, is1p)" @changeScore="changeScore($event)"/>
    </div>
  </div>
</template>

<script>
import DispNumber from './components/DispNumber.vue'
import CalcModal from './components/CalcModal.vue'

import 'normalize.css'

export default {
  name: 'App',
  components: {
    DispNumber,
    CalcModal
  },
  data(){
    return {
      score_1p: 0,
      score_2p: 0,
      score_tmp: 0,
      showContent: false,
      is1p: true
    }
  },
  methods:{
    changeCalcModal: function(state, bool){
      this.showContent = state
      this.is1p = bool
      if(this.is1p){
        this.score_tmp = this.score_1p
      }
      else{
        this.score_tmp = this.score_2p
      }
    },
    changeScore: function(score){
      if(this.is1p){
        this.score_1p = score
      }
      else{
        this.score_2p = score
      }
      this.showContent = false
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
  background: #D8FFA6;
  height: 100%;
  width: 100%;
  position: absolute;
}

#main {
  height: 96%;
  background: white;
  top: 2%;
  margin-left: 2%;
  margin-right: 2%;
  position: relative;
  border-radius: 4%;
}

#popup{
  width: 5vw;
  position: absolute;
  top: 10vh;
  right: 3vw;
  transform:rotate(-90deg);
}
</style>
