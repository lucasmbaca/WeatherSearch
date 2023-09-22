<script setup>
import Formulario from './components/Formulario.vue'
import useClima from './composable/useClima'
import Spinner from './components/Spinner.vue'
import Clima from './components/Clima.vue'
import Alerta from './components/Alerta.vue'

const {obtenerClima, clima, mostrarClima, cargando, error} = useClima()

</script>

<template>
  <h1 class="titulo">Buscador de clima</h1>
  <div class="contenedor buscador-clima">
    <Formulario
    @obtener-clima="obtenerClima"
    />

    <Alerta v-if="error">{{ error }}</Alerta>
    
    <Spinner
      v-if="cargando"
    />

    <Clima
      v-if="mostrarClima"
      :clima="clima"
    />
  </div> 
</template>