<script setup lang="ts">
  import { onMounted, reactive, ref } from 'vue';
  import { RouterView } from 'vue-router'
  import NavbarComponent from './components/shared/NavbarComponent/NavbarComponent.vue'
import ChangeLangComponent from './components/shared/ChangeLangComponent.vue';

  interface Language {
    showName: string;
    name: string;
    isCheck: boolean; 
  }

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

  // language content
  const language = ref<Language[]>([])

  // navbar content
  const navItems = ref<HomeList[]>([])

  // home content
  const homeText = ref<string[]>([])
  const homeButtons = ref<HomeList[]>([])
  const homeIsaac = ref<string[]>([])

  // about content
  const aboutTitle = ref('')
  const aboutText = ref<string[]>([])
  const aboutEducationTitle = ref('')
  const aboutEducation = ref<AboutEducation[]>([])
  const aboutEducationBtn = ref<string[]>([])
  const aboutSkills = ref<string[]>([ 'HTML5', 'CSS3', 'JavaScript', 'Bootstrap', 'Sass', 'Vue', 'Angular', 'TypeScript', 'Wordpress', 'UI/UX', 'SPA', 'Git', 'Github', 'Adobe XD', 'Figma', 'Scrum' ])

  // my work content
  const workTitle = ref('')
  const workProjects = ref<WorkProjects[]>([])
  const workBtn = ref<WorkBtn[]>([])

  // contact content
  const contactTitle = ref('')
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
        name: 'Behance',
        link: 'https://www.behance.net/isaaclouzeiro',
        editLink: 'www.behance.net/isaaclouzeiro',
        icon: 'fa-brands fa-behance'
    }
  ])
  const contactForm = ref<ContactForm>()
  const contactAlert = ref<ContactAlert>()
  const contactBtn = ref('')

  const portuguese = () => {
    // language content
    language.value = [
      { 
        showName: 'Inglês', 
        name: 'English', 
        isCheck: false 
      },
      { 
        showName: 'Português', 
        name: 'Portuguese', 
        isCheck: true 
      }
    ]

    // navbar content
    navItems.value = [
      {
        name: "Início",
        icon: "fa-house-chimney",
        link: "home"
      },
      {
        name: "Sobre",
        icon: "fa-book-open-reader",
        link: "about"
      },
      {
        name: "Trabalhos",
        icon: "fa-code",
        link: "work",
      },
      {
        name: "Contato",
        icon: "fa-envelope",
        link: "contact"
      }
    ]

    // home content
    homeText.value = [
      "Bem vindo ao meu site.",
      "Atualmente minha paixão é criar sites. Eu sou bastante curioso e estou constantemente procurando coisas novas para aprender."
    ]
    homeButtons.value.map(txt => {
      if(txt.name == 'Web Resume') txt.name = 'Currículo Web'
    })
    homeIsaac.value = ['Isaac Louzeiro', 'Desenvolvedor Web']

    // about content
    aboutTitle.value = 'Sobre'
    aboutText.value = [
        "Olá! Me chamo Isaac, sou apaixonado pela área de Desenvolvimento Web.",
        "Gosto de aprender sobre o assunto, e mostrar na prática tudo o que sei nesta área, postando no meu Github, Codepen e Portfolio Web.",
        "Sou uma pessoa bastante curiosa, que gosta de aprender e expandir meus conhecimentos. A cada dia tento melhorar minhas habilidades para que eu possa crescer profissionalmente."
    ]
    aboutEducationTitle.value = 'Educação'
    aboutEducation.value = [ 
        { 
            name: 'Curso Superior de Tecnologia, Gestão da Tecnologia da Informação', 
            institute: 'Faculdade de Tecnologia de São Paulo', 
            in: '02/2023', 
            out: '12/2025' 
        },
        { 
            name: 'Curso Profissionalizante, Desenvolvimento Web FullStack', 
            institute: 'Instituto Proa / Senac', 
            in: '03/2021', 
            out: '07/2021' 
        },
        { 
            name: 'Curso Técnico, Desenvolvimento de Sistemas', 
            institute: 'Escola Técnica Estadual Professor Basilídes de Godoy', 
            in: '07/2019', 
            out: '12/2020' 
        }
    ]
    aboutEducationBtn.value = ['fa-linkedin', 'https://linkedin.com/in/isaac-louzeiro', 'Veja mais']

    // my work content
    workTitle.value = 'Meus Trabalhos'
    workProjects.value = [
      {
          title: 'FaverTI',
          github: 'https://github.com/IsaacLouzeiro/faverti',
          link: 'https://faverti.vercel.app/',
          img: "faverti",
          about: 'Site que fala sobre TI Verde.'
      },
      {
          title: 'CriptoMoeda',
          github: 'https://github.com/IsaacLouzeiro/preco-criptomoedas',
          link: 'https://criptomoeda.netlify.app/',
          img: "criptomoeda",
          about: 'Mostrando valores das criptomoedas a partir de uma API com Vue 3 e Axios.'
      },
      {
          title: 'Spotify Clone',
          github: 'https://github.com/IsaacLouzeiro/spotify-vue-clone',
          link: 'https://spotify-copia.netlify.app/',
          img: "spotify",
          about: 'Clone do Reprodutor Web do Spotify em Vue Js, criado para treinar minhas habilidades.'
      },
      {
          title: 'Untitled Blog',
          github: 'https://github.com/IsaacLouzeiro/blog-angular',
          link: 'https://blog-angular-tau.vercel.app/',
          img: "blog",
          about: 'Projeto de um Blog criado com Angular baseado em um design do Dribbble.'
      },
      {
          title: 'Finans',
          github: 'https://github.com/IsaacLouzeiro/finans',
          link: 'https://isaaclouzeiro.github.io/finans/',
          img: "finans",
          about: 'Website fictício de finança.'
      },
      {
          title: 'Resume',
          github: 'https://github.com/IsaacLouzeiro/resume',
          link: 'https://resume-curriculo.netlify.app',
          img: "resume",
          about: 'Currículo Web, uma forma descontraída de mostrar meu lado profissional.'
      }
    ]
    workBtn.value = [
        {
            icon: 'fa-brands fa-codepen',
            text: 'Projetos Codepen',
            minText: 'Proj. Codepen',
            link: 'https://codepen.io/isaaclouzeiro'
        },
        {
            icon: 'fa-brands fa-github',
            text: 'Projetos Github',
            minText: 'Proj. Github',
            link: 'https://github.com/IsaacLouzeiro'
        }
    ]

    // contact content
    contactTitle.value = 'Contato'
    contactForm.value = {
      name: 'Nome',
      email: 'E-mail',
      message: 'Mensagem'
    }
    contactAlert.value = {
      errorAlert: 'Ocorreu um erro ao concluir o formulário',
      errorAlertIcon: 'fa-triangle-exclamation',
      successAlert: 'Mensagem enviada com sucesso',
      successAlertIcon: 'fa-circle-check'
    }
    contactBtn.value = 'Enviar Mensagem'

  }

  const english = () => {
    // language content
    language.value = [
      { 
        showName: 'English', 
        name: 'English', 
        isCheck: true 
      },
      { 
        showName: 'Portuguese', 
        name: 'Portuguese', 
        isCheck: false 
      }
    ]

    // navbar content
    navItems.value = [
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
    ]

    // home content
    homeText.value = [
      "Welcome to my website.",
      "Recently my passion is creating websites. I'm very curious and constantly searching for new things to learn."
    ]
    homeButtons.value = [
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
    ]
    homeIsaac.value = ['Isaac Louzeiro', 'Web Developer']

    // about content
    aboutTitle.value = 'About'
    aboutText.value = [
      "Hi! My name is Isaac, I'm passionate about Web Development.",
      "I like to learn about this subject, and show my skills in this area, by posting them on my Github, Codepen, and Web Portfolio.",
      "I am a very curious person, who likes to learn and expand my knowledge. Every day I try to improve my skills so that I can grow professionally."
    ]
    aboutEducationTitle.value = 'Education'
    aboutEducation.value = [ 
      { 
          name: 'Technology Degree, Information Technology Management', 
          institute: 'College of Technology of São Paulo', 
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
    ]
    aboutEducationBtn.value = ['fa-linkedin', 'https://linkedin.com/in/isaac-louzeiro', 'See more']

    // my work content
    workTitle.value = 'My Work'
    workProjects.value = [
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
    ]
    workBtn.value = [
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
    ]

    // contact content
    contactTitle.value = 'Contact'
    contactForm.value = {
      name: 'Name',
      email: 'E-mail',
      message: 'Message'
    }
    contactAlert.value = {
      errorAlert: 'There was an error completing the form',
      errorAlertIcon: 'fa-triangle-exclamation',
      successAlert: 'Message was sent successfully',
      successAlertIcon: 'fa-circle-check'
    }
    contactBtn.value = 'Send Message'

  }

  // change language
  let changedLang:any = reactive({
    lang: 'English'
  })

  const changeLang = (lang:any) => {
    changedLang.lang = lang ?? 'English'

    if(changedLang.lang == 'Portuguese') portuguese()
    else english()
  }

  onMounted(() => {
    english()
  })
</script>

<template>
  <NavbarComponent :nav-items="navItems" />

  <ChangeLangComponent 
    :language="language"

    @change-to="changeLang"
  />
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
