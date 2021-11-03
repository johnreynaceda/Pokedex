<template>
     <div class="mt-3 bg-white p-2 px-4  rounded-lg shadow-lg h-80 bg-gray-300">
               
               <div class="flex flex-col w-full h-full ">
                 <div class="header">
                   <h1 class="text-gray-700 font-bold text-lg">STATS</h1>
                 </div>
     <div class="grid grid-cols-6 gap-4 mt-5">

                <PokemonStats :class="col-span-1" v-for="(statItem,index) in stats" :key="index" :statItem="statItem"/>
     </div>
                 </div>
             </div>
</template>



<script>
export default {
    props:['stats']
}
</script>