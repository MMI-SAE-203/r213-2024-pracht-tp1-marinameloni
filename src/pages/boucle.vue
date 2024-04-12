<script setup lang="ts">
import { ref } from 'vue';

const sectionsData = [
  {
    label: 'bouton 1',
    texte: `texte panneau 1 Lorem ipsum dolor sit amet consectetur adipisicing elit. 
    Quod, quibusdam natus. Doloremque, quas voluptatum.`
  },
  {
    label: 'bouton 2',
    texte: `texte panneau 2 Amet alias provident quos quis, 
    Officia ut ab dolores quos dolorem accusamus ad,
    consectetur unde minima, ipsum eligendi inventore id
    labore, laborum rerum laboriosam corrupti iste.
    Distinctio, perspiciatis!`
  },
  {
    label: 'bouton 3',
    texte: `texte panneau 3 Repudiandae corporis voluptates, 
    odit reprehenderit sint pariatur at voluptatum, cumque
    quia sit eligendi ex culpa eos, alias magnam molestiae
    id modi accusantium ipsa eveniet accusamus. Tempora 
    quis corporis et nam.`
  }
];

const accordionsOpen = ref(sectionsData.map(() => false));
</script>

<template>
  <h1>Boucles</h1>
  <section v-for="({ label, texte }, key) in sectionsData" :key="key">
    <button @click="accordionsOpen[key] = !accordionsOpen[key]">{{ label }}</button>
    <p v-show="accordionsOpen[key]">{{ texte }}</p>
  </section>
</template>