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

        const Color = {
          normal : '#ffe175',
          fighting : '#ff6200',
          flying:'#008db0',
          ground: '#7f724a',
          rock: '#908a78',
          bug: '#85b100',
          steel:'#c5c5c5',
          fire:'#ff9000',
          water:'#00c3c7',
          grass: '#abff4d',
          electric: '#fffd4d',
          psychic:'#613dfe',
          ice:'#97cdff',
          dragon:'#ff335c',
          dark:'#323232',
          fairy:'#ff7af3',
          unknown:'#ffb9b9',
          shadow:'#757575',
          ghost: '#8d1bdb',
          poison: '#690081'
        }

    const pokes = ref([])
    provide('pokes',pokes)

    for ( let i = 1; i <= 200 ; i++){
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
                        'types': pet.types[0].type.name,
                        'exp':pet.base_experience,
                        'mostrar':true,
                        'bg':{background : Color[pet.types[0].type.name]},
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