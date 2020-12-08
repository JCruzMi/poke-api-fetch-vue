<template>
  <Suspense>
    <template #default>
      <poke-list/>
    </template>
    <template #fallback>
      <div><h1>Loading pokemons...</h1></div>
    </template>
  </Suspense>
</template>

<script>
import PokeList from './PokeList.vue'
import {ref, provide} from 'vue'

export default {
  components: { PokeList },
  async setup(){

    function giveColor (type){
        switch (type){
          case 'normal':
            return '#ffe175'
          case 'fighting':
            return '#ff6200'
          case 'flying':
            return '#008db0'
          case 'ground':
            return '#7f724a'
          case 'rock':
            return '#908a78'
          case 'bug':
            return '#85b100'
          case 'steel':
            return '#c5c5c5'
          case 'fire':
            return '#ff9000'
          case 'water':
            return '#00c3c7'
          case 'grass':
            return '#abff4d'
          case 'electric':
            return '#fffd4d'
          case 'psychic':
            return '#613dfe'
          case 'ice':
            return '#97cdff'
          case 'dragon':
            return '#ff335c'
          case 'dark':
            return '#323232'
          case 'fairy':
            return '#ff7af3'
          case 'unknown':
            return '#ffb9b9'
          case 'shadow':
            return '#757575'
          }
          
      }

    const pokes = ref([])
    provide('pokes',pokes)

    for ( let i = 1; i <= 270 ; i++){
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
                        'types':pet.types[0].type.name,
                        'bg':{background : giveColor(pet.types[0].type.name)},
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