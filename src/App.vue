<template>
  <div id="app">
    <div id="main">
      <Number :number="score_1p"/>
      <Number :number="score_2p"/>
      <button v-on:click="openModal">open</button>
    </div>
    <div id="overlay" v-show="showContent" v-on:click.self="closeModal">
      <div id="content">
        <p>これがモーダルウィンドウです。</p>
        <p><button v-on:click="increase">++</button></p>
      </div>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Number from './components/Number.vue'

import 'normalize.css'

export default {
  name: 'App',
  components: {
    Number,
    HelloWorld
  },
  data(){
    return {
      score_1p: 1,
      score_2p: 5,
      showContent: false
    }
  },
  methods:{
    openModal: function(){
      this.showContent = true
    },
    closeModal: function(){
      this.showContent = false
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
  height: 94vh;
  background: white;
  margin: 3vmin;
  position: relative;
  border-radius: 4%;
}

#overlay{
  /*　要素を重ねた時の順番　*/
  z-index:1;

  /*　画面全体を覆う設定　*/
  position:fixed;
  top:0;
  left:0;
  width:100%;
  height:100%;
  background-color:rgba(0,0,0,0.5);

  /*　画面の中央に要素を表示させる設定　*/
  display: flex;
  align-items: center;
  justify-content: center;

}

#content{
  z-index:2;
  width:50%;
  padding: 1em;
  background:#fff;
}
</style>
