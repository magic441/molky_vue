<template>
  <div id="overlay" v-show="showContent" v-on:click.self="closeModal">
    <div id="content">
      <p id="test">これがモーダルウィンドウです。</p>
      <p><button>++</button></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CalcModal',
  props: {
    showContent: Boolean
  },
  methods: {
    closeModal(){
      this.$emit('changeCalcModal', false);
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
  height: 80%;
  width: 80%;
  background: white;
  position: relative;
  border-radius: 4%;
  background:#fff;
  /*opacity: 0.8%;*/
  position: relative;
}
#test{
  position: absolute;
  transform:rotate(90deg);
  top:0;
  height:100%;
  width:50%;
  margin:0;


}
</style>
