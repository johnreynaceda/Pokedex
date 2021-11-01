<template>
  <!-- <div class="bg-blue-300">
    <li class="h-56 col-span-1 flex flex-col text-center bg-white shadow">
      <img
        :src="image"
        class="absolute -right-8 flex-shrink-0 -top-14 h-48"
        alt=""
      />
      <div class="bg-white flex-1 text-white h-20">sd</div>
      <div class="bg-blue-300 h-56 ml-3 rounded-tl-full">
        <div class="pokename mt-12 flex flex-col justify-end w-full">
          <h1>#{{ imgIndex + 1 }}1</h1>
          <h1>{{ pokemon.name }}</h1>
        </div>
      </div>
    </li>
  </div> -->
  <li class="col-span-1 flex flex-col rounded-lg">
    <div class="h-28 relative">
      <img
        :src="image"
        class="absolute top-10 left-1/2 right-1/2 h-32"
        alt=""
      />
    </div>

    <div
      class="
        bg-gradient-to-t
        from-blue-400
        to-green-300
        shadow-lg
        h-48
        rounded-3xl
        flex flex-col
      "
    >
      <div class="p-2 font-bold text-white">#{{ imgIndex + 1 }}</div>
      <div
        class="p-2 font-bold text-2xl text-gray-800 uppercase flex justify-end"
      >
        {{ pokemon.name }}
      </div>

      <div class="type p-2">
        <h1 class="px-5 rounded-xl bg-white">Grass</h1>
        <h1 class="px-5 rounded-xl bg-white">Water</h1>
      </div>
    </div>
  </li>
</template>

<script>
export default {
  props: ['pokemon', 'imgIndex'],
  data() {
    return {
      image:
        'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/' +
        this.imgIndex +
        '.png',
    }
  },
}
</script>
