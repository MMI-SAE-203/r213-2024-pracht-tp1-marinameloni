<script setup lang="ts">
import { onErrorCaptured } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'

onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})
</script>

<template>
  <header>
    <button
  aria-controls="mainNav"
  aria-expanded="true"
  class="rounded-full border-2 border-red-600 bg-red-300 px-2">
  menu
  </button>
<nav id="mainNav">
  <ul>
        <li><router-link to="/" class="text-red-500 underline"> Accueil </router-link></li>
        <li><router-link to="/accordeon" class="text-red-500 underline"> Accordéon </router-link></li>
    <li><a href="#">item 3</a></li>
  </ul>
</nav>
  </header>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
</template>
