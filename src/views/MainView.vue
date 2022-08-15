<template>
    <div id="main" class="h-100">
        <HomeContent 
            :homeText="homeText" 
            :homeButtons="homeButtons" 
            :homeIsaac="homeIsaac" 
        />
        <AboutContent 
            :aboutTitle="aboutTitle"
            :aboutText="aboutText"
            :aboutEducationTitle="aboutEducationTitle"
            :aboutEducation="aboutEducation"
            :aboutEducationBtn="aboutEducationBtn"
            :aboutSkills="aboutSkills"
        />
        <WorkContent 
            :workTitle="workTitle"
            :workProjects="workProjects"
            :workBtn="workBtn"
        />

        <ContactContent 
            :contactTitle="contactTitle"
            :contactForm="contactForm"
            :contactBtn="contactBtn"
            :contactSocial="contactSocial"
            :contactAlert="contactAlert"
        />
    </div>
</template>

<script>
import HomeContent from '@/components/HomeContent.vue';
import AboutContent from '@/components/AboutContent.vue';
import WorkContent from '@/components/WorkContent.vue';
import ContactContent from '@/components/ContactContent.vue';

export default {
    name: 'MainView',
    props: {
        // home content
        homeText: Array,
        homeButtons: Array,
        homeIsaac: Array,
        // about content
        aboutTitle: String,
        aboutText: Array,
        aboutEducationTitle: String,
        aboutEducation: Array,
        aboutEducationBtn: Array,
        aboutSkills: Array,
        // work content
        workTitle: String,
        workProjects: Array,
        workBtn: Array,
        // contact content
        contactTitle: String,
        contactForm: Object,
        contactBtn: String,
        contactSocial: Array,
        contactAlert: Array
    },
    components: {
    HomeContent,
    AboutContent,
    WorkContent,
    ContactContent
}
}
</script>
