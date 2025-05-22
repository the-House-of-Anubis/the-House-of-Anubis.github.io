<script setup>
import { ref, onMounted, inject } from 'vue'
import axios from 'axios'
import MaskBoard from './MaskBoard.vue'

const masks = ref([])
const colors = ref({})

const API_URL = inject('UCDI_API')

onMounted(async () => {
  try {
    
    const response = await axios.get(`${API_URL}platonics`)
    masks.value = response.data.masks
    colors.value = response.data.colors
    console.log(response);
  } catch (error) {
    console.error("Błąd pobierania masek:", error)
  }
})
</script>

<template>
  <MaskBoard v-if="masks.length" :masks="masks" :colors="colors" />
  <div v-else class="has-text-centered mt-6">
    <progress class="progress is-small is-primary" max="100">Ładowanie...</progress>
  </div>
</template>