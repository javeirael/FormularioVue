<template>
  <main>
    <p class="titulo">Completa el formulario</p>
    <FormularioUsuario />
  </main>
</template>

<script setup lang="ts">
import FormularioUsuario from '../components/Menu/FormularioUsuario.vue'
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  flex-direction: column; 
  align-items: center; 
}

.titulo {
  font-size: 24px;
  margin-bottom: 20px; 
}
</style>
