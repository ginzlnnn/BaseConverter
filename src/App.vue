<template>
  <h1>Convert Number</h1>
  <div v-for="base in [...Array(35).keys()].map(i => i + 2)" :key="base" style="display:inline-block; margin:5px">
    <input type="checkbox" :id="base" :value="base" v-model="selectedBase">
    <label :for="base"> Base {{ base }}</label>
  </div>
  <br>
  <br>
<span><b>Selected Base : </b>{{ selectedBase }}</span>
  <ResultPanel :lstBase=lstNumSorted() />
</template>

<script>

import ResultPanel from './components/ResultPanel.vue'

export default {
  name: 'App',
  components: {
    ResultPanel
  },
  data()  { return{
    selectedBase: [2, 8, 10, 16]
  }},
  methods: {
    lstNumSorted(){
      return this.selectedBase.sort(function(a, b){
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
