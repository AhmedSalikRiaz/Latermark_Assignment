<template>
  <div id="app">

        <div class="content">

            <div class="userInfo">

                <img class="pics" :src="VMSIcon" />

                <div class="userInputs">

                    <p id="lefties">{{ user }}</p>

                    <div>
                        <div>
                            <div>
                                <input type="text" v-model="userVal">
                            </div>

                            <div id="lefties" class="errors" v-show="userError">
                                {{ blankError }}
                            </div>
                        </div>
                    </div>



                    <p id="lefties">{{ pass }}</p>

                    <div>
                        <div>


                            <div>
                                <div class="[control, is-expanded]">
                                    <input v-if="showPassword" type="text" class="input" v-model="passVal" />
                                    <input v-else type="password" class="input" v-model="passVal">
                                </div>

                                <div class="control">
                                    <button class="button" @click="toggleShow">
                                      <!-- <span class="[icon, is-small, is-right]">
                                            <i class="fas"
                                                :class="{ 'fa-eye-slash': showPassword, 'fa-eye': !showPassword }"></i>
                                        </span> -->
                                        <font-awesome-icon icon="eye"/>
                                    </button>
                                </div>
                            </div>

                            <div id="lefties" class="errors" v-show="passError">
                                {{ blankError }}
                            </div>

                        </div>

                    </div>

                    <button class="loginBtn" @click="loginClick">LOGIN</button>
                    <p class="errors" v-show="loginError">{{ loginErrorMsg }}</p>

                    <p class="success" v-show="noErrors">{{ successMsg }}</p>

                </div>

                <img class="pics" :src="DCIcon" />

            </div>

            <div>
                <img class="mainPic" :src="mainImg" />
            </div>

        </div>

        <div class="foot">
            <img class="footerPic" :src="footnoteImg" />
        </div>
    </div>
</template>

<script>
import mainImg from "./assets/main_Image.png"
import footnoteImg from "./assets/Footnote.png"
import DCIcon from "./assets/DC_Layernote_Icon.png"
import VMSIcon from "./assets/VMS.png"

export default {
  name: 'App',
  data: function() {
        
        return {user: 'Username',
        pass: 'Password',
        btnText: 'LOGIN',

        loginErrorMsg: 'Invalid Username or Password',
        blankError: 'This field cannot be left blank',
        successMsg: 'You have successfully logged in !',


        mainImg,
        footnoteImg,
        DCIcon,
        VMSIcon,

        userVal: '',
        passVal: '',

        loginError: false,
        userError: false,
        passError: false,

        noErrors: false,

        showPassword: false,

        correctUser: 'egunay',
        correctPass: '12345'
    }},



    methods: {
        loginClick() {
            //check the username and password for errors

            if (this.userVal.trim() === "") { //no username entered
                this.userError = true;
            } else {
                this.userError = false;
            }

            if (this.passVal.trim() === "") { //no password entered
                this.passError = true;
            } else {
                this.passError = false;
            }

            if (this.userVal.trim() !== this.correctUser || this.passVal.trim() !== this.correctPass) { //empty or incorrect user info detected
                this.loginError = true;
                this.noErrors = false;
            } else {
                this.loginError = false;
                this.noErrors = true;
            }
        },

        toggleShow() {
            this.showPassword = !this.showPassword;
        }

    },

    computed: {
        buttonLabel() {
            return (this.showPassword) ? "Hide" : "Show";
        }
    }
}
</script>

<style>
#app {
    width: 100%;
    height: 100%;
    margin: 0px;
    padding-top: 80px;
    padding-bottom: 0px;
}

.content {
    width: 90%;
    height: 500px;
    max-width: 815px;
    min-width: 400px;
    margin: 0 auto;
    border-radius: 6px;
    overflow: hidden;
    background-color: white;
    display: flex;
}

.userInfo {
    margin-top: 7%;
    text-align: center;
}

.pics {
    width: 60%;
    height: auto;
}

.mainPic {
    width: 100%;
    height: 100%;
}

.userInputs {
    margin-top: 20px;
    font-size: 10px;
    text-align: center;
}

input {
    width: 60%;
    border-radius: 10px;
    border-width: 1px;
    height: 25px;
    margin-bottom: 10px;
    padding-left: 10px;
    padding-right: 10px;
    background-color: rgb(224, 240, 255);
}

.loginBtn {
    margin: 0 auto;
    margin-top: 15px;
    border: none;
    background-color: #146096;
    color: white;
    height: 30px;
    width: 200px;
    border-radius: 7px;
    font-size: 10px;
    font-weight: bold;
}

.foot {
    height: auto;
    width: 100%;
    padding: 0px;
    text-align: center;
    bottom: 0px;
    position: fixed;
}

.footerPic {
    height: 30px;
    width: auto;
    margin: 0px;
    padding: 0px;
}

.errors {
    color: red;
    font-size: 6px;
}

.success {
    color: rgb(6, 187, 6);
}

#lefties {
    margin-left: 14%;
    text-align: left;
}
</style>
