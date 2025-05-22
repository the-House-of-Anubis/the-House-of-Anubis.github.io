<script setup>
import MaskBoard from './MaskBoard.vue'

const colors = {
  identifiedMasks: {
    types: {
      adaptive: '#48c78e',
      avoidant: '#f14668',
      compliant: '#ffe08a',
      searching: '#00d1b2',
      analytic: '#3273dc',
      reactive: '#b86bff'
    },
    stages: {
      neutral: '#363636',
      resistance: '#ff3860',
      camouflage: '#ffdd57',
      navigation: '#209cee',
      passive: '#7a7a7a',
      resonance: '#a855f7'
    }
  }
}

const masks = [
  { id: 'mirror', label: 'Zwierciadlany Analityk', type: 'adaptive', stage: 'neutral' },
  { id: 'ghost', label: 'Duch Wzbraniający', type: 'avoidant', stage: 'resistance' },
  { id: 'actor', label: 'Aktor Afiliacyjny', type: 'compliant', stage: 'camouflage' },
  { id: 'wanderer', label: 'Zbłąkany Kartograf', type: 'searching', stage: 'navigation' },
  { id: 'observer', label: 'Obserwator Anonimiczny', type: 'analytic', stage: 'passive' },
  { id: 'echo', label: 'Niemy Echemistrz', type: 'reactive', stage: 'resonance' },
]
</script>

<template>
  <MaskBoard :colors="colors" :masks="masks" />
</template>