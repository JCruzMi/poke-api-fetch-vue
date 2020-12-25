<template>
    <poke-show :poke="poke" v-if="poke.stats"/>
    
    <div class="col-md-4 col-sm-6 col-xl-3" v-if="mostrar">
        <div class="card" :style="poke.bg" type="button"  @click="onStatsClick(poke.id)">
            <div class="pokemon" >
                <img :src="poke.img" alt="" width="92" height="92">
            </div>
            <div class="card-body" >
                <li class="list-group-item d-flex justify-content-between align-items-center list-inline-item" >
                    <span>{{poke.name}}</span>
                </li>
            </div>
        </div>
    </div>
</template>

<script>
import {inject} from 'vue'
import PokeFooter from './PokeFooter.vue'
import PokeShow from './PokeShow.vue'

export default {
    props: ["poke"],
    components:{
        PokeFooter,
        PokeShow
        
    },
    setup(){
         const pokes = inject('pokes')

         const mHeader = inject('mHeader')

        const mostrar = inject('mostrar')
        //cambia el valor stats para mostrar o no dando click al boton los elementos 
        const onStatsClick = id => {
            mHeader.value = false
            mostrar.value = false
            pokes.value = pokes.value.map(item => {
                if(item.id === id){
                    item.stats = !item.stats
                }
                
                return item
            })
        }
        return {onStatsClick, mostrar}
    }
}

</script>

<style>
    .card {
        z-index:1;
      align-items: center;
      margin: 10%;
      color: white;
      height: 80%;
    }
    .pokemon{
        margin-top: 10%;
    }
    li.list-group-item.d-flex.justify-content-between.align-items-center{
        background-color: transparent;
        border: solid 0px;
    }
    .card-body{
        padding: 10px;
    }
</style>