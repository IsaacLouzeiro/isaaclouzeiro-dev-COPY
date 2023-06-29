<script setup lang="ts">
  import { type PropType } from 'vue'
  import HomeComponent from '../components/HomeComponent/HomeComponent.vue'
  import AboutComponent from '../components/AboutComponent/AboutComponent.vue'

  interface HomeList {
    name: string;
    icon: string; 
    link: string;
  }

  interface AboutEducation {
    name: string;
    institute: string;
    in: string;
    out: string;
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
    },
    aboutTitle: String,
    aboutText: {
      type: Array as PropType<string[]>,
      required: true
    },
    aboutEducationTitle: String,
    aboutEducation: {
      type: Array as PropType<AboutEducation[]>,
      required: true
    },
    aboutEducationBtn: {
      type: Array as PropType<string[]>,
      required: true
    },
    aboutSkills: {
      type: Array as PropType<string[]>,
      required: true
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

    <AboutComponent 
      :about-title="aboutTitle"
      :about-text="aboutText"
      :about-education-title="aboutEducationTitle"
      :about-education="aboutEducation"
      :about-education-btn="aboutEducationBtn"
      :about-skills="aboutSkills"
    />
  </main>
</template>

<style lang="scss">
</style>