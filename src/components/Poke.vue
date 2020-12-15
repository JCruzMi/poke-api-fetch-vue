<template>
    <div class="poke-card">
        <div class="unkown" v-if="poke.stats" >
            <div class="card" :style="poke.bg" type="button"  @click="onStatsClick(poke.id)">
                <div class="pokemon" >
                    <img :src="poke.img" alt="" width="92" height="92">
                </div>
                <div class="card-body" >
                    <li class="list-group-item d-flex justify-content-between align-items-center  list-inline-item" >
                        <span>{{poke.name}}</span>
                    </li>
                    <poke-footer :poke="poke"></poke-footer>
                </div>
            </div>
        </div>
    </div>
    
    <div class="col-md-4 col-sm-6 col-xl-3">
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
                    console.log(item.stats)
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
        position: absolute;
        width: 87%;
        height: 75%;
        text-align: center;
        align-items: center;
    }

    .poke-card .card{
        margin-left: 40%;
        z-index: 10;
        width: 20%;
        height: 120px;
    }

    

    .poke-card .card .pokemon{
        margin-top: 5%;
    }
    
    

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