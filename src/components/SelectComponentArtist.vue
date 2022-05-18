<template>
  <div>
      <select
      v-model="selected"
       @change="$emit('changeArtists', selected)"
      class="form-select " 
      aria-label="Default select example">
          <option selected value="Default">Seleziona un artista</option>
          <option value="Bon Jovi">Bon Jovi</option>
          <option value="Queen">Queen</option>
          <option value="Sting">Sting</option>
          <option value="Iron Maiden">Iron Maiden</option>
          <option value="Eric Clapton">Eric Clapton</option>
          <option value="Deep Purple">Deep Purple</option>
          <option value="Metallica">Metallica</option>
          <option value="Dave Weckl">Dave Weckl</option>
          <option value="Michael Jacjson">Michael Jacjson</option>
        </select>
  </div>
</template>

<script>
export default {
    name: "SelectComponentArtist",
    data(){
        return{
        selected: 'Default',
        }
        
    },
}
</script>

<style lang="scss" scoped>
select{
        max-width: 200px;
    }
</style>