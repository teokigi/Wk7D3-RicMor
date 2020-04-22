<template lang="html">
  <div >
    <h1 > Character details</h1>
    <div> {{character.name}} </div>
    <div> {{character.species}}</div>
    <div> {{character.status}}</div>
  </div>
</template>

<script>
export default {
  name:'character-detail',
  props:['character'],
}
</script>

<style lang="css" scoped>
</style>
