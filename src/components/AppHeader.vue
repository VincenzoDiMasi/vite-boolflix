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
        <h1 class="m-4">
            BOOLFLIX
        </h1>
        <div class="input-group flex-nowrap w-25">
            <input @keyup="cleanInput" @keyup.enter="onTypeSearch" v-model.trim="searchMovie" type="text" class="form-control" placeholder="Cerca" aria-label="Username" aria-describedby="addon-wrapping">
            <button @click="onTypeSearch" class="btn btn-danger">Cerca</button>
        </div>
    </header>

</template>

<style scoped>
    header {
        height: 80px;
        background-color: black;
    }
</style>