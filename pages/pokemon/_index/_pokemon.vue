<template>
<div class="bg-gray-200 h-full w-sreen flex">
    <Navigation />
    <div class="flex-1 p-8">
      <h1 class="text-3xl font-bold text-gray-800">POKEDEX</h1>
     <div class="bg-blue-400 mt-10 p-5 rounded-2xl shadow-lg  bg-gradient-to-t from-green-200 via-blue-400 to-green-500">
         <div class="name flex space-x-4 items-center text-3xl">
           <h1 class="font-bold uppercase text-white">{{pokemon.name}}</h1>
           <h1 class="font-semibold  text-gray-200 text-xl">#{{pokemon.id}}</h1>
         </div>
         <div class="mt-5 flex space-x-3"> 
           <div class=" w-96 ">
             <div class="bg-white rounded-lg shadow-lg flex justify-center items-center w-96 h-80">
               <img :src="image" alt="" class="h-80 rounded-lg ">
             </div>
             <div class="mt-4">
               <h1 class="text-lg font-bold text-gray-700">TYPE</h1>
               <div class=" mt-2 flex space-x-2">
                 <h1 v-for="(type, index) in pokemon.types" :key="index" :class="typeColor(type.type.name)" class=" px-3 pb-1 text-white rounded-lg">{{type.type.name}}</h1>
               </div>
             </div>
             <div class="mt-4">
               <h1 class="text-lg font-bold text-gray-700">WEAKNESS</h1>
               <div class="mt-2 flex space-x-2">
                 <h1 class="bg-blue-300 px-3 pb-1 rounded-lg">sdsdsd</h1>
                 <h1 class="bg-blue-300 px-3 pb-1 rounded-lg">sdsdsd</h1>
               </div>
             </div>
             </div>
           <div class=" flex-1">
            
             <div class=" bg-white p-2 rounded-lg shadow-lg h-64 bg-gray-200">
               <div class="grid grid-cols-2 gap-4">
              <div>
               <div class="header">
                 <h1 class="font-bold">WEIGHT</h1>
               </div>
               <div class="mt-1">
                 {{pokemon.weight}} lbs
               </div>
              </div>
              <div>
               <div class="header">
                 <h1 class="font-bold">BASE EXPERIENCE</h1>
               </div>
               <div class="mt-1">
                {{pokemon.base_experience}}
               </div>
              </div>
              <div>
               <div class="header">
                 <h1 class="font-bold">HEIGHT</h1>
               </div>
               <div class="mt-1">
                  {{pokemon.height}} "
               </div>
              </div>
              
              
            
            </div>
            <div class="mt-2">
              <div class="header">
                <h1 class="font-bold text-green-600">ABILITIES</h1>
              </div>

              <div class="grid grid-cols-6 gap-2">
              <div v-for="(abilities, index) in pokemon.abilities" :key="index" class="bg-white rounded-xl mt-2 shadow-lg text-center">
               {{abilities.ability.name}}
              </div>
             
              
              
            
            </div>
            </div>
             </div>
            <PokemonStatsContainer  :stats="pokemon.stats" />
           </div>
         </div>
     </div>
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
export default {

  data(){
    return{
      image:
        'https://assets.pokemon.com/assets/cms2/img/pokedex/detail/' +
       this.convertId(this.$route.params.index) +
        '.png',
    }
  },
methods:{
   convertId(){
      if (String(this.$route.params.index).length==1) {
        return `00`+this.$route.params.index;
      }else if(String(this.$route.params.index).length==2){
        return `0`+this.$route.params.index;
      }else if(String(this.$route.params.index).length==3){
        return this.$route.params.index
      }
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

  async asyncData({params , $axios}){
     const pokemon = await $axios.$get(`https://pokeapi.co/api/v2/pokemon/${params.pokemon}`);
     return {pokemon}
  }
}
</script>