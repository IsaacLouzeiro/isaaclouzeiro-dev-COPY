<template>
    <div id="navbarContent">
        <!-- navbar laptop/pc content -->
        <div id="largeContainer" class="d-sm-block d-none">
            <nav class="d-flex flex-column align-items-center justify-content-center ps-1 ps-md-3">
                <a class="navbar-brand" href="#"><img src="@/assets/img/logo.png" alt="Logo Isaac Louzeiro"></a>

                <ul class="nav flex-column">
                    <li class="list-item">
                        <a href="#home" class="button">
                            <font-awesome-icon icon="fa-solid fa-house-chimney" /><span> {{ navBar[0] }} </span>
                        </a>
                    </li>
                    <li class="list-item">
                        <a href="#about" class="button">
                            <font-awesome-icon icon="fa-solid fa-book-open-reader" /><span> {{ navBar[1] }} </span>
                        </a>
                    </li>
                    <li class="list-item">
                        <a href="#work" class="button">
                            <font-awesome-icon icon="fa-solid fa-code" /><span> {{ navBar[2] }} </span>
                        </a>
                    </li>
                    <li class="list-item">
                        <a href="#contact" class="button">
                            <font-awesome-icon icon="fa-solid fa-envelope" /><span> {{ navBar[3] }} </span>
                        </a>
                    </li>
                </ul>
            </nav>

            <!-- language -->
            <div class="btn-group dropend language-dropdown">
                <button type="button" class="btn lang" data-bs-toggle="dropdown" aria-expanded="false">
                    <font-awesome-icon icon="fa-solid fa-language" />
                </button>
                <ul class="dropdown-menu">
                    <!-- Dropdown menu links -->
                    <li 
                        class="dropdown-item" 
                        v-for="(lang, index) in language" 
                        :key="index" 
                        :class="{ disabled: lang.isCheck }"

                        @click="changeTo(index)"
                    >
                        <button type="button">{{ lang.showName }}</button>
                    </li>
                </ul>
            </div>
        </div>

        <!-- navbar mobile content -->
        <div id="mobileContainer" class="d-block d-sm-none">
            <!-- open navbar button -->
            <button class="btn bar" type="button" data-bs-toggle="offcanvas" data-bs-target="#menuMobile" aria-controls="menuMobile" ><font-awesome-icon icon="fa-solid fa-bars" /></button>

            <div class="offcanvas offcanvas-start text-bg-dark" data-bs-scroll="true" tabindex="-1" id="menuMobile" aria-labelledby="menuMobileLabel">
                <div class="offcanvas-header">
                    <!-- language -->
                    <div class="btn-group dropend">
                        <button type="button" class="btn lang" data-bs-toggle="dropdown" aria-expanded="false">
                            <font-awesome-icon icon="fa-solid fa-language" />
                        </button>
                        <ul class="dropdown-menu">
                            <!-- Dropdown menu links -->
                            <li 
                                class="dropdown-item" 
                                v-for="(lang, index) in language" 
                                :key="index" 
                                :class="{ disabled: lang.isCheck }"

                                @click="changeTo(index)"
                            >
                                <button type="button">{{ lang.showName }}</button>
                            </li>
                        </ul>
                    </div>

                    <!-- close navbar button -->
                    <button type="button" class="bar-close" data-bs-dismiss="offcanvas" aria-label="Close"><font-awesome-icon icon="fa-solid fa-bars" /></button>
                </div>
                <!-- navbar mobile content -->
                <div class="offcanvas-body">
                    <!-- navbar mobile list -->
                    <ul class="nav flex-column">
                        <li class="nav-item"><a href="#home" class="nav-link"><font-awesome-icon icon="fa-solid fa-house-chimney" /> {{ navBar[0] }}</a></li>
                        <li class="nav-item"><a href="#about" class="nav-link"><font-awesome-icon icon="fa-solid fa-book-open-reader" /> {{ navBar[1] }}</a></li>
                        <li class="nav-item"><a href="#work" class="nav-link"><font-awesome-icon icon="fa-solid fa-code" /> {{ navBar[2] }}</a></li>
                        <li class="nav-item"><a href="#contact" class="nav-link"><font-awesome-icon icon="fa-solid fa-envelope" /> {{ navBar[3] }}</a></li>
                    </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'NavbarContent',
    data() {
        return {

        }
    },
    props: {
        language: Array,
        navBar: Array
    },
    methods: {
        changeTo(i) {
            if(i == 0) this.$emit('changeTo', 'English')
            else if(i == 1) this.$emit('changeTo', 'Portuguese')
        }
    }
}
</script>

<style lang="scss" scoped>
    @import '@/assets/colors/colors.scss'; // colors


    #navbarContent {
        height: 100%;

        #largeContainer {
            height: 100%;
            
            nav {
                position: fixed;
                height: 100%;
                min-height: 500px;
            }
        }

        @media only screen and (max-width: 575px) {
            height: auto;
            position: absolute;
        }

        @media screen and (max-height: 400px) {
            #largeContainer {
                display: none!important;
            }
            #mobileContainer {
                display: block!important;
            }
        }
    }

    // all buttons
    button, .button {
        padding: 0;
        margin: 0;
        background-color: rgba(0,0,0,0);
        border: none;
        font-size: 1.9em;
        color: $color-l-1;

        // bar button
        &.bar {
            color: $color-l-1;
        }
        // lang button
        &.lang {
            color: $color-l-3;
        }
    }
    // change language button
    .dropdown-menu {
        background-color: rgba($color-l-3, 1);
        .dropdown-item {
            padding: 0;
            button {
                font-size: 1em;
                color: $color-l-1;
                width: 100%;
                padding: 3px 0 3px 10px;
                text-align: start;

                &:hover, &:active {
                    background-color: $color-l-1;
                    color: $color-d-1;
                }
            }

            &.disabled {
                background-color: rgba($color-l-1, .3);
            }
        }
    }

    // navbar large content
    #largeContainer {

        // language
        .language-dropdown {
            position: absolute;
            top: 1.5rem;
            right: 2rem;

            button.lang {
                color: $color-l-1;
            }
        }
        
        nav {
            // navbar brand
            .navbar-brand {
                top: 1rem;
                position: absolute;
                
                img {
                    width: 72px;

                    @media only screen and (max-width: 767px) {
                        width: 60px;
                    }
                }

            }
            // navbar list
            ul {
                li {
                    // navbar button
                    .button {
                        padding: 0;
                        margin: 10px 0;
                        background-color: rgba($color-l-1, .5);
                        border: none;
                        font-size: 1.3em;
                        color: $color-d-2;
                        width: 55px;
                        height:50px;
                        border-radius: 5px;
                        display: flex;
                        flex-direction: column;
                        justify-content: center;
                        align-items: center;

                        span {
                            font-size: .75em;
                            margin-top: .3em;
                            margin-left: 3.8em;
                            color: $color-l-1;
                            position: absolute;
                            display: none;
                            opacity: .7;
                            align-self: flex-start;
                        }
                        &:hover span {
                            display: inline-block;
                        }

                        &.active {
                            background-color: rgba($color-d-2, .5);
                            color: $color-l-1;

                            span {
                                display: inline-block;
                                width: 10px;
                                height: 10px;
                                border-radius: 5px;
                                margin-top: .7em;
                                opacity: 1;
                                color: rgba($color-l-1, .5);
                                background-color: rgba($color-l-1, .5);
                                overflow: hidden;
                            }
                        }

                        @media only screen and (max-width: 767px) {
                            font-size: 1.2em;
                            width: 50px;
                            height:45px;
                        }
                    }
                }
            }
        }
    }

    // navbar mobile content
    #mobileContainer {
        // navbar mobile width content
        position: fixed;
        z-index: 9999;
        .offcanvas {
            width: 20rem;
        }
        
        @media only screen and (max-width: 576px) {
            .offcanvas {
                width: 15rem;
            }
        }
        // navbar mobile list content
        .nav {
            .nav-item {
                .nav-link {
                    padding: 5px 0;
                    margin: 5px 0;
                    color: $color-l-1;
                    text-decoration: underline;
                    text-decoration-color: $color-l-2;

                    svg {
                        margin-right: 10px;
                    }
                }
            }
        }
    }
</style>