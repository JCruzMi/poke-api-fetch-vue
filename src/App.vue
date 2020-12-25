<template>
  <div class="container" >
    <Suspense>
      <template #default>
        <poke-app/>
      </template>
      <template #fallback>
        <div class="d-flex justify-content-center" style="margin-top: 10%">
          <div class="spinner-border text-light" role="status"></div>
        </div>
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
