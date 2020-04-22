<template lang="html">
  <div >
    <h1 > Character details</h1>
    <div id="profilePane">
      <div class="avatarImage">
         <img v-bind:src="this.character.image"></img>
      </div>
      <div class="textDescription">
        <div> Name:{{character.name}} </div>
        <div> Species:{{character.species}}</div>
        <div> Status:{{character.status}}</div>
        <div> Origin:{{character.origin.name}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name:'character-detail',
  props:['character'],
}
</script>

<style lang="css" scoped>
#profilePane{
  display:flex;
}
img{
 width:150px;
 margin:0px;
 padding:0px;
}
</style>
