<template>
  <div class="sc-card text-center pb-4">
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
        img{
            max-width: 100%;
        }
}
</style>