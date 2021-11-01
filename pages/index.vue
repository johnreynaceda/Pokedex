<template>
  <!-- <div class="bg-gray-200 flex justify-between h-full">
    <Navigation />
    <div class="flex-1 w-full">
      <div class="header flex space-x-2">
        <img
          src="https://www.pngarts.com/files/4/Pokeball-PNG-Image-Background.png"
          class="h-10"
          alt=""
        />
        <h1 class="text-3xl font-extrabold text-gray-800">Pokédex</h1>
      </div>
      <div class="body mt-8">
        <PokemonList />
      </div>
    </div>
    <ProfileContainer />
  </div> -->
  <div class="bg-gray-200 h-full w-sreen flex">
    <Navigation />
    <div class="flex-1 p-8">
      <h1>POKEDEX</h1>
      <PokemonList />
    </div>
    <div class="bg-red-200 w-80 rounded-l-3xl shadow-xl h-screen sticky top-0">
      <div class="content p-5">
        <div class="bg-white rounded-xl shadow-lg px-2 py-3 flex flex-col">
          <div class="flex space-x-2">
            <div class="name flex flex-col">
              <h1 class="font-bold text-gray-700">ASH KETCHUM</h1>
              <h1
                class="
                  text-sm
                  font-semibold
                  text-blue-300 text-gray-700
                  leading-3
                "
              >
                Level 100
              </h1>
            </div>
            <img
              src="https://cdn2.bulbagarden.net/upload/thumb/9/91/Ash_M23.png/150px-Ash_M23.png"
              alt=""
              class=""
            />
          </div>

          <div
            class="
              mt-5
              bg-blue-400
              rounded-lg
              flex
              justify-center
              items-center
              py-2
              text-white
              shadow-lg
            "
          >
            <span>Edit Profile</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navigation from '~/components/Navigation.vue'
import ProfileContainer from '~/components/ProfileContainer.vue'
export default {
  components: { Navigation, ProfileContainer },
}
</script>
