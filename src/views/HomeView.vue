<script setup lang="ts">
  import { type PropType } from 'vue'
  import HomeComponent from '../components/HomeComponent/HomeComponent.vue'
  import AboutComponent from '../components/AboutComponent/AboutComponent.vue'

  interface HomeList {
    name: string;
    icon: string; 
    link: string;
  }

  defineProps({
    homeText: {
      type: Array as PropType<string[]>,
      required: true
    },
    homeButtons: {
      type: Array as PropType<HomeList[]>,
      required: true
    },
    homeIsaac: {
      type: Array as PropType<string[]>,
      required: false
    }
  })
</script>

<template>
  <main data-bs-spy="scroll" data-bs-target="#navbar" data-bs-smooth-scroll="true" tabindex="0">
    <HomeComponent 
      :home-text="homeText"
      :home-buttons="homeButtons"
      :home-isaac="homeIsaac"
    />

    <AboutComponent />
  </main>
</template>

<style lang="scss">
</style>