<template>
    <form @submit.prevent="filtrar">
        <input
            type="text"
            class="form-control my-3"
            placeholder="Buscar pokemon"
            v-model.trim="texto"
        >
  </form>
</template>

<script>

import {ref, inject} from 'vue'

export default {
    setup(){
        const estado = inject('estado')
        
        const texto = ref('')

        const filtrar = () =>{
            if(texto.value === ''){
                estado.value = ''
            }
            else{
                estado.value = texto.value
            }
        }
        //return de la funcion que se usa en el componente
        return {filtrar, texto}

    }
}
</script>

<style>

</style>