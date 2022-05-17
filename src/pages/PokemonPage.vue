<template>
  <h1>Who is this Pokemon?</h1>
  <!-- TODO: img -->
  <PokemonPicture />
  <PokemonOptions />
  <!-- TODO: options -->
</template>

<script>
import PokemonOptions from "../components/PokemonOptions";
import PokemonPicture from "../components/PokemonPicture";
export default {
  components: { PokemonPicture, PokemonOptions },
};
</script>

<style></style>
