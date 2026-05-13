<script setup lang="ts">
import { ref, computed } from 'vue';
import ListOfDays from './components/ListOfDays.vue';
import DNIInput  from './components/DNIInput.vue';
import CorrespondeCobro from './components/CorrespondeCobro.vue';
//logica
type DiaLaboral = 'Lunes' | 'Martes' | 'Miercoles' | 'Jueves' | 'Viernes';

const dias: DiaLaboral [] = ['Lunes', 'Martes', 'Miercoles', 'Jueves', 'Viernes'];

const diaSeleccionado = ref<DiaLaboral>('Lunes')

const dniInput = ref<string>('')

const seleccionarDia = (dia : DiaLaboral): void => {
  diaSeleccionado.value = dia
}

const cronograma: Record<DiaLaboral, string[]> = {
  'Lunes': ['0', '1'],
  'Martes': ['2', '3'],
  'Miercoles': ['4', '5'],
  'Jueves': ['6', '7'],
  'Viernes': ['8', '9']
}

const correspondeCobro = computed (() => {
  if (dniInput.value.length === 0) return null

  const ultimoDigito = dniInput.value.slice(-1)
  const digitoDelDia = cronograma [diaSeleccionado.value]

  return digitoDelDia.includes(ultimoDigito)
})

const actualizarinput = (dni: string):void => {
  dniInput.value = dni
}
</script>



<template>
  <!--html va aca -->
  

  <H1 class="text-xl font-bolt">Gestor de pagos</H1>

    <ListOfDays/>

    <DNIInput @cambio-de-input="actualizarinput"/>

    <CorrespondeCobro
    :dni-input="dniInput"
    :corresponde-cobro="correspondeCobro"/>

</template>

<style scoped>
/* estilos van aca*/ 
</style>
