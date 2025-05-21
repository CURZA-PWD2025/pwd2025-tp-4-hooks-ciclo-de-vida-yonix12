<template>

</template>
  
  <script setup lang="ts">
import { onMounted, onUnmounted } from 'vue';

const props = defineProps(['componente']);

onMounted(() => {
  alert(`Cambiaste al componente: ${props.componente}`);
  console.log('🔔 Componente Alertas montado');
});

onUnmounted(() => {
  console.log('❌ Componente Alertas desmontado');
});
</script>

  
  <style scoped>

  </style>
  