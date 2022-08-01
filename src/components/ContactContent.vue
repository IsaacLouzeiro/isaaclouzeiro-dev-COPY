<template>
    <div id="contact" class="py-4">
        <h2 class="mb-4 mt-3 text-md-center">{{ contactTitle }}</h2>

        <form>
            <label for="nameCont">
                <span>{{ contactForm.name }}</span><br>
                <input type="text" v-model="formCont.name" id="nameCont">
            </label>

            <label for="emailCont">
                <span>{{ contactForm.email }}</span><br>
                <input type="mail" v-model="formCont.mail" id="emailCont">
            </label>

            <label for="messageCont">
                <span>{{ contactForm.message }}</span><br>
                <textarea v-model="formCont.message" id="messageCont" rows="5"></textarea>
            </label>

            <button type="button" class="btn">{{ contactBtn }}</button>
        </form>

        <div class="socialCont row g-0">
            <a :href="social.link" target="_blank" class="d-flex align-items-center col-md-6" v-for="(social, index) in contactSocial" :key="index">
                <font-awesome-icon :icon="social.icon" />

                <div class="d-flex flex-column ps-2">
                    <span>{{ social.name }}</span>
                    <p>{{ social.editLink }}</p>
                </div>
            </a>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ContactContent',
    props: {
        // contact content
        contactTitle: String,
        contactForm: Object,
        contactBtn: String,
        contactSocial: Array
    },
    data() {
        return {
            formCont: {
                name: '',
                email: '',
                message: ''
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    @import '@/assets/colors/colors.scss';

    * { color: $color-l-1; }

    h2 {
        color: $color-l-3;
        font-size: 1.9em;
    }

    form {
        max-width: 800px;
        margin: auto;
        padding-bottom: 2em;

        label {
            display: block;
            padding: .5em 0;

            input, textarea {
                background: rgba(0,0,0,0);
                border: 0;
                border-bottom: 2px solid;
                width: 100%;
                max-height: 150px;
                outline: none;
            }
        }

        button {
            background-color: $color-d-2;
            margin-top: 1em;
            &:hover { background-color: $color-d-2; opacity: .7; }
        }
    }

    .socialCont {
        max-width: 800px;
        margin: auto;

        a {
            text-decoration: none;
            margin: 1em 0;

            svg {
                font-size: 2.5em;
            }

            div {
                span {
                    font-size: 1.3em;
                    margin-bottom: -.3em;
                }

                p {
                    font-weight: 300;
                    text-decoration: none;
                    padding: 0;
                    margin: 0;
                }
            }
        }
    }
</style>