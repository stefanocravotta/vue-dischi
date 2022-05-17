<template>
  <header class="d-flex justify-content-between">
    <img src="https://cdn.iconscout.com/icon/free/png-256/spotify-14-437140.png" alt="">
    <select class="form-select " aria-label="Default select example">
        <option selected>Seleziona un genere</option>
        <option value="1">Rock</option>
        <option value="2">Pop</option>
        <option value="3">Jazz</option>
        <option value="4">Metal</option>
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
    height: 60px;
    padding: 10px 10px;
    background-color: lighten($primary-color, 5%);
    img{
        max-width: 40px;
    }
    select{
        max-width: 200px;
    }
}
</style>