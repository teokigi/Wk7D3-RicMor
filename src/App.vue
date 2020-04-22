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
      <character-list></character-list>
    </div>
  </div>
</body>
</template>

<script>

import CharacterList from './components/CharacterList.vue'


export default {
  name: 'App',
  data(){
    return {
      rmShow: null
    }
  },
  components:{
    'character-list': CharacterList
  },
  mounted(){
    fetch('https://rickandmortyapi.com/api/character/')
    .then(res => res.json())
    .then(data => this.rmShow = data)
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
TODO - Display a list of character names.
TODO - Add a click event to the list item which should then render more detail about that character (name, species, status).
TODO - Use reusable components.
     Extensions
TODO - Instead of rendering a list, populate a dropdown with all of the characters names.
TODO - Add a change event to the select that renders information about the selected character.
     Advanced Extensions
TODO - Add the characters image and origin name to the character detail component.
TODO - Add a search bar to the page so that when a user enters the characters name the character detail component renders. Try to achieve this without the
     Planning
     Draw a diagram of your files, detailing:
TODO - the data, props, components and methods for each component.
TODO - the flow of data throughout the application.
-->
