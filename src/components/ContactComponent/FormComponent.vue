<script setup lang="ts">
  import emailjs from '@emailjs/browser'
  import { ref, type PropType } from 'vue';

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

  const successIsVisible= ref(false)
  const errorIsVisible= ref(false)

  const sendEmail= (e: any) => {
    emailjs.sendForm('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', e.target, 'YOUR_PUBLIC_KEY')
    .then((result) => {
      console.log('SUCCESS!', result.text);
      successIsVisible.value = true
      setInterval(() => {
        successIsVisible.value = false
      }, 4000);

    }, (error) => {
      console.log('FAILED...', error.text);
      errorIsVisible.value = true
      setInterval(() => {
        errorIsVisible.value = false
      }, 4000);
    });
  }
</script>

<template>
  <form ref="form" @submit.prevent="sendEmail($event)" class="mt-3">
    <label for="nameCont">
      <span>{{ contactForm.name }}</span><br>
      <input type="text" name="from_name" id="nameCont" required>
    </label>

    <label for="emailCont">
      <span>{{ contactForm.email }}</span><br>
      <input type="email" name="reply_to" id="emailCont" required>
    </label>

    <label for="messageCont">
      <span>{{ contactForm.message }}</span><br>
      <textarea id="messageCont" rows="5" name="message" required></textarea>
    </label>

    <button type="submit" class="btn">{{ contactBtn }}</button>

    <div class="alert bg-danger mt-3" id="errorAlert" v-show="errorIsVisible">
      <font-awesome-icon :icon="`fa-solid ${contactAlert.errorAlertIcon}`" class="me-2" /> {{ contactAlert.errorAlert }}
    </div>
    <div class="alert bg-success mt-3" id="successAlert" v-show="successIsVisible">
      <font-awesome-icon :icon="`fa-solid ${contactAlert.successAlertIcon}`" class="me-2" /> {{ contactAlert.successAlert }}
    </div>
  </form>
</template>

<style scoped lang="scss">
@import '../../assets/colors.scss';

* { color: $color-l-1; }

form {
  max-width: 800px;
  margin: auto;
  padding-bottom: 2em;

  label {
    display: block;
    padding: .5em 0;
    font-size: 1.2rem;

    input, textarea {
      background: rgba(0,0,0,0);
      border: 0;
      border-bottom: 2px solid;
      width: 100%;
      max-height: 150px;
      outline: none;
      font-weight: 300;
    }
  }

  button {
    background-color: $color-d-2;
    margin-top: 1em;
    color: $color-l-1;
    &:hover { background-color: $color-d-2; opacity: .7; }
  }
}
</style>