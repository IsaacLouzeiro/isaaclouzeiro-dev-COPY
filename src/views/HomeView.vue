<script setup lang="ts">
  import { type PropType } from 'vue'
  import HomeComponent from '../components/HomeComponent/HomeComponent.vue'
  import AboutComponent from '../components/AboutComponent/AboutComponent.vue'
  import WorkComponent from '../components/WorkComponent/WorkComponent.vue'

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

  interface WorkProjects {
    title: string;
    github: string;
    link: string;
    img: string;
    about: string;
  }

  interface WorkBtn {
    icon: string;
    text: string;
    minText: string;
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
    },
    workTitle: String,
    workProjects: {
      type: Array as PropType<WorkProjects[]>,
      required: true
    },
    workBtn: {
      type: Array as PropType<WorkBtn[]>,
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

    <WorkComponent 
      :work-title="workTitle"
      :work-btn="workBtn"
      :work-projects="workProjects"
    />
  </main>
</template>

<style lang="scss">
</style>