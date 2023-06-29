<script setup lang="ts">
  import type { PropType } from 'vue';
import ButtonComponent from '../shared/ButtonComponent.vue';
  import CardComponent from './CardComponent.vue';

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
  <section id="work" class="work-content container px-0">
    <div class="w-100 h-100 row align-items-center work-content__box-items">
      <h2>{{ workTitle }}</h2>

      <ul class="row justify-content-center p-0 m-0 mt-3">
        <li 
          v-for="(item, index) in workProjects"
          :key="index"
          class="col-md-6 col-lg-4"
        >
          <CardComponent 
            :title="item.title"
            :github="item.github"
            :about="item.about"
            :img="item.img"
            :link="item.link"
          />
        </li>
      </ul>

      <div class="d-flex justify-content-between">
        <ButtonComponent 
          v-for="(item, index) in workBtn"
          :key="index"
          :name="item.text"
          :icon="item.icon"
          :link="item.link"
          class="d-none d-md-inline-block"
        />
        <ButtonComponent 
          v-for="(item, index) in workBtn"
          :key="index"
          :name="item.text"
          :link="item.link"
          class="d-inline-block d-md-none"
        />
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
@import '../../assets/colors.scss';

.work-content {
  padding: 5rem 0;

  &__box-items {
    h2 {
      color: $color-l-3;
    }
  }
}
</style>