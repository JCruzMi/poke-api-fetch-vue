<template>
    <div class="col-md-4 col-sm-6 col-xl-3" >
        <div class="card" :style="poke.bg" >
            <div class="pokemon" >
                <img :src="poke.img" alt="" width="92" height="92">
            </div>
            <div class="card-body" >
                <li class="list-group-item d-flex justify-content-between align-items-center" >
                    <span>{{poke.name}}</span>
                </li>
                <poke-footer
                :poke="poke" 
                />
                
            </div>
        </div>
    </div>
</template>

<script>
import PokeFooter from './PokeFooter.vue'
import {inject} from 'vue'

export default {
    props: ["poke"],
    components:{
        PokeFooter
    },
    setup(){
        
        const pokes = inject('pokes')

        //cambia el valor stats para mostrar o no dando click al boton los elementos 
        const onStatsClick = id => {
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
    .card {
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