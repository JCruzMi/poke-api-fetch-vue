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

    for ( let i = 1; i <= 10; i++){
      const responsePoke = await fetch('https://pokeapi.co/api/v2/pokemon/'+i)

      let pet = await responsePoke.json()

      let pok = await {'name':pet.name, 
                        'id':pet.id, 
                        'img':pet.sprites.other.dream_world.front_default,
                        'atk':pet.stats[1].base_stat, 
                        'hp':pet.stats[0].base_stat, 
                        'espatk':pet.stats[3].base_stat,
                        'def':pet.stats[2].base_stat,
                        'espdef':pet.stats[4].base_stat,
                        'speed':pet.stats[5].base_stat,
                        'height':pet.height,
                        'weight':pet.weight,
                        'exp':pet.base_experience,
                        'types':pet.types,
                        'bg':{background : "#d67f44"},
                        'stats': false
                        }

      pokes.value.push(pok)
    }

    return{pokes}

  }

}
</script>

<style>

</style>