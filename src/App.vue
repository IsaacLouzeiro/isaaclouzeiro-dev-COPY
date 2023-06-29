<script setup lang="ts">
  import { ref } from 'vue';
  import { RouterView } from 'vue-router'
  import NavbarComponent from './components/shared/NavbarComponent/NavbarComponent.vue'

  interface HomeList {
    name: string;
    icon: string;
    link: string;
  }

  interface AboutEducation {
    name: string;
    institute: string;
    in: string;
    out: string;
  }

  interface WorkProjects {
    title: string;
    github: string;
    link: string;
    img: string;
    about: string;
  }

  interface WorkBtn {
    icon: string;
    text: string;
    minText: string;
    link: string;
  }

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

  // navbar content
  const navItems = ref<HomeList[]>([
    {
      name: "Home",
      icon: "fa-house-chimney",
      link: "home"
    },
    {
      name: "About",
      icon: "fa-book-open-reader",
      link: "about"
    },
    {
      name: "Work",
      icon: "fa-code",
      link: "work",
    },
    {
      name: "Contact",
      icon: "fa-envelope",
      link: "contact"
    }
  ])

  // home content
  const homeText = ref([
    "Welcome to my website.",
    "Recently my passion is creating websites. I'm very curious and constantly searching for new things to learn."
  ])
  const homeButtons = ref<HomeList[]>([
    {
        name: 'Web Resume',
        icon: 'fa-solid fa-window-maximize',
        link: 'https://resume-curriculo.netlify.app'
    },
    {
        name: 'Codepen',
        icon: 'fa-brands fa-codepen',
        link: 'https://codepen.io/isaaclouzeiro'
    },
    {
        name: 'Github',
        icon: 'fa-brands fa-github',
        link: 'https://github.com/IsaacLouzeiro'
    }
  ])
  const homeIsaac = ref(['Isaac Louzeiro', 'Web Developer'])

  // about content
  const aboutTitle = ref('About')
  const aboutText = ref([
      "Hi! My name is Isaac, I'm passionate about Web Development.",
      "I like to learn about this subject, and show my skills in this area, by posting them on my Github, Codepen, and Web Portfolio.",
      "I am a very curious person, who likes to learn and expand my knowledge. Every day I try to improve my skills so that I can grow professionally."
  ])
  const aboutEducationTitle = ref('Education')
  const aboutEducation = ref<AboutEducation[]>([ 
      { 
          name: 'Technology Degree, Information Technology Management', 
          institute: 'College of Technology of Franco da Rocha', 
          in: '02/2023', 
          out: '12/2025' 
      },
      { 
          name: 'Vocational Course, FullStack Web Programming', 
          institute: 'Instituto Proa / Senac', 
          in: '03/2021', 
          out: '07/2021' 
      },
      { 
          name: 'Technical Course, Systems Development', 
          institute: 'State Technical School Professor Basilídes de Godoy', 
          in: '07/2019', 
          out: '12/2020' 
      }
  ])
  const aboutEducationBtn = ref(['fa-linkedin', 'https://linkedin.com/in/isaac-louzeiro', 'See more'])
  const aboutSkills = ref([ 'HTML5', 'CSS3', 'JavaScript', 'Bootstrap', 'Sass', 'Vue', 'Angular', 'TypeScript', 'Wordpress', 'UI/UX', 'SPA', 'Git', 'Github', 'Adobe XD', 'Figma', 'Scrum' ])

// my work content
const workTitle = ref('My Work')
const workProjects = ref<WorkProjects[]>([
    {
        title: 'FaverTI',
        github: 'https://github.com/IsaacLouzeiro/faverti',
        link: 'https://faverti.vercel.app/',
        img: "faverti",
        about: 'Website that talks about IT Green.'
    },
    {
        title: 'CriptoMoeda',
        github: 'https://github.com/IsaacLouzeiro/preco-criptomoedas',
        link: 'https://criptomoeda.netlify.app/',
        img: "criptomoeda",
        about: 'Showing cryptocurrencies values from an API with Vue 3 and Axios.'
    },
    {
        title: 'Spotify Clone',
        github: 'https://github.com/IsaacLouzeiro/spotify-vue-clone',
        link: 'https://spotify-copia.netlify.app/',
        img: "spotify",
        about: 'Spotify Web Audio Player clone in Vue Js, created to practice my abilities.'
    },
    {
        title: 'Untitled Blog',
        github: 'https://github.com/IsaacLouzeiro/blog-angular',
        link: 'https://blog-angular-tau.vercel.app/',
        img: "blog",
        about: 'A blog project created with Angular based on Dribbble layout.'
    },
    {
        title: 'Finans',
        github: 'https://github.com/IsaacLouzeiro/finans',
        link: 'https://isaaclouzeiro.github.io/finans/',
        img: "finans",
        about: 'Fictitious website of finance.'
    },
    {
        title: 'Resume',
        github: 'https://github.com/IsaacLouzeiro/resume',
        link: 'https://resume-curriculo.netlify.app',
        img: "resume",
        about: 'Web resume, a relaxed way of show my professional side.'
    }
])
const workBtn = ref<WorkBtn[]>([
    {
        icon: 'fa-brands fa-codepen',
        text: 'Codepen Projects',
        minText: 'Codepen Proj.',
        link: 'https://codepen.io/isaaclouzeiro'
    },
    {
        icon: 'fa-brands fa-github',
        text: 'Github Projects',
        minText: 'Github Proj.',
        link: 'https://github.com/IsaacLouzeiro'
    }
])

// contact content
const contactTitle = ref('Contact')
const contactSocial = ref<ContactSocial[]>([
  {
      name: 'Github',
      link: 'https://github.com/isaaclouzeiro',
      editLink: 'github.com/isaaclouzeiro',
      icon: 'fa-brands fa-github'
  },
  {
      name: 'Linkedin',
      link: 'https://linkedin.com/in/isaac-louzeiro',
      editLink: 'linkedin.com/in/isaac-louzeiro',
      icon: 'fa-brands fa-linkedin'
  },
  {
      name: 'Codepen',
      link: 'https://codepen.io/isaaclouzeiro',
      editLink: 'codepen.io/isaaclouzeiro',
      icon: 'fa-brands fa-codepen'
  },
  {
      name: 'Instagram',
      link: 'https://instagram.com/isaac.louzeiro',
      editLink: 'instagram.com/isaac.louzeiro',
      icon: 'fa-brands fa-instagram'
  }
])
const contactForm = ref<ContactForm>({
  name: 'Name',
  email: 'E-mail',
  message: 'Message'
})
const contactAlert = ref<ContactAlert>({
  errorAlert: 'There was an error completing the form',
  errorAlertIcon: 'fa-triangle-exclamation',
  successAlert: 'Message was sent successfully',
  successAlertIcon: 'fa-circle-check'
})
const contactBtn = ref('Send Message')
</script>

<template>
  <NavbarComponent :nav-items="navItems" />
  <RouterView 
    :home-text="homeText"
    :home-buttons="homeButtons"
    :home-isaac="homeIsaac"

    :about-title="aboutTitle"
    :about-text="aboutText"
    :about-education-title="aboutEducationTitle"
    :about-education="aboutEducation"
    :about-education-btn="aboutEducationBtn"
    :about-skills="aboutSkills"

    :work-title="workTitle"
    :work-btn="workBtn"
    :work-projects="workProjects"

    :contact-title="contactTitle"
    :contact-form="contactForm"
    :contact-alert="contactAlert"
    :contact-btn="contactBtn"
    :contact-social="contactSocial"
  />
</template>

<style lang="scss">
#app {
  display: flex;
  flex-direction: row;
}
</style>
