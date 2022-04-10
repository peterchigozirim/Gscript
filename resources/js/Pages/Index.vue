<template>
    <div class="h-screen bg-white transition-all duration-500 grid grid-cols-3" >
        <div class="bg-white z-50 min-h-full"></div>
        <div>
            <div class="h-full mt-[100px] flex flex-col items-center space-y-6">
                <div class="text-center flex-col flex space-y-4 items-center border border-gray-300 rounded-lg w-11/12 py-12 px-8 min-h-[65vh]">
                    <tittle></tittle>
                    <welcome-tittle v-if="nextPage == 'password'" @click="back"></welcome-tittle>
                    <sub-tittle v-if="nextPage == 'email'"></sub-tittle>
                    <email-tittle v-else></email-tittle>

                    <div class="flex transition-all duration-500">
                        <!-- <div class="space-y-10 transition-all duration-500 " :class="nextPage == 'email' ? 'ml-0 ' : '-ml-[50rem] '">
                            <div class="relative transition-all space-y-2 duration-1000">
                                <div class="rounded z-20 transition-all duration-1000" :class="border? 'border-2 border-blue-500' : 'border-2 border-gray-300'">
                                    <input
                                        ref="input"
                                        class="h-12 w-80 border-0 focus:ring-0 focus:outline-none focus:border-0" @focus="checkFocus" type="text" v-model="form.email"
                                    >
                                    <div class="absolute px-1 bg-white z-10  font-semibold" :class="border? '-top-3 left-2 text-sm text-blue-700/80' :' top-3 left-3 text-gray-600'">
                                        <p>
                                            Email or phone
                                        </p>
                                    </div>
                                </div>
                                <div class="text-left font-semibold">
                                    <Link class="text-[#1a73e8]">
                                        Forget email?
                                    </Link>
                                </div>
                            </div>
                            <learn-more></learn-more>

                            <div class="flex justify-between">
                                <create-account></create-account>

                                <div @click="next" class="bg-blue-600 hover:bg-blue-700/95 text-gray-50 hover:shadow-lg rounded px-6 py-1 cursor-pointer">
                                    <p>Next</p>
                                </div>
                            </div>
                        </div> -->
                        <div class="space-y-10 mt-10" :class="nextPage == 'password'? 'ml-0' : 'mr-96'">
                            <div class="relative transition-all duration-1000 space-y-3">
                                <div class="rounded z-20 transition-all duration-1000" :class="border? 'border-2 border-blue-500' : 'border border-gray-300'">
                                    <input
                                        v-if="fieldType == 'text'"
                                        ref="input"
                                        class="h-12 w-80 border-0 focus:ring-0 px-2 focus:outline-none focus:border-0" @focus="checkFocus" type="text" v-model="form.password"
                                    >
                                    <input
                                        v-if="fieldType == 'password'"
                                        ref="input"
                                        class="h-12 w-80 border-0 focus:ring-0 px-2 focus:outline-none focus:border-0" @focus="checkFocus" type="password" v-model="form.password"
                                    >
                                    <div class="absolute px-1 bg-white z-10  font-semibold" :class="border? '-top-3 left-2 text-sm text-blue-700/80' :' top-3 left-3 text-gray-600'">
                                        <p>
                                            Password
                                        </p>
                                    </div>
                                </div>
                                <div class="text-left space-x-4 flex">
                                    <div class="rounded-full  flex justify-center items-center -mt-1 w-8 h-8" :class="fieldType == 'password'? 'hover:bg-blue-100' : 'hover:bg-gray-200'">
                                        <input type="checkbox" @click="showPass" class="border-2 border-black/60 checked:bg-blue-800 after:outline-none after:ring-0 checked:ring-0 checked:border-2 checked:border-black/60" id="">
                                    </div>
                                    <label for="show">Show password</label>
                                </div>
                            </div>
                            <learn-more></learn-more>

                            <div class="flex justify-between">
                                <forget-password></forget-password>

                                <div @click="next" class="bg-blue-600 hover:bg-blue-700/95 text-white hover:shadow-lg rounded px-6 py-1 cursor-pointer">
                                    <p>Sign in</p>
                                </div>
                            </div>
                        </div>
                        
                    </div>
                </div>
                <div class="flex justify-between text-sm w-11/12 items-center">
                    <div class="-ml-3">
                        <select name="" id="" class="ring-0 text-xs w-48 border-0 outline-none focus:outline-none focus:right-0 focus:border-0">
                            <option value="">English (United Kingdom)</option>
                        </select>
                    </div>
                    <footer-div></footer-div>
                </div>
            </div>
        </div>
        <div class="bg-white z-10"></div>
    </div>
</template>

<script>
import { defineComponent } from 'vue'
import { Head, Link } from '@inertiajs/inertia-vue3';
import InputDiv from './Component/InputDiv.vue'
import SubTittle from './Component/SubTittle.vue'
import Tittle from './Component/Tittle.vue'
import { onMounted, ref } from 'vue';
import LearnMore from './Component/LearnMore.vue';
import CreateAccount from './Component/CreateAccount.vue';
import FooterDiv from './Component/FooterDiv.vue';
import WelcomeTittle from './Component/WelcomeTittle.vue';
import EmailTittle from './Component/EmailTittle.vue';
import ForgetPassword from './Component/ForgetPassword.vue';
export default defineComponent({
  components: { Tittle, SubTittle, InputDiv, Head, Link, LearnMore, CreateAccount, FooterDiv, WelcomeTittle, EmailTittle, ForgetPassword },
    data(){
        return{
            form: this.$inertia.form({
                email: '',
                password: '',
                remember: false,
                
            }),
            border: false,
            nextPage: "password",
            fieldType: "password"
        }
    },

    methods:{
        checkFocus(){
            
            if (this.border == false) {
                this.border = true
            }else{
                this.border = false
            }

        },
        disableAll(){
            if (this.border == true) {
                this.border = false
            }
        },
        next(){
            if (this.nextPage == 'email') {
                this.nextPage = 'password'
            }else{

            }
        },
        back(){
            if (this.nextPage == 'password') {
                this.nextPage == 'email'
            }
        },
        showPass(){
            if (this.fieldType == "password") {
                this.fieldType = "text"
            }else{
                this.fieldType = "password"
            }
        }

    },
    
})
</script>

<style>

</style>