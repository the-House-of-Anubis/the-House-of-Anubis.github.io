<script setup>
import { provide } from 'vue';
import PlatonExam from './components/PlatonExam.vue'

provide( 'UCDI_API', 'https://apokryf.pl/api/')


</script>

<template>
  <header></header>
  <main>
    <PlatonExam />
  </main>
</template>

<style scoped>
 
</style>
