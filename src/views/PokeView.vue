<script setup>
    import {useRoute, useRouter} from 'vue-router'
    import {useGetData} from '@/composables/getData'
    import {useFavoritoStore} from '@/store/favoritos'

    const route=useRoute()
    const router=useRouter()

    const useFavoritos=useFavoritoStore()

    const { add ,findpoke}=useFavoritos

    const {getData,data,loading} = useGetData();

    const back=()=>
    {
        router.push('/pokemon')
    }

    /* const getData=async()=>
    {
        try {
            const {data}=await axios.get(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)
            console.log(data)
            poke.value=data
        } catch (error) {
            console.log(error)
            poke.value=null
        }        
    } */

    getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}/`)
</script>


<template>
    <h1 v-if="loading">Cargando informacion</h1>

    <div v-if="data">
        <img :src=" data.sprites?.other.home.front_default " alt="">
        <h1>Poke Name: {{$route.params.name}}</h1>
        <button :disabled="findpoke(data.name)" class="btn btn-outline-danger mb-2" @click="add(data)">Agregar Favoritos</button>
    </div>
    <h1 v-else>No Existe el pokemon</h1>
    <button @click="back" class="btn btn-outline-primary">volver</button>
    
    
</template>