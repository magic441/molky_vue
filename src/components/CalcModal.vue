<template>
  <div id="overlay" v-show="showContent" v-on:click.self="closeModal">
    <div id="content">
      <div id="panel">
        <div id="line">
          <div id="num" v-bind:class="{active: isActive_4}" v-on:click="changeNum(4)"><span>+4</span></div>
          <div id="num" v-bind:class="{active: isActive_3}" v-on:click="changeNum(3)"><span>+3</span></div>
          <div id="num" v-bind:class="{active: isActive_2}" v-on:click="changeNum(2)"><span>+2</span></div>
          <div id="num" v-bind:class="{active: isActive_1}" v-on:click="changeNum(1)"><span>+1</span></div>
        </div>
        <div id="line">
          <div id="num" v-bind:class="{active: isActive_8}" v-on:click="changeNum(8)"><span>+8</span></div>
          <div id="num" v-bind:class="{active: isActive_7}" v-on:click="changeNum(7)"><span>+7</span></div>
          <div id="num" v-bind:class="{active: isActive_6}" v-on:click="changeNum(6)"><span>+6</span></div>
          <div id="num" v-bind:class="{active: isActive_5}" v-on:click="changeNum(5)"><span>+5</span></div>
        </div>
        <div id="line">
          <div id="num" v-bind:class="{active: isActive_12}" v-on:click="changeNum(12)"><span>+12</span></div>
          <div id="num" v-bind:class="{active: isActive_11}" v-on:click="changeNum(11)"><span>+11</span></div>
          <div id="num" v-bind:class="{active: isActive_10}" v-on:click="changeNum(10)"><span>+10</span></div>
          <div id="num" v-bind:class="{active: isActive_9}" v-on:click="changeNum(9)"><span>+9</span></div>
        </div>
        <div id="line">
          <div id="func" v-on:click="calcScore"><span>OK</span></div>
          <div id="num" v-bind:class="{active: isActive_25}" v-on:click="to25"><span>25</span></div>
          <div id="num" v-bind:class="{active: isActive_0}" v-on:click="to0"><span>0</span></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalcModal',
  props: {
    showContent: Boolean,
    score: Number
  },
  data () {
    return {
      calcnum: 0,
      mode: 0
    }
  },
  computed:{
    isActive_1: function(){
      if(this.calcnum == 1){
        return true
      }
      return false
    },
    isActive_2: function(){
      if(this.calcnum == 2){
        return true
      }
      return false
    },
    isActive_3: function(){
      if(this.calcnum == 3){
        return true
      }
      return false
    },
    isActive_4: function(){
      if(this.calcnum == 4){
        return true
      }
      return false
    },
    isActive_5: function(){
      if(this.calcnum == 5){
        return true
      }
      return false
    },
    isActive_6: function(){
      if(this.calcnum == 6){
        return true
      }
      return false
    },
    isActive_7: function(){
      if(this.calcnum == 7){
        return true
      }
      return false
    },
    isActive_8: function(){
      if(this.calcnum == 8){
        return true
      }
      return false
    },
    isActive_9: function(){
      if(this.calcnum == 9){
        return true
      }
      return false
    },
    isActive_10: function(){
      if(this.calcnum == 10){
        return true
      }
      return false
    },
    isActive_11: function(){
      if(this.calcnum == 11){
        return true
      }
      return false
    },
    isActive_12: function(){
      if(this.calcnum ==12){
        return true
      }
      return false
    },
    isActive_0: function(){
      if(this.calcnum ==0 && this.mode ==1){
        return true
      }
      return false
    },
    isActive_25: function(){
      if(this.calcnum ==25 && this.mode ==1){
        return true
      }
      return false
    },

  },
  methods: {
    closeModal(){
      this.$emit('changeCalcModal', false)
      this.calcnum = 0
      this.mode = 0
    },
    changeNum(int){
      this.calcnum = int
      this.mode = 0
    },
    to25(){
      this.mode = 1
      this.calcnum = 25
    },
    to0(){
      this.mode = 1
      this.calcnum = 0
    },
    calcScore(){
      switch(this.mode){
        case 1 :
          this.$emit('changeScore', this.calcnum)
          this.calcnum = 0
          this.mode = 0
          break
        default :
          let tmp = 0
          tmp = this.score + this.calcnum
          if (tmp > 50){
            tmp = 25
          }
          this.$emit('changeScore', tmp)
          this.calcnum = 0
          this.mode = 0
          break
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
  height: 60vh;
  width: 60vh;
  background: white;
  border-radius: 4%;
  opacity: 0.95;
  position: relative;
}
#panel{
  height: 90%;
  width: 90%;
  top: 5%;
  left: 5%;
  background:white;
  position: relative;
  opacity: 0.95;
  border: 1px solid;
  margin: 0;
  display: flex;
  flex-direction: row;
  justify-content: start;
  /* flex-wrap: nowrap; */
}

#line{
  width: 25%;
  height: 100%;
}

#num{
  height: 25%;
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 0.5px solid;
  box-sizing: border-box;
  border-radius: 1%;
}
#num > span {
  writing-mode: vertical-rl;
  text-orientation: sideways;
  align-items: center;
  display: flex;
  transform:rotate(180deg);
  font-size:5vh;
}
#func{
  height: 50%;
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 0.5px solid;
  box-sizing: border-box;
  border-radius: 1%;
}
#func > span {
  writing-mode: vertical-rl;
  text-orientation: sideways;
  align-items: center;
  display: flex;
  transform:rotate(180deg);
  font-size:5vh;
}
#test{
  position: absolute;
  transform:rotate(180deg);
  top:0;
  height:100%;
  width:50%;
  margin:0;
  writing-mode: vertical-rl;
  text-orientation: sideways;
}

.active{
  /* background: gainsboro; */
  background: #E7FBFF;
}
</style>
