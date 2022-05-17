<template>
  <header class="d-flex justify-content-between">
    <img src="https://cdn.iconscout.com/icon/free/png-256/spotify-14-437140.png" alt="">
    <select class="form-select " aria-label="Default select example">
        <option selected>Open this select menu</option>
        <option value="1">One</option>
        <option value="2">Two</option>
        <option value="3">Three</option>
    </select>
  </header>
</template>

<script>
export default {
    name: "HeaderComponent"
}
</script>

<style lang="scss" scoped>
@import "../assets/style/vars";
header{
    padding: 5px 10px;
    background-color: lighten($primary-color, 20%);
    img{
        max-width: 40px;
    }
    select{
        max-width: 100px;
    }
}
</style>