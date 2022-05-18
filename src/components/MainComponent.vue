<template>
  <main>
      <header class="d-flex justify-content-between">
        <img src="https://cdn.iconscout.com/icon/free/png-256/spotify-14-437140.png" alt="">
        <div class="d-flex">
          <SelectComponent class="me-2" @changeValue='albumToSearch' />
          <SelectComponentArtist @changeArtists='artistToSearch' />
        </div>
      </header>
      <div 
      v-if="isLoading"
      class="container card-container d-flex flex-wrap">
          <CardComponent
           v-for= "(albumCard,index) in printAlbumFiltered" 
           :key="`album-card-${index}`"
           :albumCard = "albumCard"/>
      </div>
      <div class="text-center py-5" v-else>
          <LoaderComponent titleLoading= "Sto caricando gli Album"/>
      </div>
  </main>
</template>

<script>
import axios from 'axios';
import CardComponent from './CardComponent.vue';
import LoaderComponent from './LoaderComponent.vue';
import SelectComponent from './SelectComponent.vue';
import SelectComponentArtist from './SelectComponentArtist.vue';
export default {
    name: "MainComponent",
    components: {
    CardComponent,
    LoaderComponent,
    SelectComponent,
    SelectComponentArtist
},
  data(){
    return{
      baseUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      albumCards: [],
      isLoading: false,
      choiseValue: "",
      choiseArtist:""
    }
  },
  mounted(){
    this.getAPI();
    
  },
  methods: {
    getAPI(){
      axios.get(this.baseUrl)
      .then(r =>{
        this.albumCards = r.data.response;
        this.isLoading= true
      })
    },
    albumToSearch(selectValue){
      this.choiseValue = selectValue;
    },
    artistToSearch(selectValue){
      this.choiseArtist = selectValue;
    },
  },
  computed: {
    printAlbumFiltered(){

      let albumFiltered = [];

      if(this.choiseArtist === "Default" && this.choiseValue === "Default"){
        albumFiltered = this.albumCards
      }else if(this.choiseValue === "Default" && this.choiseArtist !== "Default"){
        albumFiltered = this.albumCards.filter(album =>{
          return album.author.includes(this.choiseArtist)
        })
      }else if(this.choiseArtist === "Default" && this.choiseValue !== "Default"){
        albumFiltered = this.albumCards.filter(album =>{
          return album.genre.includes(this.choiseValue)
        })
      }else if(this.choiseArtist !== "Default" && this.choiseValue !== "Default"){
        albumFiltered = this.albumCards.filter(album =>{
          return (album.author.includes(this.choiseArtist) && album.genre.includes(this.choiseValue))
        })
      }
      return albumFiltered
    },
    searchAlbum(){
      let albumFiltered = [];

      if(this.choiseValue === "Default"){
        albumFiltered = this.albumCards
      }else{
        albumFiltered = this.albumCards.filter(album =>{
          return album.genre.includes(this.choiseValue)
        })
      }
      return albumFiltered
    }
  }
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars";

main{
    background-color: $primary-color;
    min-height: calc(100vh);
    header{
    height: 60px;
    padding: 10px 10px;
    background-color: lighten($primary-color, 5%);
    img{
        max-width: 40px;
        }
    }
    .card-container{
        padding: 40px 0;
        min-height: calc(100% - 60px);
    }
}
</style>