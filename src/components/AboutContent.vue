<template>
    <div id="about" class="d-flex align-items-center py-5">
        <div class="row py-1">
            <div class="col-md-7">
                <div class="aboutText">
                    <h2 class="pt-3"> {{ aboutTitle }} </h2>
                    <p v-for="(text, index) in aboutText" :key="index"> {{ text }} </p>
                </div>
    
                <div class="aboutEducation">
                    <h2> {{ aboutEducationTitle }} </h2>
    
                    <ul class="nav flex-column">
                        <li v-for="(ed, index) in aboutEducation" :key="index">
                            <p>{{ ed.name }} | {{ ed.in }} - {{ ed.out }}</p>
                            <p class="fw-light">{{ ed.institute }}</p>
                        </li>
                    </ul>
    
                    <a class="btn" :href="aboutEducationBtn[0]" target="_blank"><font-awesome-icon icon="fa-brands fa-linkedin" />&nbsp; {{ aboutEducationBtn[1] }}</a>
                </div>
            </div>

            <div class="aboutSkills col-md-5 d-flex justify-content-center align-items-center py-5">
                <!-- skills tag cloud interactive -->
                <div class="tagcloud"></div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'AboutContent',
    props: {
        aboutTitle: String,
        aboutText: Array,
        aboutEducationTitle: String,
        aboutEducation: Array,
        aboutEducationBtn: Array,
        aboutSkills: Array
    },
    // Skills Tag Cloud
    mounted() {
        const TagCloud = require('TagCloud');

        const container = '.tagcloud';
        const texts = this.aboutSkills;
        const options = {
            maxSpeed: 'fast'
        };

        TagCloud(container, texts, options);

    }
}
</script>

<style lang="scss" scoped>
    @import '@/assets/colors/colors.scss';

    #about {
        width: 100%;
        min-height: 650px;
        color: $color-l-1;

        h2 {
            color: $color-l-3;
        }

        p {
            font-size: 1.15em;
        }

        .aboutText {
            h2 {
                font-size: 1.9em;
            }
            
            p {
                margin: .4em 0;
            }
        }
        
        .aboutEducation {
            h2 {
                font-size: 1.4em;
                margin-top: .7em;
                margin-bottom: 0;
            }

            li {
                margin: .4em 0;
                p {
                    margin: 0;
                }
            }

            .btn {
                background-color: $color-d-2;
                color: $color-l-1;
                margin: .8em 0;
            }

        }

        .aboutSkills {
            font-size: 1.2em;
        }

        @media only screen and (min-width: 768px) {
            height: 100%;

            .aboutText {
                h2 {
                    margin-top: 1em;
                }
            }
        }
        @media only screen and (min-width: 868px) {
            .aboutText {
                h2 {
                    margin-top: 0;
                }
            }
        }
    }
</style>