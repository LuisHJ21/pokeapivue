<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>

  <nav class="navbar bg-dark navbar-dark">
    <div class="container">
      <RouterLink class="navbar-brand " to="/">
        <img src="@/assets/logo.svg" alt="Logo" width="30" height="24" class="d-inline-block align-text-top">
        PokeApi
      </RouterLink>
      <div>
        <RouterLink active-class="active" class="btn btn-outline-primary me-2" to="/">Home</RouterLink>
        <RouterLink active-class="active" class="btn btn-outline-primary me-2" to="/pokemon">Pokemon</RouterLink>
        <RouterLink active-class="active" class="btn btn-outline-primary" to="/favoritos">Favoritos</RouterLink>

      </div>
    </div>
  </nav>
  
  <div class="container">
    <RouterView />
  </div>

  
</template>


