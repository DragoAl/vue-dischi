<template>
  <div id="app">
    <AppHeader 
      :filteredTypes="GenreArr"
      @GenreSelect ='SelectedGenre'
      />
    <ListDisc @genreReady = 'getGenreArr' />
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
  },
  data() {
    return {
      GenreArr: [],
      selectOpt : 'all'
    }
      
  },
  methods : {
    SelectedGenre(genere) {
      this.selectOpt = genere;
    },
    getGenreArr (generes) {
      this.GenreArr = generes
    }
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
