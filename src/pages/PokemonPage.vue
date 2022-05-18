<template>
  <h1>Who is this Pokemon?</h1>
  <!-- TODO: img -->
  <PokemonPicture :pokemonId="4" :showPokemon="true" />
  <PokemonOptions :pokemons="pokemonArr" />
  <!-- TODO: options -->
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
    };
  },
  methods: {
    async mixPokemonArray() {
      this.pokemonArr = await getPokemonOptions();
      //console.log(this.pokemonArr);
    },
  },
  mounted() {
    this.mixPokemonArray();
  },
};
</script>

<style></style>
