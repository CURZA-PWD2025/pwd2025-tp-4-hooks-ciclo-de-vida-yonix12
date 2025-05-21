<template>
  <div>
    <h2>Agregas nuevas Profesiones</h2>
    <input
      v-model="newProfession"
      placeholder="Agregar nueva profesión"
      @keyup.enter="addProfession"
    />
    <button @click="addProfession">Agregar Profesión</button>
    <ul>
      <li
        v-for="profession in professions"
        :key="profession.id"
        :class="{ 'existing-profession': existingIds.includes(profession.id) }"
      >
        {{ profession.nombre }}: {{ profession.descripcion }}
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { ref, onBeforeUpdate, onUpdated } from 'vue';

interface Profesion {
  id: number;
  nombre: string;
  descripcion: string;
}

const professions = ref<Profesion[]>([
  { id: 1, nombre: 'Ingeniero', descripcion: 'Profesión relacionada con ingeniería' },
  { id: 2, nombre: 'Médico', descripcion: 'Profesión dedicada a la salud' },
  { id: 3, nombre: 'Profesor', descripcion: 'Profesión dedicada a la enseñanza' },
  { id: 4, nombre: 'Diseñador', descripcion: 'Profesión dedicada al diseño gráfico' },
  { id: 5, nombre: 'Programador', descripcion: 'Profesión dedicada al desarrollo de software' }
]);

const newProfession = ref('');

const existingIds = ref<number[]>([]);

onBeforeUpdate(() => {
  existingIds.value = professions.value.map(p => p.id);
  console.log('Lista aún no modificada');
});

onUpdated(() => {
  console.log('Lista modificada');
});

const addProfession = () => {
  const nombre = newProfession.value.trim();
  if (nombre !== '') {
    existingIds.value = professions.value.map(p => p.id);

    const newId = professions.value.length + 1;
    professions.value.push({
      id: newId,
      nombre,
      descripcion: 'Descripción de la nueva profesión',
    });
    newProfession.value = '';
  }
};
</script>

<style scoped>
.existing-profession {
  color: blue;
  font-weight: bold;
}
li{
  font-size: 20px;
  margin: 1rem;

}
input, button{
  padding: 10px;
  margin: 2px;

}
div {
  display: flex;
  flex-direction: column;
  align-items: center; 
  justify-content: center; 
  text-align: center;
}


</style>
