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
    <li><RouterLink to="@/pages/index.vue" class="text-red-500 underline"> Accueil </RouterLink></li>
    <li><RouterLink to="@/pages/accordeon.vue" class="text-red-500 underline"> Accordéon </RouterLink></li>
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
