<template>
  <div class="text-center record gap-1 flex justify-center font-bold text-white">      
    <div class="wins bg-green-600 px-6 rounded">
      <p class="text-3xl">{{ fighter.wins }} </p>
    </div>
    
    <div class="losses bg-red-600 px-6 rounded">
      <p class="text-3xl">{{ fighter.losses }}</p>
    </div>
    
    <div class="draws bg-blue-400 px-6 rounded">
      <p class="text-3xl">{{ fighter.draws }}</p>
    </div>  
  </div>

  <div>
    <img class="rounded-xl" :src="fighter.image" alt="fighter image">
  </div>

  <div class="max-w-5xl">
    <div class="max-w-md p-2 bg-slate-600 m-12 rounded-xl">
      <img :src="fighter.image" alt="fighter image">
    </div>
    <div class="card text-center border-4 ">
      <p>Fighter ID: {{ fighter._id }}</p>
      <p>{{ fighter.firstName }}</p>
      <p>{{ fighter.lastName }}</p>
    <p>{{ fighter.wins }} Wins</p>
    <p>Overall: {{ fighter.ovr }}</p>   
  </div>
  </div>
  
</template>

<script setup>
  const { fighters } = defineProps(['fighter'])
  const { id } = useRoute().params
  const uri = 'https://virtron-production.up.railway.app/fighters/' + id 

  // fetch fighters
  const { data: fighter } = await useFetch(uri, { key: id })
  
</script>

<style scoped>

</style>