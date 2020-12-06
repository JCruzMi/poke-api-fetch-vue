<template>
  <div class="container" >
    <Suspense>
      <template #default>
        <poke-app/>
      </template>
      <template #fallback>
        <div>Loading pokemons</div>
      </template>
    </Suspense>
  </div>
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
  body{
    background: rgb(41, 41, 41);
  }
</style>
