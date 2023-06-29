<script setup lang="ts">
  import { type PropType } from 'vue'
  import HomeComponent from '../components/HomeComponent.vue'

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
  <main>
    <HomeComponent 
      :home-text="homeText"
      :home-buttons="homeButtons"
      :home-isaac="homeIsaac"
    />
  </main>
</template>

<style lang="scss">
</style>