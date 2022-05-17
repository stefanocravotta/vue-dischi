<template>
  <div>

    <HeaderComponent />

    <MainComponent />

  </div>
</template>

<script>
import axios from 'axios';
import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent
},
  data(){
    return{
      baseUrl: "https://flynn.boolean.careers/exercises/api/array/music",

    }
  },
  mounted(){
    this.getAPI();
  },
  methods: {
    getAPI(){
      axios.get(this.baseUrl)
      .then(r =>{
        console.log(r.data);
      })
    }
  },
}
</script>

<style lang="scss">
@import "./assets/style/global";
@import "./assets/style/vars";
</style>
