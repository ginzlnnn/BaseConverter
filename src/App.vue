<template>
  <H1>Convert Number</H1>
  <div v-for="base in [...Array(15).keys()].map(i => i + 2)" :key="base" style="display:inline-block">
    <input type="checkbox" :id="base" :value="base" v-model="checkedNum">
    <label :for="Base">Base {{ base }}</label>
  </div>
  <br>
<span>Checked Num: {{ checkedNum }}</span>
  <InputNumber :lstBase=lstNumSorted() />
</template>

<script>

import InputNumber from './components/InputNumber.vue'

export default {
  name: 'App',
  components: {
    InputNumber
  },
  data()  { return{
    checkedNum: []
  }},
  methods: {
    lstNumSorted(){
      return this.checkedNum.sort(function(a, b){
        return (a > b) ? 1 : -1;
      });
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
</style>
