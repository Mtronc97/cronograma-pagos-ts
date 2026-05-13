<script setup lang="ts">
import { ref } from 'vue';


const emit = defineEmits<{
    (e: 'cambioDeInput', dni: string) :void
}>()

const dniInput = ref<string> ('')

const cambiosDetectado = () => {
  emit('cambioDeInput', dniInput.value)
} 

</script>


<template>
    <div class="w-full max-w-md bg-white p6 rounded-2xl shadow-sm border border-slate-200 mt6">
    <label class="block text-sm font-semibold text-slate-700 mb-2">Ingrese su DNI</label>
    <input @change="" v-model="dniInput" type="text" placeholder="99999999" maxlength="8"
    class="w-full p-3 border border-slate-300 rounded-xl focus:ring-2 focus:ring-indigo-500 outline-none transition-all"/>
  </div>
</template>