<template>
  <p>{{pokes.name}} {{pokes.id}}</p>
</template>

<script>

import {inject} from 'vue'

export default {
    components: {
    
    },
    async setup(){

        const pokes = inject('pokes')

        return {pokes}
    },
    

}
</script>

<style>

</style>