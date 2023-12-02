<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div>
    <div class="banner">
      <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="100" height="100" />
      <div>
        <h1>Administración de presupuestos</h1>
        <h1>Municipalidad de Trancas</h1>
      </div>
    </div>

    <nav>
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/cargapre">Carga de presupuesto</RouterLink>
    </nav>
  </div>
</template>
<style scoped>
.wrapper {
  display: flex;
  place-items: flex-start;
  flex-wrap: wrap;
}
.banner {
    display: flex;
    align-items: center;
    justify-items: center;
    padding: 1rem;
}
</style>
