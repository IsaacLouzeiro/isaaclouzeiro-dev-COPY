<template>
    <div class="row h-100 g-0">
        <div  class="col-1">
            <NavbarContent :language="language" :navBar="navBar" @change-to="changeLang = $event" />
        </div>
        
        <router-view 
            class="col-sm-11 gx-sm-5"

            :homeText="homeText"    
            :homeButtons="homeButtons"    
            :homeIsaac="homeIsaac"

            :aboutTitle="aboutTitle"
            :aboutText="aboutText"
            :aboutEducationTitle="aboutEducationTitle"
            :aboutEducation="aboutEducation"
            :aboutEducationBtn="aboutEducationBtn"
            :aboutSkills="aboutSkills"

            :workTitle="workTitle"
            :workProjects="workProjects"
            :workBtn="workBtn"

            :contactTitle="contactTitle"
            :contactForm="contactForm"
            :contactBtn="contactBtn"
            :contactSocial="contactSocial"
        />
    </div>
</template>

<script>
import NavbarContent from '@/components/NavbarContent.vue'

export default {
    name: 'App',
    data() {
        return {
            // navbar content
            language: [],
            changeLang: '',
            navBar: [],

            // home content
            homeText: [],
            homeButtons: [],
            homeIsaac: [],

            // about content
            aboutTitle: '',
            aboutText: [],
            aboutEducationTitle: '',
            aboutEducation: [ { name: '', institute: '', in: '', out: '' } ],
            aboutEducationBtn: [],
            aboutSkills: [],

            // my work content
            workTitle: '',
            workProjects: [],
            workBtn: [],

            // contact content
            contactTitle: '',
            contactForm: {},
            contactBtn: '',
            contactSocial: []
        }
    },

    // translation config
    methods: {
        english() {
            // navbar content
            this.language = [
                { showName: 'English', name: 'English', isCheck: true },
                { showName: 'Portuguese', name: 'Portuguese', isCheck: false }
            ]

            this.navBar = [
                'Home',
                'About',
                'My Work',
                'Contact'
            ]

            // home content
            this.homeText = [ 
                "Welcome to my website.",
                "Recently my passion is creating websites. I'm very curious and constantly searching for new things to learn."
            ]

            this.homeButtons = [
                {
                    name: 'Web Resume',
                    icon: 'fa-solid fa-window-maximize',
                    link: 'https://isaac-resume.web.app/'
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

            this.homeIsaac = ['Isaac Louzeiro', 'Front-End Web Developer']

            // about content
            this.aboutTitle = 'About'

            this.aboutText = [
                "Hi! My name is Isaac, I'm passionate about Web Development, especially the Front-End area.",
                "I like to learn about this subject, and show my skills in this area, putting it on my Github, Codepen, and Web Portfolio.",
                "I am a very curious person, who likes to learn and expand my knowledge. Every day I try to improve my skills so that I can grow professionally."
            ]

            this.aboutEducationTitle = 'Education'
            this.aboutEducation = [ 
                { 
                    name: 'Vocational Course, Java Web Programing', 
                    institute: 'Instituto Proa / Senac', 
                    in: '07/2021', 
                    out: '12/2021' 
                },
                { 
                    name: 'Technical Course, Systems Development', 
                    institute: 'Public Technical School Professor Basilídes de Godoy', 
                    in: '07/2019', 
                    out: '12/2020' 
                }
            ]
            this.aboutEducationBtn = ['https://linkedin.com/in/isaac-louzeiro', 'See more']
            this.aboutSkills = [ 'HTML5', 'CSS3', 'JavaScript', 'Bootstrap', 'Sass', 'Vue', 'SPA', 'Wordpress', 'SEO', 'NPM', 'Git', 'Github', 'Adobe XD', 'Figma', 'Scrum', 'Trello' ]
        
        
            // my work content
            this.workTitle = 'My Work'
            this.workProjects = [
                {
                    title: 'CriptoMoeda',
                    github: 'https://github.com/IsaacLouzeiro/preco-criptomoedas',
                    link: 'https://criptomoeda.netlify.app/',
                    img: require("@/assets/img/projects/criptoMoeda.png"),
                    about: 'Showing cryptocurrencies values from an API with Vue 3 and Axios.'
                },
                {
                    title: 'Spotify Clone',
                    github: 'https://github.com/IsaacLouzeiro/spotify-vue-clone',
                    link: 'https://spotify-copia.netlify.app/',
                    img: require("@/assets/img/projects/spotifyClone.png"),
                    about: 'Spotify Web Audio Player clone in Vue Js, created to practice my abilities.'
                },
                {
                    title: 'Economie',
                    github: 'https://github.com/IsaacLouzeiro/economie',
                    link: 'https://economie-dinie.github.io/economie/resumo.html',
                    img: require("@/assets/img/projects/economie.png"),
                    about: 'Website focused on helping young and adult people to organize financially, in a friendly way. Demoday work project of the Proa Institute 4.0 in Web Java Programming in 2021.'
                },
                {
                    title: 'Leandro Louzeiro',
                    github: 'https://github.com/IsaacLouzeiro/website-portfolio-fotografia2',
                    link: 'https://leandrolouzeiro.com.br/',
                    img: require("@/assets/img/projects/leandroLouzeiro.png"),
                    about: 'Photograpy portfolio developed for the photographer Leandro Louzeiro. version 2.0'
                },
                {
                    title: 'Finans',
                    github: 'https://github.com/IsaacLouzeiro/finans',
                    link: 'https://isaaclouzeiro.github.io/finans/',
                    img: require("@/assets/img/projects/finans.png"),
                    about: 'Fictitious website of finance.'
                },
                {
                    title: 'Resume',
                    github: 'https://github.com/IsaacLouzeiro/resume',
                    link: 'https://isaac-resume.web.app/',
                    img: require("@/assets/img/projects/resume.png"),
                    about: 'Web resume, a relaxed way of show my professional side.'
                }
            ]
            this.workBtn = [
                {
                    icon: 'fa-brands fa-codepen',
                    text: 'Codepen Projects',
                    minText: 'Codepen',
                    link: 'https://codepen.io/isaaclouzeiro'
                },
                {
                    icon: 'fa-brands fa-github',
                    text: 'Github Projects',
                    minText: 'Github',
                    link: 'https://github.com/IsaacLouzeiro'
                }
            ]

            // contact content
            this.contactTitle = 'Contact'
            this.contactForm = {
                name: 'Name',
                email: 'E-mail',
                message: 'Message'
            }
            this.contactBtn = 'Send Message',
            this.contactSocial = [
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
            ]
        },

        portuguese() {
            // navbar content
            this.language = [
                { showName: 'Inglês', name: 'English', isCheck: false },
                { showName: 'Português', name: 'Portuguese', isCheck: true }
            ]
            
            this.navBar = [
                'Início',
                'Sobre',
                'Meus Trabalhos',
                'Contato'
            ]

            // home content
            this.homeText = [ 
                "Bem vindo ao meu site.",
                "Recentemente minha paixão é criar sites. Eu sou bastante curioso e estou constantemente procurando coisas novas para aprender."
            ]

            this.homeButtons = [
                {
                    name: 'Currículo Web',
                    icon: 'fa-solid fa-window-maximize',
                    link: 'https://isaac-resume.web.app/'
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

            this.homeIsaac = ['Isaac Louzeiro', 'Desenvolvedor Web Front-End']

            // about content
            this.aboutTitle = 'Sobre'

            this.aboutText = [
                "Olá! Me chamo Isaac, sou apaixonado pela área de Desenvolbimento Web, principalmente na parte de Front-end.",
                "Gosto de aprender sobre o assunto, e principalmente mostrar na prática tudo o que sei nesta área, adicionando no meu Github, Codepen e Portfolio Web.",
                "Sou uma pessoa bastante curiosa, que gosta de aprender e expandir meus conhecimentos. A cada dia tento melhorar minhas habilidades para que eu possa crescer profissionalmente."
            ]

            this.aboutEducationTitle = 'Educação'
            this.aboutEducation = [ 
                { 
                    name: 'Curso Profissionalizante, Programação Web Java', 
                    institute: 'Instituto Proa / Senac', 
                    in: '07/2021', 
                    out: '12/2021' 
                },
                { 
                    name: 'Curso Técnico, Desenvolvimento de Sistemas', 
                    institute: 'Escola Técnica Estadual Professor Basilídes de Godoy', 
                    in: '07/2019', 
                    out: '12/2020' 
                }
            ]
            this.aboutEducationBtn = ['https://linkedin.com/in/isaac-louzeiro' ,'Veja mais']
            this.aboutSkills = [ 'HTML5', 'CSS3', 'JavaScript', 'Bootstrap', 'Sass', 'Vue', 'SPA', 'Wordpress', 'SEO', 'NPM', 'Git', 'Github', 'Adobe XD', 'Figma', 'Scrum', 'Trello' ]
        
            // my work content
            this.workTitle = 'Meus Projetos'
            this.workProjects = [
                {
                    title: 'CriptoMoeda',
                    github: 'https://github.com/IsaacLouzeiro/preco-criptomoedas',
                    link: 'https://criptomoeda.netlify.app/',
                    img: require("@/assets/img/projects/criptoMoeda.png"),
                    about: 'Mostrando valores das criptomoedas a partir de uma API com Vue 3 e Axios.'
                },
                {
                    title: 'Clone Spotify',
                    github: 'https://github.com/IsaacLouzeiro/spotify-vue-clone',
                    link: 'https://spotify-copia.netlify.app/',
                    img: require("@/assets/img/projects/spotifyClone.png"),
                    about: 'Clone do Reprodutor Web do Spotify em Vue Js, criado para treinar minhas habilidades.'
                },
                {
                    title: 'Economie',
                    github: 'https://github.com/IsaacLouzeiro/economie',
                    link: 'https://economie-dinie.github.io/economie/resumo.html',
                    img: require("@/assets/img/projects/economie.png"),
                    about: 'Site voltado a ajudar jovens e adultos a se organizar financeiramente, de uma maneira amigável. Projeto final Demoday do curso de Programação Java Web do Instituto Proa em 2021.'
                },
                {
                    title: 'Leandro Louzeiro',
                    github: 'https://github.com/IsaacLouzeiro/website-portfolio-fotografia2',
                    link: 'https://leandrolouzeiro.com.br/',
                    img: require("@/assets/img/projects/leandroLouzeiro.png"),
                    about: 'Portfolio de fotografia desenvolvido para o fotógrafo Leandro Louzeiro. Versão 2.0'
                },
                {
                    title: 'Finans',
                    github: 'https://github.com/IsaacLouzeiro/finans',
                    link: 'https://isaaclouzeiro.github.io/finans/',
                    img: require("@/assets/img/projects/finans.png"),
                    about: 'Website fictício de finança.'
                },
                {
                    title: 'Resume',
                    github: 'https://github.com/IsaacLouzeiro/resume',
                    link: 'https://isaac-resume.web.app/',
                    img: require("@/assets/img/projects/resume.png"),
                    about: 'Currículo Web, uma forma descontraída de mostrar meu lado profissional.'
                }
            ]
            this.workBtn = [
                {
                    icon: 'fa-brands fa-codepen',
                    text: 'Projetos no Codepen',
                    minText: 'Codepen',
                    link: 'https://codepen.io/isaaclouzeiro'
                },
                {
                    icon: 'fa-brands fa-github',
                    text: 'Projetos no Github',
                    minText: 'Github',
                    link: 'https://github.com/IsaacLouzeiro'
                }
            ]

            // contact content
            this.contactTitle = 'Contato'
            this.contactForm = {
                name: 'Nome',
                email: 'E-mail',
                message: 'Mensagem'
            }
            this.contactBtn = 'Enviar Mensagem',
            this.contactSocial = [
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
            ]
        }
    },
    created() {
        this.english()
    },
    components: {
        NavbarContent
    },
    watch: {
        changeLang(toLang) {
            // console.log(toLang)
            if(toLang == 'Portuguese') {
                this.portuguese()
            }else {
                this.english()
            }
        }
    }
}
</script>


<style lang="scss">
    // standard
    
    @import url('https://fonts.googleapis.com/css2?family=Ubuntu:ital,wght@0,300;0,500;0,700;1,300;1,400;1,500;1,700&display=swap'); // ubuntu font
    @import '@/assets/colors/colors.scss'; // colors

    .gradient { background-image: linear-gradient(to bottom right, $color-d-2, $color-l-2); background-attachment: fixed; } // main gradient

    a { &:hover { text-decoration: none; opacity: .7 } }; // link hover
    ul { list-style-type: none; } // list without style type
    .btn, button, input { &:focus, &:hover { border-color: rgba(0,0,0,0); outline: none; } } // removing outline

    * { // space and font
        margin: 0;
        padding: 0;
        font-family: 'Ubuntu', 'Trebuchet MS', sans-serif;
        box-sizing: border-box;
    }

    html, body, #app { width: 100%; height: 100%;  }

    html, body {
        box-sizing: content-box;
        overflow-y: auto;
    }

    #app {
        padding-left: 1rem;
        padding-right: 1rem;
        position: relative;
        max-width: 1440px;
        margin: auto;
        scroll-behavior: smooth;
        overflow-y: scroll;
        scrollbar-color: $color-d-2 rgba($color-l-1, .4);
        scrollbar-width: thin;
    }

</style>
