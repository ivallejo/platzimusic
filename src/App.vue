<template lang="pug">
  #app
    img(src='./assets/logo.png')
    h2 Platzi Music

    select(v-model="selectedCountry")
      option(v-for="country in countries" v-bind:value="country.value") {{ country.name }}

    ul
      artist(v-for="artist in artists" :artist="artist")
      
</template>

<script>
import Artist from './components/Artist.vue'
import getArtists from './api'
export default {
  name: 'app',
  data () {
    return {
      artists : [],
      countries:[
        {value:'peru',name:'Peru'},
        {value:'argentina',name:'Argentina'},
        {value:'spain',name:'España'}
      ],
      selectedCountry:'peru'
    }
  },
  components:{
    Artist
  },
  methods:{
    refreshArtist(){
      const self = this
      getArtists(this.selectedCountry)
        .then(function(artists){
          self.artists = artists
        })
    }
  },
  mounted: function(){
    this.refreshArtist()
  },
  watch: {
    selectedCountry() {
      this.refreshArtist()
    }
  }
}
</script>

<style lang="stylus">
#app
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px

h1, h2
  font-weight normal

ul
  list-style-type none
  padding 0

li
  display inline-block
  margin 0 10px

a
  color #42b983
</style>
