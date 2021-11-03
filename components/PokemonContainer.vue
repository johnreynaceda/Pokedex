<template>
 
  <nuxt-link :to="getUrl"  class="col-span-1 cursor-pointer flex flex-col rounded-lg">
    <div class="h-28 relative">
      <img
        :src="image"
        class="absolute top-10 left-1/2 right-1/2 h-32"
        alt=""
      />
    </div>

    <div
      class="
       bg-gradient-to-t from-gray-200 via-blue-400 to-green-500
        shadow-lg
        h-48
        rounded-3xl
        flex flex-col
      "
    >
      <div class="p-2 font-bold text-white" >#{{ imgIndex }} </div>
      <div
        class="p-2 font-bold text-2xl text-gray-800 uppercase flex justify-end"
      >
        {{ pokemon.name }}
      </div>

      <div class="type flex space-x-2 px-2 mt-2">
        <h1 v-for="(types,index) in types" :key="index" class="px-5 rounded-xl py-1 text-white" :class="typeColor(types.type.name)">{{types.type.name}}</h1>
      </div>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  props: ['pokemon', 'imgIndex'],
  data() {
    return {
      image:
        'https://assets.pokemon.com/assets/cms2/img/pokedex/detail/' +
       this.convertId(this.imgIndex) +
        '.png',

        url : this.pokemon.url,
        types : {},

        getUrl: '/pokemon/'+this.imgIndex+'/'+this.pokemon.name,
    }
  },
  methods : {
    convertId(){
      if (String(this.imgIndex).length==1) {
        return `00`+this.imgIndex;
      }else if(String(this.imgIndex).length==2){
        return `0`+this.imgIndex;
      }else if(String(this.imgIndex).length==3){
        return this.imgIndex
      }
    },
    async getData(){
      this.types = await this.$axios.get(this.url).then((res)=>{return res.data.types}).catch((err)=>console.log(err))
    },

    typeColor(pokeType){
      if (pokeType=="grass") {
        return "bg-green-600";
      } else if (pokeType=="poison"){
        return "bg-indigo-700";
      
      } else if (pokeType=="fire"){
        return "bg-red-500";
      }  else if (pokeType=="flying"){
        return "bg-gradient-to-b from-green-400 to-blue-500 ";
      }
      else if (pokeType=="water"){
        return "bg-blue-500 ";
      }else if (pokeType=="bug"){
        return "bg-green-500 ";
      }else if (pokeType=="normal"){
        return "bg-white text-gray-800 ";
      } else if (pokeType=="electric"){
        return "bg-yellow-500 ";
      }else if (pokeType=="ground"){
        return "bg-gradient-to-b from-yellow-700 to-yellow-300 ";
      }else if (pokeType=="fairy"){
        return "bg-red-300 ";
      }else if (pokeType=="fighting"){
        return "bg-yellow-500 ";
      } else if (pokeType=="psychic"){
        return "bg-indigo-400 ";
      }else if (pokeType=="ice"){
        return "bg-blue-300 ";
      }else if (pokeType=="rock"){
        return "bg-gray-500 ";
      }else if (pokeType=="dragon"){
        return "bg-gradient-to-b from-red-500 to-blue-400 ";
      }else if (pokeType=="dark"){
        return "bg-gradient-to-b from-white to-black ";
      }else if (pokeType=="ghost"){
        return "bg-indigo-800 ";
      }
    }
  },
  mounted(){
    this.getData();
  }
}
</script>
