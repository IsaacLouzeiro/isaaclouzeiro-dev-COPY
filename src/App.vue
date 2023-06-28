<script setup lang="ts">
  import { ref } from 'vue';
import { RouterView } from 'vue-router'
  import NavbarComponent from './components/shared/NavbarComponent.vue'

  interface NavType {
    target: string;
    icon: string;
    name: string;
  }

  const navItems = ref<NavType[]>([
    {
      target: "home",
      icon: "fa-house-chimney",
      name: "Home"
    },
    {
      target: "about",
      icon: "fa-book-open-reader",
      name: "About"
    },
    {
      target: "work",
      icon: "fa-code",
      name: "Work"
    },
    {
      target: "contact",
      icon: "fa-envelope",
      name: "Contact"
    }
  ])
</script>

<template>
  <NavbarComponent :nav-items="navItems" />
  <RouterView />
</template>

<style lang="scss">
#app {
  display: flex;
  flex-direction: row;
}
</style>
