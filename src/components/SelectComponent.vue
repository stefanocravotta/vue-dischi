<template>
  <div>
      <select
      v-model="selected"
       @change="$emit('changeValue', selected)"
      class="form-select " 
      aria-label="Default select example">
          <option selected value="Default">Seleziona un genere</option>
          <option value="Rock">Rock</option>
          <option value="Pop">Pop</option>
          <option value="Jazz">Jazz</option>
          <option value="Metal">Metal</option>
        </select>
  </div>
</template>

<script>
export default {
    name: "SelectComponent",
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