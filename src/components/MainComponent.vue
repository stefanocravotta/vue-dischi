<template>
  <main>
      <div class="container d-flex flex-wrap">
          <CardComponent
           v-for= "(albumCard,index) in albumCards" 
           :key="`album-card-${index}`"
           :albumCard = "albumCard"/>
      </div>
  </main>
</template>

<script>
import axios from 'axios';
import CardComponent from './CardComponent.vue';
export default {
    name: "MainComponent",
    components: {
    CardComponent
},
  data(){
    return{
      baseUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      albumCards: []

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
      })
    }
  },
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars";
main{
    background-color: $primary-color;
    .container{
        padding: 40px 0;
    }
}
</style>