<script setup lang="ts">
  defineProps({
    name: String,
    icon: String,
    link: String
  })
</script>

<template>
  <li
    class="nav-item"
  >
    <a :href="`#${link}`" class="btn">
      <font-awesome-icon :icon="`fa-solid ${icon}`" />
    </a>

    <span>{{ name }}</span>
  </li>
</template>

<style lang="scss" scoped>
@import '../../../assets/colors.scss';

li {
  margin: .5rem 0;
  position: relative;

  a.btn {
    width: 3.4rem;
    height: 3rem;
    display: flex;
    justify-content: center;
    align-items: center;
    border: none;
    background-color: rgba($color-l-1, .5);
    color: $color-d-2;
    position: relative;
    z-index: 1;

    &:hover,
    &.active {
      background-color: $color-d-2;
      color: $color-l-1;
    }

    svg {
      font-size: 1.4rem;
    }
  }

  a:hover ~ span {
      opacity: 1;
      left: 115%;
  }

  span {
    opacity: 0;
    display: inline-block;
    position: absolute;
    left: 0;
    top: 20%;
    background-color: $color-d-2;
    padding: .2rem 1rem;
    border-radius: .2rem;
    transition: all .5s;
    z-index: 0;
  }
}
</style>