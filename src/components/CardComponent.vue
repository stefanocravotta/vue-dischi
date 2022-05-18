<template>
  <div class="sc-card text-center">
              <img class="mb-3" :src="albumCard.poster">
              <h4>{{albumCard.title}}</h4>
              <h5>{{albumCard.author}}</h5>
              <h6>{{albumCard.year}}</h6>
          </div>
</template>

<script>
export default {
    name: "CardComponent",
    props: {
        albumCard : Object
    }
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars";

.sc-card{
        width: calc(100% / 5 - 20px);
        margin: 10px 10px;
        padding: 10px;
        background-color: lighten($primary-color, 5%);
        color: white;
        box-shadow: 0 5px 5px rgba(0, 0, 0, .3);
        cursor: pointer;
        transition: all .3s;
        &:hover{
            box-shadow: 0 10px 10px rgba(0, 0, 0, .3);
            scale: 105%;
        }
        img{
            max-width: 100%;
        }
        h4{
            margin-bottom: 25px;
        }
        h5,h6{
            color: rgba(211, 211, 211, 0.377);
        }
}
</style>