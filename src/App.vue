<script setup lang="ts">
  import { ref } from 'vue';
  import { RouterView } from 'vue-router'
  import NavbarComponent from './components/shared/NavbarComponent.vue'

  interface NavType {
    target: string;
    icon: string;
    name: string;
  }

  // navbar content
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

  // home content
  const homeText = ref([ 
    "Welcome to my website.",
    "Recently my passion is creating websites. I'm very curious and constantly searching for new things to learn."
  ])

  const homeButtons = ref([
    {
        name: 'Web Resume',
        icon: 'fa-solid fa-window-maximize',
        link: 'https://resume-curriculo.netlify.app'
    },
    {
        name: 'Codepen',
        icon: 'fa-brands fa-codepen',
        link: 'https://codepen.io/isaaclouzeiro'
    },
    {
        name: 'Github',
        icon: 'fa-brands fa-github',
        link: 'https://github.com/IsaacLouzeiro'
    }
  ])

  const homeIsaac = ref(['Isaac Louzeiro', 'Web Developer'])
</script>

<template>
  <NavbarComponent :nav-items="navItems" />
  <RouterView 
    :home-text="homeText"
    :home-buttons="homeButtons"
    :home-isaac="homeIsaac"
  />
</template>

<style lang="scss">
#app {
  display: flex;
  flex-direction: row;
}
</style>
