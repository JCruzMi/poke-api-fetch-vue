<template>  
    <form @submit.prevent="filtrar">
        <div class="container">
            <ul class="list-group">
                <li class="list-group-item d-flex justify-content-between align-items-center">
                    <img class="img" src="https://raw.githubusercontent.com/HybridShivam/pokedex-angular-app/master/pokedex.png">
                    <div style="width:90%">
                        <input
                            type="text"
                            class="form-control my-3"
                            placeholder="Buscar pokemon"
                            v-model.trim="texto"
                        >
                    </div>
                </li>
            </ul>
        
        </div>
  </form>
</template>

<script>

import {ref, inject, provide} from 'vue'

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
.img{
    width: 5%;
    height: 5%;
}
</style>