<template>
  <div>

  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  components: {
    
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

</style>
