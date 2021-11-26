<template>
  <div id="app">
    <ListDisc />
  </div>
</template>

<script>
import ListDisc from './components/ListDisc.vue'

export default {
  name: 'App',
  components: {
    ListDisc
  }
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  
}
</style>
