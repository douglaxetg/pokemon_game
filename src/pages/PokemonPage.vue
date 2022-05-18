<template>
  <h1 v-if="!pokemon">Wait a moment please...</h1>

  <div v-else>
    <h1>Who is this Pokemon?</h1>
    <!-- TODO: img -->
    <PokemonPicture :pokemonId="pokemon.id" :showPokemon="showPokemon" />
    <PokemonOptions :pokemons="pokemonArr" @selection="checkAnswer" />
    <!-- TODO: options -->
    <template v-if="showAnswer">
      <button @click="newGame">New Game</button>
      <h2>{{ message }}</h2>
    </template>
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
      showAnswer: false,
      message: "",
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
      this.showAnswer = true;
      if (pokemonId === this.pokemon.id) {
        this.message = `Correct, it's ${this.pokemon.name}`;
      } else {
        this.message = `Oops, it was ${this.pokemon.name}`;
      }
    },
    newGame() {
      (this.pokemonArr = []),
        (this.showPokemon = false),
        (this.showAnswer = false),
        this.mixPokemonArray();
      this.pokemon = null;
    },
  },
  mounted() {
    this.mixPokemonArray();
  },
};
</script>

<style></style>
