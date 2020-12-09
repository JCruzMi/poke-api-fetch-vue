<template>
  <!-- Small modal dont works
  <button type="button" class="btn btn-primary" data-toggle="modal" data-target="modal1">Small modal</button>

  <div class="container">
    <div class="modal"
      tabindex="-1" 
      id="modal1"
      >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-body"> 
              ...
          </div>
        </div>
      </div>
    </div>
  </div>
  -->
  <poke-header />

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

        const pokes = computed(() => {
          if(estado.value === ''){
            return AllPokes.value
          }else{
            return AllPokes.value.filter(item => item.id === estado.value-1+1 || item.name.includes(estado.value))
          }
        })

        provide('estado', estado)

        return {pokes}
    },
    

}
</script>

<style>

</style>