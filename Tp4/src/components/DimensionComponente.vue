<template>
    <div>
<h1>Dimencion de la ventana: <span id="dimencion">{{ ancho }} <span>X</span> {{ largo }}</span></h1>
    </div>



</template>

<script lang="ts" setup>
import {ref,onMounted, onUnmounted} from 'vue'
 const ancho=ref(0);
 ancho.value=window.innerWidth;
 const largo=ref(0);
 largo.value=window.innerHeight;

 function actualizarDimensiones(){
    ancho.value=window.innerWidth;
    largo.value=window.innerHeight;
 }
 onMounted(()=>{
 window.addEventListener('resize',actualizarDimensiones);
 })

 onUnmounted(()=>{
 window.removeEventListener('resize',actualizarDimensiones);
 })



</script>


<style scoped>

h1{
    display: inline-block;
    margin: 0 auto;
    background-color: crimson;
    padding: 10px;
    text-decoration:underline solid black 5px;
}
div{
    text-align: center;
}
h1 span{
    color: #ffcc66;
}
#dimencion{
    color: #f0f0f0;
}


</style>