<template>
  <body id="app">
  <div id="divPage">

    <noscript>
      <strong>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work properly without JavaScript enabled. Please enable it to continue.</strong>
    </noscript>

    <div id="divHeader">
      <h1>Rick and Morty</h1>
    </div>

    <div id="divBody">
      <div> Character List </div>
        <label for="charcter_select">Select a character:</label>
        <select id="character_select" v-model="selectedCharacter">
          <option disabled value="">Select a country</option>
           <character-list v-for="character in rmShow" :character="character">
           </character-list>
         </option>
     </select>
      <character-detail v-if="selectedCharacter" :character="selectedCharacter"></character-detail>
    </div>

  </div>
</body>
</template>

<script>

import CharacterList from './components/CharacterList.vue'
import {eventBus} from './main.js'
import CharacterDetail from './components/CharacterDetail.vue'

export default {
  name: 'App',
  data(){
    return {
      rmShow: null,
      selectedCharacter: null,
    }
  },
  components:{
    'character-list':   CharacterList,
    'character-detail': CharacterDetail,

  },
  mounted(){
    fetch('https://rickandmortyapi.com/api/character/')
    .then(res => res.json())
    .then(data => this.rmShow = data.results)

    eventBus.$on('character-info',character => this.selectedCharacter = character)
  },
}
</script>

<style>
body{
  width:100%;
  height:100%;
  margin:0px;
  padding:0px;
  display:flex;
  background-color:lightgreen;
  justify-content:center;
  align=content:center;
  border-style:solid;
}
#divPage{
  width:100%;
  border-color:blue;
  border-style:dotted;

}
#divHeader{
  width:100%;
  border-color:red;
  border-style:none;
  border-bottom-style:double;
  text-align:center;
}
div{
  border-style:solid;
}
</style>
<!-- MVP
DONE - Display a list of character names.
DONE - Add a click event to the list item which should then render more detail about that character (name, species, status).
WUT? - Use reusable components.
     Extensions
DONE - Instead of rendering a list, populate a dropdown with all of the characters names.
TODO - Add a change event to the select that renders information about the selected character.
     Advanced Extensions
TODO - Add the characters image and origin name to the character detail component.
TODO - Add a search bar to the page so that when a user enters the characters name the character detail component renders. Try to achieve this without the
     Planning
     Draw a diagram of your files, detailing:
TODO - the data, props, components and methods for each component.
TODO - the flow of data throughout the application.
-->
