<template>
  <poke-header v-if="mHeader"/>

  <div class="row" >
    <poke 
    
    v-for="poke in pokes"
      :key="poke.id"
    
    :poke="poke" />
  </div>
</template>

<script>

import {inject, provide, computed, ref} from 'vue'
import Poke from './Poke.vue'
import PokeHeader from './PokeHeader.vue'

export default {
    components: {
        Poke,
        PokeHeader
    
    },
    async setup(){

        const AllPokes = inject('pokes')

        const estado = ref('')

        const mHeader = inject('mHeader')

        const pokes = computed(() => {
          if(estado.value === ''){
            return AllPokes.value
          }else{
            return AllPokes.value.filter(item => item.id === estado.value-1+1 || item.name.includes(estado.value))
          }
        })

        provide('estado', estado)

        return {pokes, mHeader}
    },
    

}
</script>

<style>

</style>