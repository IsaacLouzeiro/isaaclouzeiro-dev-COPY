<script setup lang="ts">
  import type { PropType } from 'vue';
  import ButtonComponent from '../shared/ButtonComponent.vue';
  import TagCloudComponent from './TagCloudComponent.vue';

  interface AboutEducation {
    name: string;
    institute: string;
    in: string;
    out: string;
  }

  defineProps({
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
  <section id="about" class="about-content container">
    <div class="w-100 h-100 row align-items-center">
      <div class="about-content__text-box col-lg-7">
        <h2>{{ aboutTitle }}</h2>
        <p
          v-for="(text, index) in aboutText"
          :key="index"
        >{{ text }}
        </p>

        <h4>{{ aboutEducationTitle }}</h4>
        <p 
          v-for="(item, index) in aboutEducation"
          :key="index"
          class="education"
        >
          <span>{{ item.name }} | {{ item.in }} - {{ item.out }}</span>
          {{ item.institute }}
        </p>

        <ButtonComponent 
          :icon="aboutEducationBtn[0]"
          :link="aboutEducationBtn[1]"
          :name="aboutEducationBtn[2]"
          icontType="brands"
        />
      </div>

      <div class="about-content__skill-box col-lg-5 text-center">
        <TagCloudComponent 
          :aboutSkills="aboutSkills"
        />
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import '../../assets/colors.scss';

.about-content {
  padding: 5rem 0;

  &__text-box {
    h2,h4 {
      color: $color-l-3;
    }

    p {
      font-size: 1.1rem;
    }

    .education {
      font-weight: 300;
      span {
        font-weight: 400;
        display: block;
      }
    }
  }

  &__skill-box {
    @media only screen and (max-width: 992px) {
      margin-top: 3rem;
    }
  }
}
</style>