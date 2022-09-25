<script setup>
 import {useFavoritoStore} from '@/store/favoritos'
import { storeToRefs } from 'pinia';
import {RouterLink} from 'vue-router'



 const useFavoritos=useFavoritoStore()


const {favoritos}=storeToRefs(useFavoritos)
const {remove}=useFavoritos

</script>

<template>

    <h1>Favoritos</h1>

    <p v-if="favoritos.length===0">Sin favoritos</p>

    <ul class="list-group text-center">
        <li v-for="poke in favoritos" class="list-group-item" :key="poke.id">
            <div>
                {{poke.name}}
            </div>
            <div>
                <button class="btn btn-sm btn-danger me-2" @click="remove(poke.id)">Eliminar</button>
                <router-link class="btn btn-sm btn-success" :to="`/pokemon/${poke.name}`" >Mas Informacion</router-link>

            </div>
            
        </li>
    </ul>

</template>