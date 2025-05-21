<template>
    <div id="cuerpo">
      <header>
        <h1>TP4</h1>
      </header>
  
      <main>
        <h2>Selecciona un componente que deseas ver</h2>
  
        <div id="seleccionar">
          <select v-model="componenteSeleccionado">
            <option value="Lista">Lista</option>
            <option value="Tareas">Tareas</option>
            <option value="DimensionComponente">Dimencionar</option>
          </select>
        </div>
  
        <Alertas :componente="componenteSeleccionado" :key="componenteSeleccionado + '-alerta'" />
  
        <component :is="componentes[componenteSeleccionado]" :key="componenteSeleccionado" />
      </main>
  
      <aside>
        <h2>Trabajo realizado por</h2>
        <p>Jonathan Gorostiaga</p>
      </aside>
  
      <footer>
        <h1>Todos los derechos reservados</h1>
      </footer>
    </div>
  </template>
  
  <script setup lang="ts">
  import Lista from './components/Lista.vue';
  import Tareas from './components/tareas.vue';
  import DimensionComponente from './components/DimensionComponente.vue';
  import Alertas from './components/alertas.vue';
  
  import { ref } from 'vue';
  
  const componentes = {
    Lista,
    Tareas,
    DimensionComponente,
  };
  
  const componenteSeleccionado = ref<'Lista' | 'Tareas' | 'DimensionComponente'>('Lista');
  </script>
  
  <style scoped>
  #cuerpo {
    display: grid;
    grid-template-areas:
      "header header header"
      "aside main main"
      "footer footer footer";
    grid-template-columns: 1fr 2fr 1fr;
    grid-template-rows: auto 1fr auto;
    height: 100vh;
    gap: 1px;
    margin: -7px;
  }
  
  header {
    background-color: #e6b8a2;
    grid-area: header;
    text-align: center;
  }
  
  aside {
    background-color: #e2a5b9;
    grid-area: aside;
    padding: 20px;
  }
  
  main {
    background-color: #b0d3eb;
    grid-area: main;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  footer {
    background-color: #a3c27a;
    height: auto;
    grid-area: footer;
    text-align: center;
  }
  
  select {
    font-size: 20px;
    margin: 10px;
    padding: 10px;
    background: linear-gradient(rgb(113, 113, 116), rgb(216, 209, 209));
  }
  </style>
  