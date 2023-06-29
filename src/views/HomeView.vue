<script setup lang="ts">
  import HomeComponent from '../components/HomeComponent.vue'

  defineProps({
    homeText: Array,
    homeButtons: Array,
    homeIsaac: Array
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