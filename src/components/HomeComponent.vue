<script setup lang="ts">
import ButtonComponent from './shared/ButtonComponent.vue';

interface HomeButton {
  name: string;
  icon: string; 
  link: string;
}

  defineProps({
    homeText: Array,
    homeButtons: {
      type: Array as () => HomeButton[],
      required: true
    },
    homeIsaac: Array
  })

</script>

<template>
  <section id="home" class="home-content container">
    <div class="w-100 h-100 row align-items-center justify-content-center">
      <div class="home-content__text-box col-12 col-md-8 col-lg-7">
        <h2>{{ homeText && homeText[0] }}</h2>
        <p>{{ homeText && homeText[1] }}</p>

        <ButtonComponent
          v-for="(item, index) in homeButtons"
          :key="index"
          :name="item.name"
          :icon="item.icon"
          :link="item.link"
          class="me-2 mb-2"
        />
      </div>

      <div class="home-content__author-box col-12 col-md-4 text-center">
        <img src="@/assets/img/me.jpeg" alt="Author image" class="img-fluid ">
        <h3>{{ homeIsaac && homeIsaac[0] }}</h3>
        <p>{{ homeIsaac && homeIsaac[1] }}</p>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import '../assets/colors.scss';

.home-content {
  min-height: 500px;

  @media only screen and (max-width: 767.98px) {
    min-height: 700px;
  }

  @media only screen and (max-width: 575.98px) {
    min-height: 800px;
  }

  &__text-box {
    h2 {
      font-size: 2rem;
    }

    p {
      font-size: 1.2rem;
      color: $color-l-3;
    }
  }

  &__author-box {
    img {
      width: 10rem;
      border-radius: 5rem;
      border: 5px solid $color-l-3;
      margin-bottom: .6rem;
    }

    h3 {
      font-size: 1.8rem;
    }

    p {
      font-size: 1.3rem;
      font-weight: 300;
      font-style: italic;
    }
  }
}
</style>