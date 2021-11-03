<template>
  <div class="bg-gray-200 h-full w-sreen flex">
    <Navigation />
    <div class="flex-1 p-8">
      <h1 class="text-3xl font-bold text-gray-800">POKEDEX</h1>
      <PokemonList />
    </div>
    <ProfileContainer/>
  </div>
</template>

<script>
import Navigation from '~/components/Navigation.vue'
import ProfileContainer from '~/components/ProfileContainer.vue'
export default {
  components: { Navigation, ProfileContainer },
}
</script>
