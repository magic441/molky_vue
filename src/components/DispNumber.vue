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
  display: flex;
  align-items: center;
  justify-content: center;
}
span{
  font-size:20vh;
  writing-mode: vertical-rl;
  text-orientation: sideways;
  transform:rotate(180deg);
}
</style>
