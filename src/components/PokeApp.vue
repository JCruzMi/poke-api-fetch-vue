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

    for ( let i = 1; i <= 150; i++){
      const responsePoke = await fetch('https://pokeapi.co/api/v2/pokemon/'+i)

      let pet = await responsePoke.json()

      pokes.value.push(pet)
    }

    return{pokes}

  }

}
</script>

<style>

</style>