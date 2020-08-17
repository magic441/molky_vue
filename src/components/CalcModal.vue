<template>
  <div class="number">
    <h1>{{ number }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Number',
  props: {
    number: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
