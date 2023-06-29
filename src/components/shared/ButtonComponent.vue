<script setup lang="ts">
  defineProps({
    link: String,
    icon: String,
    name: String
  })
</script>

<template>
  <a 
    :href="link"
    target="_blank"
    class="btn py-2"
  >
    <font-awesome-icon :icon="`fa-solid ${icon}`" />{{ name }}
  </a>
</template>

<style lang="scss" scoped>
@import '../../assets/colors.scss';

a.btn {
  background-color: $color-d-2;
  color: $color-l-1;

  svg {
    margin-right: .5rem;
    font-size: 1.2rem;
  }
}
</style>