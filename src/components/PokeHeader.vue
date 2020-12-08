<template>
    <div class="md-form active-purple active-purple-2 mb-3">
        <input class="form-control" type="text" placeholder="Search" aria-label="Search">
    </div>
</template>

<script>

import {inject} from 'vue'

export default {
    setup(){
        const pokes = inject('pokes')
    }
}
</script>

<style>

</style>