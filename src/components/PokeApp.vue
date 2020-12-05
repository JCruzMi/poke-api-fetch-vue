<template>
  <Suspense>
    <template #default>
      <poke-list/>
    </template>
    <template #fallback>
      <div>Loading pokemons</div>
    </template>
  </Suspense>
</template>

<script>
import PokeList from './PokeList.vue'
import {ref, provide} from 'vue'

export default {
  components: { PokeList },
  async setup(){

    const pokes = ref([])
    provide('pokes',pokes)

    const responsePoke = await fetch('https://pokeapi.co/api/v2/pokemon/1')

    pokes.value = await responsePoke.json()
    
    return{pokes}

  }

}
</script>

<style>

</style>