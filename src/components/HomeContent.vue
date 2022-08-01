<template>
    <div id="home" class="d-flex justify-content-center align-items-center">
        <div class="row align-items-center justify-content-center h-100 g-0">
            <div class="homeTextButtons col-md-7">
                <div class="digitacao">
                    <h2 class="boxText"><span class="text">{{ homeText[0] }}</span></h2><span class="barra">|</span>
                </div>
                <p>{{ homeText[1] }}</p>
        
                <ul class="nav">
                    <li class="nav-item" v-for="(btn, index) in homeButtons" :key="index">
                        <a :href="btn.link" class="nav-link btn" target="_blank">
                            <span class="d-none d-lg-inline">
                                <font-awesome-icon :icon="btn.icon"/>
                            </span>
                            {{ btn.name }}
                        </a>
                    </li>
                </ul>
            </div>
    
            <div class="homeIsaac col-md-4">
                <img src="@/assets/img/me.jpeg" :alt="homeIsaac[0]">
                <h3>{{ homeIsaac[0] }}</h3>
                <p>{{ homeIsaac[1] }}</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HomeContent',
    props: {
        // home content
        homeText: Array,
        homeButtons: Array,
        homeIsaac: Array
    }
}
</script>

<style lang="scss" scoped>
    @import '@/assets/colors/colors.scss';

    @import '@/assets/writingAnimation.scss';

    #home {
        width: 100%;
        height: 100%;

        .homeTextButtons {
            h2 { color: $color-l-1; }
    
            p { color: $color-l-3; }
    
            ul {
                li {
                    a {
                        background-color: $color-d-2;
                        color: $color-l-1;
                        margin-right: .5em;

                        @media only screen and (max-width: 380px) {
                            padding: 5px 8px;
                            font-size: 1em;
                        }

                        @media only screen and (max-width: 354px) {
                            padding: 5px 8px;
                            font-size: .9em;
                        }
                    }
                }
            }
        }

        .homeIsaac {
            display: flex;
            flex-direction: column;
            align-items: center;

            img {
                width: 10em;
                height: 10em;
                border-radius: 5em;
                border: 5px solid $color-l-3;

                @media only screen and (max-width: 380px) {
                    width: 9em;
                    height: 9em;
                }
            }

            h3, p { color: $color-l-1; }

            h3 { margin-top: .5em; }

            p { font-size: 1.1em; font-style: italic; }
        }

        @media only screen and (min-width: 767px) {
            flex-direction: row;
            justify-content: space-evenly;
            align-items: center;
        }

        @media only screen and (max-width: 767px) {
            >div {
                max-height: 600px;
            }
        }
    }
</style>