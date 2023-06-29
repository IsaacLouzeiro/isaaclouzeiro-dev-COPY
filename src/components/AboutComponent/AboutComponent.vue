<script setup lang="ts">
  import ButtonComponent from '../shared/ButtonComponent.vue';
  import TagCloudComponent from './TagCloudComponent.vue';
</script>

<template>
  <section id="about" class="about-content container">
    <div class="w-100 h-100 row align-items-center">
      <div class="about-content__text-box col-lg-7">
        <h2>About</h2>
        <p>Hi! My name is Isaac, I'm passionate about Web Development.</p>
        <p>I like to learn about this subject, and show my skills in this area, by posting them on my Github, Codepen, and Web Portfolio.</p>
        <p>I am a very curious person, who likes to learn and expand my knowledge. Every day I try to improve my skills so that I can grow professionally.</p>

        <h4>Education</h4>
        <p class="education">
          <span>Technology Degree, Information Technology Management | 02/2023 - 12/2025</span>
          College of Technology of Franco da Rocha
        </p>
        <p class="education">
          <span>Vocational Course, FullStack Web Programming | 03/2021 - 07/2021</span>
          Instituto Proa / Senac
        </p>
        <p class="education">
          <span>Technical Course, Systems Development | 07/2019 - 12/2020</span>
          State Technical School Professor Basilídes de Godoy
        </p>

        <ButtonComponent 
          link="https://www.linkedin.com/in/isaac-louzeiro/"
          name="See more"
          icon="fa-linkedin"
          icontType="brands"
        />
      </div>

      <div class="about-content__skill-box col-lg-5 text-center">
        <TagCloudComponent 
          :aboutSkills="[ 'HTML5', 'CSS3', 'JavaScript', 'Bootstrap', 'Sass', 'Vue', 'Angular', 'TypeScript', 'Wordpress', 'UI/UX', 'SPA', 'Git', 'Github', 'Adobe XD', 'Figma', 'Scrum' ]"
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