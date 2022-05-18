<template>
  <h1 v-if="!pokemon">Wait a moment please...</h1>
  <div v-if="pokemon">
    <h1>Who is this Pokemon?</h1>
    <!-- TODO: img -->
    <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon" />
    <PokemonOptions :pokemons="pokemonArr" @selection="checkAnswer($event)" />
    <!-- TODO: options -->
  </div>
</template>

<script>
import PokemonOptions from "../components/PokemonOptions";
import PokemonPicture from "../components/PokemonPicture";
import getPokemonOptions from "../helpers/getPokemonOptions";

getPokemonOptions();

export default {
  components: { PokemonPicture, PokemonOptions },
  data() {
    return {
      pokemonArr: [],
      pokemon: null,
      showPokemon: false,
    };
  },
  methods: {
    async mixPokemonArray() {
      this.pokemonArr = await getPokemonOptions();

      const rndInt = Math.floor(Math.random() * 4);
      this.pokemon = this.pokemonArr[rndInt];
    },
    checkAnswer(pokemonId) {
      this.showPokemon = true;
      console.log("check Answer", pokemonId);
    },
  },
  mounted() {
    this.mixPokemonArray();
  },
};
</script>

<style></style>
