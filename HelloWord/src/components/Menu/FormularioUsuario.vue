<template>
  <form @submit.prevent="submitForm">
    <div class="form-group">
      <label for="nombre">Nombre:</label>
      <input type="text" id="nombre" v-model="nombre" pattern="[A-Za-záéíóúÁÉÍÓÚüÜñÑ\s]+" required class="rounded-input">
      <span v-if="nombreInvalido" class="error-message">El nombre no puede contener números.</span>
      <span v-if="nombreIguales" class="error-message">El nombre y el apellido no pueden ser iguales.</span>
    </div>
    <div class="form-group">
      <label for="apellido">Apellido:</label>
      <input type="text" id="apellido" v-model="apellido" pattern="[A-Za-záéíóúÁÉÍÓÚüÜñÑ\s]+" required class="rounded-input">
      <span v-if="apellidoInvalido" class="error-message">El apellido no puede contener números.</span>
      <span v-if="apellidoIguales" class="error-message">El nombre y el apellido no pueden ser iguales.</span>
    </div>
    <div class="form-group">
      <label for="edad">Edad:</label>
      <input type="number" id="edad" v-model.number="edad" min="1" required class="rounded-input">
      <span v-if="edadInvalida" class="error-message">La edad debe estar entre 1 y 60 años.</span>
    </div>
    <div class="form-group">
      <label for="telefono">Teléfono:</label>
      <input type="tel" id="telefono" v-model="telefono" @keypress="validarTelefono" maxlength="10" required class="rounded-input">
      <span v-if="telefonoInvalido" class="error-message">El teléfono debe tener 10 dígitos numéricos.</span>
    </div>


    <div class="form-group">
      <label for="genero">Género:</label>
      <select id="genero" v-model="genero" required class="rounded-input">
        <option value="">Selecciona un género</option>
        <option value="hombre">Hombre</option>
        <option value="mujer">Mujer</option>
        <option value="otros">Otros</option>
      </select>
      <input v-if="genero === 'otros'" type="text" v-model="otroGenero" placeholder="Especificar otro género" class="rounded-input">
    </div>
    <div> 
      <button type="submit" class="enviar-button" >Enviar</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      nombre: '',
      apellido: '',
      edad: null,
      telefono: '',
      genero: '',
      otroGenero: '',
      nombreInvalido: false,
      apellidoInvalido: false,
      nombreIguales: false,
      apellidoIguales: false,
      edadInvalida: false,
      telefonoInvalido: false
    };
  },
  methods: {

    validarTelefono(event) {
    const charCode = event.keyCode;
    if (charCode < 48 || charCode > 57) {
      event.preventDefault(); 
    }
  },
    submitForm() {
      // Validación del Nombre
      if (!/^[A-Za-záéíóúÁÉÍÓÚüÜñÑ\s]+$/.test(this.nombre)) {
        this.nombreInvalido = true;
      } else {
        this.nombreInvalido = false;
      }

      // Validación del Apellido
      if (!/^[A-Za-záéíóúÁÉÍÓÚüÜñÑ\s]+$/.test(this.apellido)) {
        this.apellidoInvalido = true;
      } else {
        this.apellidoInvalido = false;
      }

      // Validación de la Edad
      if (this.edad < 1 || this.edad > 60) {
        this.edadInvalida = true;
      } else {
        this.edadInvalida = false;
      }

      // Validación del Teléfono
      if (this.telefono.length !== 10) {
        this.telefonoInvalido = true;
      } else {
        this.telefonoInvalido = false;
      }

    // Validación del Nombre y Apellido
    if (this.nombre.toLowerCase() === this.apellido.toLowerCase()) {
      this.nombreIguales = true;
      this.apellidoIguales = true;
      return;
    } else {
      this.nombreIguales = false;
      this.apellidoIguales = false;
    }

    }
  }
};
</script>

<style>
.form-group {
  margin-bottom: 2px;
}

.error-message {
  color: red;
  font-size: 12px;
  display: block;
}

.rounded-input {
  border-radius: 5px;
  border: 1px solid #ccc;
  padding: 8px;
  width: 100%;
  box-sizing: border-box;
}
.enviar-button {
  border: none;
  border-radius: 20px; 
  background-color: blue; 
  color: white; 
  padding: 10px 20px; 
  cursor: pointer; 
  transition: background-color 0.3s; 
}

.enviar-button:hover {
  background-color: darkblue; 
}
</style>
