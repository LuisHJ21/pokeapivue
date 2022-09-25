<script setup>
    import {RouterLink} from 'vue-router'
    import {useGetData} from '@/composables/getData'



    const {data,getData,loading,error}=useGetData()


    getData("https://pokeapi.co/api/v2/pokemon")

</script>

<template>
    <h1>Lista de Pokemon</h1>
    <p v-if="loading" >Cargando Info...</p>
    <div class="alert alert-danger" v-if="error">{{error}}</div>
    <div v-if="data">
        <ul class="list-group text-center">
            <li v-for="pok in data.results" class="list-group-item">
                <router-link :to="`/pokemon/${pok.name}`">{{pok.name}}</router-link>
                
            </li>
        </ul>
        <div class="mt-2">
            <button :disabled="!data.previous" class="btn btn-warning me-2"  @click="getData(data.previous)">Prev</button>
            <button :disabled="!data.next===null" class="btn btn-primary" @click="getData(data.next)">Next</button>
        </div>
        
    </div>
    
</template>