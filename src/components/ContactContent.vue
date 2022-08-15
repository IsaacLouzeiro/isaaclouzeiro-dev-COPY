<template>
    <div id="contact" class="py-4">
        <h2 class="mb-4 mt-3 text-md-center">{{ contactTitle }}</h2>

        <form @submit.prevent="sendMail($event)">
            <label for="nameCont">
                <small class="text-danger" v-if="formBoolean.name == false">{{ contactAlert[0].nameAlert }}</small><br>
                <span>{{ contactForm.name }}</span><br>
                <input type="text" name="from_name" v-model="formCont.name" id="nameCont">
            </label>

            <label for="emailCont">
                <small class="text-danger" v-if="formBoolean.email == false">{{ contactAlert[0].emailAlert }}</small><br>
                <span>{{ contactForm.email }}</span><br>
                <input type="mail" name="reply_to" v-model="formCont.email" id="emailCont">
            </label>

            <label for="messageCont">
                <small class="text-danger" v-if="formBoolean.message == false">{{ contactAlert[0].messageAlert }}</small><br>
                <span>{{ contactForm.message }}</span><br>
                <textarea v-model="formCont.message" id="messageCont" rows="5" name="message"></textarea>
            </label>

            <button type="submit" class="btn">{{ contactBtn }}</button>

            <div class="alert bg-danger mt-3" id="errorAlert" style="display: none;">
                <font-awesome-icon :icon="contactAlert[0].contAlert.errorAlertIcon" class="me-2" /> {{ contactAlert[0].contAlert.errorAlert }}
            </div>
            <div class="alert bg-success mt-3" id="successAlert" style="display: none;">
                <font-awesome-icon :icon="contactAlert[0].contAlert.successAlertIcon" class="me-2" /> {{ contactAlert[0].contAlert.successAlert }}
            </div>
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
import emailjs from 'emailjs-com';

export default {
    name: 'ContactContent',
    props: {
        // contact content
        contactTitle: String,
        contactForm: Object,
        contactBtn: String,
        contactSocial: Array,
        contactAlert: Array
    },
    data() {
        return {
            formCont: {
                name: '',
                email: '',
                message: ''
            },
            formBoolean: {
                name: true,
                email: true,
                message: true
            }
        }
    },

    methods: {
        sendMail(e) {
            if (this.formCont.name == '' || this.formCont.name == ' ') this.formBoolean.name = false
            else if(this.formCont.email == '' || this.formCont.email == ' ') this.formBoolean.email = false
            else if(this.formCont.message == '' || this.formCont.message == ' ') this.formBoolean.message = false
            else {
                try {
                    emailjs.sendForm('SERVICE_ID', 'TEMPLATE_ID', e.target, 'USER_ID', {
                        name: this.formCont.name,
                        email: this.formCont.email,
                        message: this.formCont.message
                    })

                    this.$el.querySelector("#successAlert").style.display = "block";
                    setInterval(() => {
                        this.$el.querySelector("#successAlert").style.display = "none";
                    }, 4000);

                } catch(error) {
                    console.log({error})

                    this.$el.querySelector("#errorAlert").style.display = "block";
                    setInterval(() => {
                        this.$el.querySelector("#errorAlert").style.display = "none";
                    }, 4000);
                }
    
                // reset
                this.formCont.name = ''
                this.formCont.email = ''
                this.formCont.message = ''
                this.formBoolean.name = true
                this.formBoolean.email = true
                this.formBoolean.message = true
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