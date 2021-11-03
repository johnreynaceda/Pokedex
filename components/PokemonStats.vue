<template>
                    <div class=" flex flex-col w-full ">
                         <h1 class="text-sm text-center font-bold text-gray-800">{{statItem.base_stat}}</h1>
                   <div class="flex flex-col space-y-2">

                    <div :class="statItem.base_stat>=100? 'bg-blue-600' : 'bg-white'" class=" h-2 w-full"></div>

                    <div :class="statItem.base_stat>=90? 'bg-blue-600' : 'bg-white'" class=" h-2 w-full"></div>
                    <div :class="statItem.base_stat>=80? 'bg-blue-600' : 'bg-white'" class=" h-2 w-full"></div>
                    <div :class="statItem.base_stat>=70? 'bg-blue-600' : 'bg-white'" class=" h-2 w-full"></div>
                    <div :class="statItem.base_stat>=60? 'bg-blue-600' : 'bg-white'" class=" h-2 w-full"></div>
                    <div :class="statItem.base_stat>=50? 'bg-blue-600' : 'bg-white'" class=" h-2 w-full"></div>
                    <div :class="statItem.base_stat>=40? 'bg-blue-600' : 'bg-white'" class=" h-2 w-full"></div>
                    <div :class="statItem.base_stat>=30? 'bg-blue-600' : 'bg-white'" class=" h-2 w-full"></div>
                    <div :class="statItem.base_stat>=20? 'bg-blue-600' : 'bg-white'" class=" h-2 w-full"></div>
                    <div :class="statItem.base_stat>=10? 'bg-blue-600' : 'bg-white'" class=" h-2 w-full"></div>
                    <div :class="statItem.base_stat>0? 'bg-blue-600' : 'bg-white'" class=" h-2 w-full" ></div>
                  
                   </div>
                   <h1 class="text-xs text-center font-semibold">HP {{statItem.stat.name}}</h1>
                  </div>
               
</template>

<script>
export default {
    props:['statItem']
}
</script>