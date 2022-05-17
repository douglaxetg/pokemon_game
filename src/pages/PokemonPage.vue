<template>
  <h1>Who is this Pokemon?</h1>
  <!-- TODO: img -->
  <PokemonPicture :pokemonId="4" :showPokemon="true" />
  <PokemonOptions />
  <!-- TODO: options -->
</template>

<script>
import PokemonOptions from "../components/PokemonOptions";
import PokemonPicture from "../components/PokemonPicture";
import getPokemonOptions from "../helpers/getPokemonOptions";

console.log(getPokemonOptions());

export default {
  components: { PokemonPicture, PokemonOptions },
};
</script>

<style></style>
