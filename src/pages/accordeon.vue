<script setup lang="ts">
import { ref } from 'vue';

const maVar = ref(true)
</script>

<template>
  <button class="button1" @click="maVar = false">Cacher</button>
  <button class="button1" @click="maVar = true">Montrer</button>
  <button class="button1" @click="maVar = !maVar">Bascule</button>
  <h1 v-show="maVar"
  class="text-2xl">Des lasagnes...   <img src="/public/favicon.ico" alt="garfield"></h1>

</template>