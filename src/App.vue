<template>
  <Suspense>
    <template #default>
      <poke-app/>
    </template>
    <template #fallback>
      <div>Loading pokemons</div>
    </template>
  </Suspense>
</template>

<script>
import PokeApp from './components/PokeApp.vue'

export default {
  name: 'App',
  components: {
    PokeApp
    
  }
}
</script>

<style>

</style>
