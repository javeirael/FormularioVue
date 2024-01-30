<template>
  <div>
    <nav class="navbar">
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
      <RouterLink to="/Formulario">Formulario</RouterLink>
    </nav>

    <div class="router-view-wrapper">
      <RouterView />
    </div>
  </div>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: #62caa8; 
  color: white; /* Cambia el color del texto según tus preferencias */
  padding: 1rem;
  text-align: center;
}

.navbar a {
  color: white;
  text-decoration: none;
  padding: 1rem;
}

.navbar a:hover {
  background-color: #33a177; 
}

.router-view-wrapper {
  margin-top: 2rem; 
}
</style>
