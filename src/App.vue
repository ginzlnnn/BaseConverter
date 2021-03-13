<template>
  <H1>Convert Number</H1>
  <InputNumber :lstBase=[2,8,10,12,16] />
</template>

<script>

import InputNumber from './components/InputNumber.vue'

export default {
  name: 'App',
  components: {
    InputNumber
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
</style>
