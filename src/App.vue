<template>
  <div id="app">
    <AppHeader/>
    <ListDisc />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import ListDisc from './components/ListDisc.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
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
  color: #2c3e50;
  background-color:#1e2d3b ;
  padding-bottom: 50px;
  
}
</style>
