<script setup lang="ts">
import { onMounted, toRefs } from 'vue';
import TagCloud from 'TagCloud';

const props = defineProps({
  aboutSkills: {
    type: Array as () => string[],
    required: true
  }
})

onMounted(() => {
  const container = '.tagcloud';
  const { aboutSkills } = toRefs(props);
  const texts = aboutSkills.value;
  const options = {
      maxSpeed: 'fast',
      radius: 140
  };

  TagCloud(container, texts, options);
})

</script>

<template>
  <div class="tagcloud d-inline-block"></div>
</template>

<style lang="scss" scoped>
.tagcloud {
  font-size: 1.2rem;
}
</style>