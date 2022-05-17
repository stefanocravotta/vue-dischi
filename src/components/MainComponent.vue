<template>
  <main>
      <div 
      v-if="isLoading"
      class="container d-flex flex-wrap">
          <CardComponent
           v-for= "(albumCard,index) in albumCards" 
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
export default {
    name: "MainComponent",
    components: {
    CardComponent,
    LoaderComponent
},
  data(){
    return{
      baseUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      albumCards: [],
      isLoading: false

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
        console.log(this.albumCards);
        this.isLoading= true
      })
    }
  },
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars";
main{
    background-color: $primary-color;
    min-height: calc(100vh - 60px);
    .container{
        padding: 40px 0;
    }
}
</style>