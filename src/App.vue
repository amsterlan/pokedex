<template>
  <div id="app">

    <div class="column is-half is-offset-one-quarter">
      <div v-for="(poke,index) in pokemons" :key="index">
      <PokemonV :name="poke.name" :url="poke.url" :num="index+1"/>
    </div>
    
    </div>
  </div>
</template>

<script>
  //import { stringLiteral } from '@babel/types';
  import axios from 'axios';
  import PokemonV from './components/PokemonV.vue';
  export default {
    name: 'App',
    data(){
    return {
      pokemons: []
    }
  },
  created: function(){
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0").then(res=>{
      console.log("pegou a lista de pokemons");
      this.pokemons = res.data.results;
    })
  },
  components: {
    PokemonV,
}
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
