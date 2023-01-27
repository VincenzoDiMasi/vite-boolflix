<script>
import {store} from '../store'
export default {
    data () {
        return {
            store,
            searchProduct: '',
        }
    },
    methods: {
        
    },
    emits: ['product-search', 'clean-input']
}
</script>

<template>
    <header class="d-flex justify-content-between align-items-center px-4">
        <div class="d-flex">
            <h1 class="text-danger">B</h1>
            <h1 class="">
                OOLFLIX
            </h1>
        </div>
        <div class="input-group flex-nowrap w-25">
            <input @keyup="cleanInput" @keyup.enter="onTypeSearch" v-model.trim="searchMovie" type="text" class="form-control" placeholder="Cerca" aria-label="Username" aria-describedby="addon-wrapping">
            <button @click="onTypeSearch" class="btn btn-danger">Cerca</button>
        </div>
    </header>

</template>

<style lang="scss" scoped>
    header {
        height: 80px;
        background-color: black;
        
        h1{
            color: white;
        }
    }
</style>