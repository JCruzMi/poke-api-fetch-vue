<template>
    <div class="container">
        <div class="poke-card">
            <div class="unkown">
                <div class="card" :style="poke.bg" type="button"  @click="onStatsClick(poke.id)">
                    <div class="pokemon" >
                        <img :src="poke.img" alt="" width="92" height="92">
                    </div>
                    <div class="card-body" >
                        <span>{{poke.name}}</span>
                        <div class="peso">
                            <ul class="list-group">
                                <li class="list-group-item d-flex justify-content-between align-items-center">
                                    {{poke.height}}
                                    <span>{{poke.weight}}</span>
                                </li> 
                                <li class="list-group-item d-flex justify-content-between align-items-center">
                                    Altura
                                    <span>Peso</span>
                                </li> 
                            </ul>
                        </div>
                        <br>
                    
                        <poke-footer :poke="poke"></poke-footer>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import {inject} from 'vue'
import PokeFooter from './PokeFooter.vue'

export default {
props: ["poke"],
    components:{
        PokeFooter 
    },  
    setup(){
         const pokes = inject('pokes')

         const mHeader = inject('mHeader')

         const mostrar = inject('mostrar')

        //cambia el valor stats para mostrar o no dando click al boton los elementos 
        const onStatsClick = id => {
            mHeader.value = true
            mostrar.value = true
            pokes.value = pokes.value.map(item => {
                if(item.id === id){
                    item.stats = !item.stats
                }
                return item
            })
        }
        return {onStatsClick}
    }
}
</script>

<style>

.poke-card {
    width: 100%;
    text-align: center;
    justify-content: center;
    align-items: center;
    display: flex;
  
}

    .poke-card .card{
        width: 300px;
        height: 120px;
    }

    .poke-card .card-body{
        width: 100%;
    }

    .poke-card .card .pokemon{
        margin-top: 5%;
    }
    
</style>