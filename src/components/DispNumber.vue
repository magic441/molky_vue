<template>
  <div class="number">
    <span v-on:click="openModal">{{ number }}</span>
  </div>
</template>

<script>
export default {
  name: 'Number',
  props: {
    number: Number
  },
  methods: {
    openModal(){
      this.$emit('changeCalcModal', true);
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.number{
  position: relative;
  height: 50%;
}
span{
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: auto;
  width: 20vh;
  height: 20vh;
  font-size:20vh;
  /* transform:rotate(90deg); */
}
</style>
