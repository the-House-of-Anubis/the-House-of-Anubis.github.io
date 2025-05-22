<script setup>
import { ref, computed } from 'vue'

// addon dla Props
const {masks, colors} = defineProps({
  masks: Array,
  colors: Object,
})

const selected = ref(null)

const getTypeColor = (mask) => {
  return colors?.identifiedMasks?.types?.[mask.type] ?? '#888888'
}
const getStageColor = (mask) => {
  return colors?.identifiedMasks?.stages?.[mask.stage] ?? '#555555'
}
</script>

<template>
  <section class="section">
    <div class="container">
      <h1 class="title is-3 has-text-centered mb-6">Tablica Masek: Eksperyment Platoński</h1>

      <div class="columns is-multiline">
        <div
          v-for="mask in masks"
          :key="mask.id"
          class="column is-one-third"
        >
          <div
            class="box mask-tile has-text-centered"
            :class="{ 'is-selected': selected === mask.id }"
            @click="selected = mask.id"
            :style="{
              backgroundColor: selected === mask.id ? getTypeColor(mask) : '#050505',
              borderColor: selected === mask.id ? getStageColor(mask) : 'transparent'
            }"
          >
            <h2 class="title is-5">{{ mask.label }}</h2>
            <p class="is-size-7 has-text-grey-light">
              Etap: {{ mask.stage }}<br />
              Typ: {{ mask.type }}
            </p>
          </div>
        </div>
      </div>

      <div v-if="selected" class="notification is-info mt-5">
        Wybrana maska:
        <strong>{{ masks.find((m) => m.id === selected).label }}</strong>
      </div>
    </div>
  </section>
</template>

<style scoped>
.mask-tile {
  color: #f0f0f0;
  transition: all 0.3s ease;
  cursor: pointer;
  border: 2px solid transparent;
  background-color: #050505;
  min-height: 120px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}
.mask-tile:hover {
  transform: scale(1.05);
  background-color: #111111;
}
.is-selected {
  box-shadow: 0 0 0 3px rgba(255, 255, 255, 0.2) inset;
  color: black;
}
</style>