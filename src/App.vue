<template>
<!-- AppHeader e ListDisc fratelli si collegano tra di loro passando i dati attraverso il padre(app) -->
  <div id="app">
    <AppHeader 
      :filteredTypes= "GenreArr"
      @GenreSelect = 'SelectedGenre'
      :filteredArtist= "ArtistArr"
      @ArtistSelect= 'SelectedArtist' 
      />
    <ListDisc 
      :selectOpt= 'genere'
      :selectArtist= 'artista'
      @genreReady = 'getGenreArr'
      @artistReady= 'getArtistArr'
    />
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
      genere : 'all',
      ArtistArr:[],
      artista : 'all'
    }
  },

  methods : {
    // funzione che ricevde il valore dal select e lo copia in genere che comunica l'ele selezionato a listDisc
    SelectedGenre(genere) {
      this.genere = genere;
    },
    // copio in GenreArr l'array dei generi che si trova in ListDisc 
    getGenreArr (generes) {
      this.GenreArr = generes
    },
    getArtistArr(artists) {
      this.ArtistArr = artists;
    },
    SelectedArtist(artista) {
      this.artista = artista;
    },
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
  height: 1000px;
  // padding-bottom: 50px;
}
</style>
