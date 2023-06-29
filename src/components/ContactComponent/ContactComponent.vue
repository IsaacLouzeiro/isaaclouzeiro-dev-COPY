<script setup lang="ts">
import type { PropType } from 'vue';
import FormComponent from './FormComponent.vue';
import ButtonSocialComponent from './ButtonSocialComponent.vue';

interface ContactSocial {
  name: string;
  link: string;
  editLink: string;
  icon: string;
}

interface ContactAlert {
  errorAlert: string;
  errorAlertIcon: string;
  successAlert: string;
  successAlertIcon: string;
}

interface ContactForm {
  name: string;
  email: string;
  message: string;
}

defineProps({
  contactTitle: String,
  contactSocial: {
    type: Array as PropType<ContactSocial[]>,
    required: true
  },
  contactForm: {
    type: Object as PropType<ContactForm>,
    required: true
  },
  contactAlert: {
    type: Object as PropType<ContactAlert>,
    required: true
  },
  contactBtn: String
})
</script>

<template>
  <section id="contact" class="contact-content container px-0">
    <div class="w-100 h-100 row align-items-center contact-content__box-items">
      <h2 class="text-center">{{ contactTitle }}</h2>

      <FormComponent
      :contact-form="contactForm"
      :contact-alert="contactAlert"
      :contact-btn="contactBtn"
      />

      <div class="socialCont row g-0">
        <ButtonSocialComponent 
          v-for="(social, index) in contactSocial" 
          :key="index"
          :name="social.name"
          :icon="social.icon"
          :link="social.link"
          :edit-link="social.editLink"
          class="col-md-6"
        />
      </div>
    </div>
  </section>
</template>

<style scoped lang="scss">
@import '../../assets/colors.scss';

.contact-content {
  padding: 5rem 0;

  &__box-items {
    h2 {
       color: $color-l-3;
    }
    
    .socialCont {
      max-width: 800px;
      margin: auto;
    }
  }
}
</style>