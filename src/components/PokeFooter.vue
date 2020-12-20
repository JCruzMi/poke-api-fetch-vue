<template>
    <div class="progress">
        <div class="progress-bar bg-success" role="progressbar" :style="{width: poke.hp+'%'}" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100">{{poke.hp}}</div>
    </div>
    <div class="progress">
        <div class="progress-bar bg-success" role="progressbar" :style="{width: poke.atk+'%'}" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100">{{poke.atk}}</div>
    </div>
    <div class="progress">
        <div class="progress-bar bg-success" role="progressbar" :style="{width: poke.def+'%'}" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100">{{poke.def}}</div>
    </div>
    <div class="progress">
        <div class="progress-bar bg-success" role="progressbar" :style="{width: poke.espatk+'%'}" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100">{{poke.espatk}}</div>
    </div>
    <div class="progress">
        <div class="progress-bar bg-success" role="progressbar" :style="{width: poke.espdef+'%'}" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100">{{poke.espdef}}</div>
    </div>
</template>

<script>

import {inject} from 'vue'

export default {
    props:['poke'],
    setup(){
        
        const pokes = inject('pokes')

        //cambia el valor stats para mostrar o no dando click al boton los elementos 
        const onStatsClick = id => {
            pokes.value = pokes.value.map(item => {
                if(item.id === id){
                    item.stats = !item.stats
                }
                item.mostrar = !item.mostrar
                return item
            })
        }

        return {onStatsClick}
    }
}
</script>

<style>

</style>