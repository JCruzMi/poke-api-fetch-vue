<template>
  <div class="row" >
    <poke 
    
    v-for="poke in pokes"
      :key="poke.id"
    
    :poke="poke" />
  </div>
</template>

<script>

import {inject} from 'vue'
import Poke from './Poke.vue'

export default {
    components: {
        Poke
    
    },
    async setup(){

        const pokes = inject('pokes')

        console.log(pokes)

        return {pokes}
    },
    

}
</script>

<style>

</style>