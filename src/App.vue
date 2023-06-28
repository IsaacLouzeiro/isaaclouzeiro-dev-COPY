<script setup lang="ts">
  import { ref } from 'vue';
import { RouterView } from 'vue-router'
  import NavbarComponent from './components/shared/NavbarComponent.vue'

  type NavType = {
    icon: string;
    name: string;
  }

  const navItems = ref<NavType[]>([
    {
      icon: "fa-house-chimney",
      name: "Home"
    },
    {
      icon: "fa-book-open-reader",
      name: "About"
    },
    {
      icon: "fa-code",
      name: "Work"
    },
    {
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
