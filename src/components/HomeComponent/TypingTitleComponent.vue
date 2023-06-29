<script setup lang="ts">
  defineProps({
    title: String,
    letter: Number,
    time: Number
  })
</script>

<template>
  <h2 class="typingTitle">{{ title }}</h2>
</template>

<style lang="scss" scoped>
.typingTitle {
    width: 21ch;
    animation: typing 2s steps(21), blink .5s step-end infinite alternate;
    white-space: nowrap;
    overflow: hidden;
    border-right: 3px solid;
}

@keyframes typing {
    from {
        width: 0;
    }
}

@keyframes blink {
    50% {
        border-color: transparent;
    }
}
</style>