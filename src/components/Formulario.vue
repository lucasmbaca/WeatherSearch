<script setup>
    import {ref, reactive } from 'vue';

    import Alerta from './Alerta.vue'

    const emit = defineEmits(['obtener-clima'])

    const paises = [
        { codigo: 'CL', nombre: 'Chile' },
        { codigo: 'US', nombre: 'Estados Unidos' },
        { codigo: 'MX', nombre: 'México' },
        { codigo: 'AR', nombre: 'Argentina' },
        { codigo: 'CO', nombre: 'Colombia' },
        { codigo: 'CR', nombre: 'Costa Rica' },
        { codigo: 'ES', nombre: 'España' },
        { codigo: 'PE', nombre: 'Perú' }
    ]

    const busqueda = reactive({
        ciudad:'',
        pais:''
    })

    const error = ref('')

    const buscarClima = () => {
        console.log('buscando...')
        if(Object.values(busqueda).includes('')){
            error.value = 'Todos los campos son obligatorios'
            return
        }

        error.value=''

        emit('obtener-clima', busqueda)
        
    }

</script>

<template>
    <form
        class="formulario"
        @submit.prevent="buscarClima"
    >

        <Alerta v-if="error">{{ error }}</Alerta>

        <div class="campo">
            <label for="ciudad">Ciudad</label>
            <input 
                type="text"
                id="ciudad"
                placeholder="Ciudad"
                v-model="busqueda.ciudad"
            >
        </div>
        <div class="campo">
            <label for="pais">Pais</label>
            <select
                id="pais"
                v-model="busqueda.pais"
            >
                <option value="">-- Seleccionar --</option>
                <option v-for="pais in paises" :value="pais.codigo">{{ pais.nombre }}</option>
            </select>
        </div>      
        
        <input type="submit" value="Consultar Clima">
    </form>
</template>


