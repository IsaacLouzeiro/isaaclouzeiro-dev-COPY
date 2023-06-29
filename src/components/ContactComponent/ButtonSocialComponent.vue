<script setup lang="ts">
  defineProps({
    name: String,
    link: String,
    editLink: String,
    icon: String,
  })
</script>

<template>
  <a :href="link" target="_blank" class="d-flex align-items-center nav-link px-3">
    <font-awesome-icon :icon="`fa-brands ${icon}`" />

    <div class="d-flex flex-column ps-2">
      <span>{{ name }}</span>
      <p>{{ editLink }}</p>
    </div>
  </a>
</template>

<style scoped lang="scss">
a {
  text-decoration: none;
  margin: 1em 0;

  svg {
    font-size: 2.5em;
  }

  div {
    span {
        font-size: 1.3em;
        margin-bottom: -.3em;
    }

    p {
        font-weight: 300;
        text-decoration: none;
        padding: 0;
        margin: 0;
    }
  }
}
</style>