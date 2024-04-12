<script setup lang="ts">
import { onErrorCaptured, ref, Transition } from 'vue'
import { RouterLink, RouterView } from 'vue-router/auto'

onErrorCaptured((err, instance, info) => {
  console.error('erreur : ', err, '\ninfo : ', info, '\ncomposant : ', instance)
  return true
})
const menuIsOpen = ref(false);
</script>

<template>
  <header>
    <button
      aria-controls="mainNav"
      aria-expanded="menuIsOpen"
      class="rounded-full border-2 border-red-600 bg-red-300 px-2"
      @pointerdown="menuIsOpen = !menuIsOpen">
      menu
    </button>
    <Transition
      class="transition-transform duration-1000"
      enter-from-class="-translate-x-full"
      enter-to-class="translate-x-0"
      leave-active-class="-translate-x-full"
    >
      <nav id="mainNav" v-show="menuIsOpen">
        <ul>
          <li><router-link to="/" class="text-red-500 underline"> Accueil </router-link></li>
          <li><router-link to="/accordeon" class="text-red-500 underline"> Accordéon </router-link></li>
          <li><a href="#">item 3</a></li>
        </ul>
      </nav>
    </Transition>
  </header>
  <RouterView v-slot="{ Component }">
    <Suspense>
      <component :is="Component" />
    </Suspense>
  </RouterView>
</template>