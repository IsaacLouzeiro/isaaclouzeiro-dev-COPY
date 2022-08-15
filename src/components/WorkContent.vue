<template>
    <div id="work" class="py-5">
        <h2 class="pb-3"> {{workTitle }} </h2>
        <div>
            <ul class="myProjects nav justify-content-between">
                <li v-for="(proj, index) in workProjects" :key="index" class="px-2 pt-2 me-1">
                    <div class="headerProjects d-flex justify-content-between">
                        <a :href="proj.link" target="_blank" class="projectName">
                            {{ proj.title }}
                        </a>

                        <a :href="proj.github" target="_blank" class="projectGit">
                            <font-awesome-icon icon="fa-brands fa-github" />
                        </a>
                    </div>
                    
                    <div class="centerSpace">
                    </div>

                    <a :href="proj.link" target="_blank" class="mainProjects d-flex align-self-center w-100">
                        <img :src="proj.img" :alt="proj.title">
                        <font-awesome-icon icon="fa-solid fa-link" />
                    </a>
                </li>
            </ul>

            <div class="d-flex align-items-center justify-content-between boxBtnProjects">
                <a :href="btn.link" v-for="(btn, index) in workBtn" :key="index" class="btn mt-3" target="_blank">
                    <font-awesome-icon :icon="btn.icon" />
                     <span class="d-none d-sm-inline ps-2">{{ btn.text }}</span><span class="d-inline d-sm-none ps-2">{{ btn.minText }}</span>
                </a>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'WorkContent',
    props: {
        // work content
        workTitle: String,
        workProjects: Array,
        workBtn: Array
    }
}
</script>

<style lang="scss" scoped>
    @import '@/assets/colors/colors.scss';
    
    #work {
        width: 100%;
    }

    h2 {
        color: $color-l-3;
        font-size: 1.9em;
    }

    .myProjects {
        li {
            background-color: rgba($color-l-1, .5);
            margin-bottom: 3vw;
            border-radius: 5px;
            position: relative;
            width: 32%;
            max-height: 15.5em;

            .headerProjects {
                .projectName {
                    color: $color-d-2;
                    font-size: 1.2em;
                    text-decoration: none;
                    margin-left: .3em;
                }
                .projectGit {
                    color: $color-d-1;
                    font-size: 2em;
                    position: relative;
                    bottom: .3em;
                }
            }

            .centerSpace {
                height: 14vw;
            }
            
            .mainProjects {
                position: absolute;
                top: 2.4em;
                left: 0;
                right: 0;
                
                * {
                    transition: all .2s ease-in;
                }

                img {
                    width: 100%;
                }

                svg {
                    position: absolute;
                    left: 0; 
                    right: 0; 
                    bottom: 0; 
                    top: 0; 
                    margin: auto; 
                    font-size: 3em;
                    color: $color-l-1;
                    opacity: 0;
                }

                &:hover {
                    svg {
                        opacity: 1;
                    }
                }
            }

            @media only screen and (max-width: 992px) {
                width: 48%;
                
                .centerSpace {
                    height: 20.5vw;
                }
            }

            @media only screen and (max-width: 576px) {
                width: 100%;
                max-height: 20em;
                margin-bottom: 10vw;

                .centerSpace {
                    height: 45vw;
                }
            }
        }
    }

    .boxBtnProjects {
        .btn {
            background-color: $color-d-2;
            color: $color-l-1;

            svg {
                @media only screen and (max-width: 350px) {
                    display: none ;
                }
            }
        }
    }
</style>