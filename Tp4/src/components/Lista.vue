<template>
    <div>
      <h2>Lista de Profesiones</h2>
      <ul>
        <li v-for="profesion in lista" :key="profesion.id">
          {{ profesion.nombre }} - {{ profesion.descripcion }}
        </li>
      </ul>
      <p v-if="lista.length === 0">Cargando profesiones...</p>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref, onMounted } from 'vue';
  import { profesiones } from '../resource/profesiones'; 
  
  interface Profesion {
    id: number;
    nombre: string;
    descripcion: string;
  }
  
  const lista = ref<Profesion[]>([]);
  
  onMounted(() => {
    setTimeout(() => {
      lista.value = [...profesiones]
    }, 3000);
  });
  </script>
  
  <style scoped>
  h2 {
    color: darkblue;
  }
  li{
    margin: 5px;
    font-size: 20px;
  }
  </style>
  