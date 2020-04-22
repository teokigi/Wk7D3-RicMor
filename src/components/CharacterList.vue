<template lang="html">
  <option :value="character" v-on:selected="handleClick">{{character.name}}</option>
</template>

<script>

import {eventBus} from '../main.js'

export default {
  name:'character-list',
  props:['character'],
  methods: {
    handleClick(){
      eventBus.$emit('character-info', this.character)
    },
  }
}
</script>

<style lang="css" scoped>

</style>
