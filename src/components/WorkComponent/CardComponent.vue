<script setup lang="ts">
  // images
  import blog from '../../assets/img/projects/blog.png'
  import faverti from '../../assets/img/projects/faverti.png'
  import criptomoeda from '../../assets/img/projects/criptoMoeda.png'
  import spotify from '../../assets/img/projects/spotifyClone.png'
  import resume from '../../assets/img/projects/resume.png'
  import finans from '../../assets/img/projects/finans.png'

  import { ref } from 'vue';

  const props = defineProps({
    title: String,
    github: String,
    link: String,
    img: String,
    about: String,
  })

  const image = ref('')

  if(props.img == 'faverti') {
    image.value = faverti
  } else if(props.img == 'criptomoeda') {
    image.value = criptomoeda
  } else if(props.img == 'resume') {
    image.value = resume
  } else if(props.img == 'blog') {
    image.value = blog
  } else if(props.img == 'spotify') {
    image.value = spotify
  } else if(props.img == 'finans') {
    image.value = finans
  }
</script>

<template>
  <div class="col-lg-4 col-md-6 portfolio-item px-3 pt-3">
    <div class="d-flex justify-content-between portfolio-item__header">
      <a :href="link" target="_blank" class="nav-link">{{ title }}</a>

      <a :href="github" target="_blank"><font-awesome-icon :icon="['fab', 'github']" /></a>
    </div>

    <div class="portfolio-item__wrap">
      <img
          :src="image"
          alt="aqui é uma imagem"
          class="img-fluid"
      />

      <div class="portfolio-info">
        <h4>{{ title }}</h4>
        <p>{{ about }}</p>
      </div>
      <div class="portfolio-links">
        <a :href="link" class="portfolio-lightbox me-2" title="Website" target="_blank"><font-awesome-icon :icon="['fas', 'window-maximize']" /></a>
        <a :href="github" class="portfolio-lightbox ms-2" title="Github" target="_blank"><font-awesome-icon :icon="['fab', 'github']" /></a>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
@import '../../assets/colors.scss';

.portfolio-item {
  width: 100%;
  margin-bottom: 30px;
  background-color: rgba($color-l-1, .5);
  border-radius: .5rem;

  &__header {
    a {
      color: $color-d-2 !important;
      font-size: 1.3rem;
    }

    svg {
      color: $color-d-1;
      font-size: 1.8rem;
    }
  }

  &__wrap {
    transition: 0.3s;
    position: relative;
    overflow: hidden;
    z-index: 1;
    cursor: pointer;
    bottom: -15px;
    border-radius: 5px;

    img {
      width: 100%;
      max-height: 270.56px;
    }

    .portfolio-info {
      opacity: 0;
      position: absolute;
      top: 10%;
      left: 0;
      right: 0;
      text-align: center;
      z-index: 3;
      transition: all ease-in-out 0.3s;

      h4 {
        font-size: 20px;
        color: $color-l-1;
        font-weight: 600;
      }

      p {
        color: $color-l-1;
        font-size: 14px;
      }
    }

    .portfolio-links {
      opacity: 0;
      left: 0;
      right: 0;
      bottom: 10%;
      text-align: center;
      z-index: 5;
      position: absolute;
      transition: all ease-in-out 0.3s;

      a {
        color: rgba($color-l-1, 0.6);
        margin: 0 2px;
        font-size: 28px;
        display: inline-block;
        transition: 0.3s;
        position: relative;
        top: 1rem;

        &:hover {
          color: $color-l-1;
        }
      }
    }

    &::before {
      content: "";
      background: rgba($color-d-2, 0.9);
      position: absolute;
      left: 30px;
      right: 30px;
      top: 30px;
      bottom: 30px;
      transition: all ease-in-out 0.3s;
      z-index: 2;
      opacity: 0;
    }

    &:hover::before {
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      opacity: 1;
    }

    &:hover .portfolio-info {
      opacity: 1;
      top: calc(50% - 48px);
    }

    &:hover .portfolio-links {
      opacity: 1;
      bottom: calc(50% - 50px);
    }
  }
}
</style>