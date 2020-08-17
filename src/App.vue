<template>
  <div id="app">
    <div id="main">
      <DispNumber :number="score_1p" @changeCalcModal="changeCalcModal($event)"/>
      <DispNumber :number="score_2p" @changeCalcModal="changeCalcModal($event)"/>
      <CalcModal :showContent="showContent" @changeCalcModal="changeCalcModal($event)"/>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import DispNumber from './components/DispNumber.vue'
import CalcModal from './components/CalcModal.vue'

import 'normalize.css'

export default {
  name: 'App',
  components: {
    DispNumber,
    HelloWorld,
    CalcModal
  },
  data(){
    return {
      score_1p: 25,
      score_2p: 30,
      showContent: false
    }
  },
  methods:{
    changeCalcModal: function(state){
      this.showContent = state
    },
    increase: function(){
      this.score_1p += 1
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

</style>
