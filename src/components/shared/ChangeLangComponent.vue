<script setup lang="ts">
  import type { PropType } from 'vue';

  interface Language {
    showName: string;
    name: string;
    isCheck: boolean; 
  }

  defineProps({
    language: {
      type: Array as PropType<Language[]>,
      required: true
    }
  })
</script>

<template>
  <div class="btn-group dropend language-dropdown">
    <button type="button" class="btn lang" data-bs-toggle="dropdown" aria-expanded="false">
      <font-awesome-icon icon="fa-solid fa-language" />
    </button>
    <ul class="dropdown-menu">
      <li 
        class="dropdown-item p-0" 
        v-for="(lang, index) in language" 
        :key="index" 
        :class="{ disabled: lang.isCheck }"

        @click="$emit('change-to', lang.showName)"
      >
        <button type="button">{{ lang.showName }}</button>
      </li>
    </ul>
  </div>
</template>

<style scoped lang="scss">
@import '../../assets/colors.scss';

button, .button {
  padding: 0;
  margin: 0;
  background-color: transparent;
  border: none;
  color: $color-l-1;
}

.language-dropdown {
  position: absolute;
  top: 1.5rem;
  right: 2rem;
  font-size: 2rem;
  z-index: 999;

  button.lang {
      color: $color-l-1;
      svg {
        font-size: 2rem;
      }
  }

  .dropdown-menu {
     background-color: $color-l-3;

     .dropdown-item {
        button {
          width: 100%;
          padding: .25rem;

          &:hover {
            color: $color-d-1;
          }
        }

        &.disabled button {
          background-color: rgba($color-l-1, .5);
        }
     }
  }
}
</style>