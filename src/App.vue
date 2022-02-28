<template>
  <div id="app">
    <MyHeader @selectedGenreEvt="setSelectedGenre" :genresList="genresList"/>
    <MyMain @genresReady="setGenres" :selectedGenre="selectedGenre"/>
  </div>
</template>

<script>
import MyHeader from './components/MyHeader.vue'
import MyMain from './components/MyMain.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
    MyMain
  },
  data(){
    return{
      genresList:[],
      selectedGenre:''
    }
  },
  methods:{
    setGenres(genresListEvt){
      this.genresList=genresListEvt;
    },
    setSelectedGenre(selectedGenreEvt){
      this.selectedGenre=selectedGenreEvt;
      
    }
  }
}
</script>

<style lang="scss">

</style>
