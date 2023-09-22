<script setup>
import useClima from '../composable/useClima'

const {formatearTemperatura} = useClima()

defineProps({
    clima:{
        type:Object,
        required:true
    }
})

</script>

<template>
    <div class="resultado">
        <h2>Clima:{{ clima.name }} </h2>
        <p class="actual">{{formatearTemperatura(clima.main.temp )}}</p>
        <div class="temperaturas">
            <p>Min:{{formatearTemperatura(clima.main.temp_min )}} <span>&deg:C</span></p>
            <p>Max:{{formatearTemperatura(clima.main.temp_max )}}<span>&deg:C</span></p>
        </div>
    </div>
</template>



