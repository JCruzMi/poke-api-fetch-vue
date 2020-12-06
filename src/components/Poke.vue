<template>
    <div class="col-md-4 col-sm-6 col-xl-3" :v-if="poke.length" >
        <div class="card" >
            <div class="pokemon" >
                <img :src="poke.sprites.other.dream_world.front_default" alt="" width="92" height="92">
            </div>
            <div class="card-body" >
                <li class="list-group-item d-flex justify-content-between align-items-center" >
                    <span>{{poke.name}}</span>
                </li>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["poke"]
}

</script>

<style>
    .card {
      background:rgb(255, 196, 0);
      align-items: center;
      margin: 10%;
      color: white;
    }
    .pokemon{
        margin: 3px;
    }
    li.list-group-item.d-flex.justify-content-between.align-items-center{
        background-color: transparent;
        border: solid 0px;
    }
    .card-body{
        padding: 10px;
    }
</style>