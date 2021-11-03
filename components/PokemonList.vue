<template>
 
  <div class="">
    <div class="flex justify-end">
      <input type="text" class="h-12 w-96 rounded-lg shadow-lg px-2 focus:outline-none focus:border-0" placeholder="Name or Number">
    </div>
    <ul
      role="list"
      class="
        grid grid-cols-1
        gap-4
        sm:grid-cols-2
        md:grid-cols-3
        lg:grid-cols-4
      "
    >
      <PokemonContainer @openContainer="openPokemon()" 
        v-for="(pokemon, index) in pokemons"
        :key="index"
        :imgIndex="index + 1"
        :pokemon="pokemon"
      />

      <!-- More people... -->
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pokemons: [],
    }
  },
  methods: {
 
    async getPokemons() {
      this.pokemons = await this.$axios
        .get('https://pokeapi.co/api/v2/pokemon?limit=50')
        .then((res) => {
          return res.data.results
        })
        .catch((err) => {
          console.log(err)
        })
    },
  },
  mounted() {
    this.getPokemons()
  },
}
</script>
