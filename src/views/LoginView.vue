<template>
<div class="container-fluid ">
        <div class="row" style="padding-top:20em;">
            <div class="col-6">
                <div class="col-7 float-end pe-4">
                    <h2 class="text-white">Login</h2>
                        <div class="mb-3">
                            <input class="border-0 border-bottom col-12 py-3 bg-transparent text-white" v-model="model.account.username" placeholder="User name" name="username" style="outline: none;" required>
                        </div>
                        <div class="mb-3">
                            <input type="password" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" v-model="model.account.password" placeholder="Password" name="password" style="outline: none;" required>
                        </div>
                        <a class="text-decoration-danger fs-6 text-danger fw-light fst-italic" href="">Forget password???</a>
                        <button  @click="handleLogin" type="button" name="submit_btn" class="text-dark py-3 mt-3 col-12 border-0 bg-transparent login__button position-relative">
                            <div class="text-white">Login</div>
                        </button>
                </div>
            </div>

            <div class="col-6">

                <div class="col-7 ps-4">
                    <h2 class="text-white">New customer</h2>
                    <p class="mt-3 text-white">
                        With just a few simple steps to register, you will receive the following special benefits from Netflix:
                    </p>
                    <p class="mt-3 text-white">
                        - Book tickets conveniently and quickly.
                    </p>
                    <p class="mt-3 text-white">
                        - Receive information about hot movies and special promotions.
                    </p>
                    <RouterLink to="/register" class="mt-3 text-white">
                        <button class="text-dark py-3 mt-3 col-12 border-0 bg-transparent login__button position-relative">
                            <div class="text-white">Register</div>
                        </button>
                    </RouterLink>
                </div>

            </div>

        </div>
    </div>
</template>

<script>
import axios from 'axios'
    export default {
        name: 'LoginView',
        data() {
            return {
                model: {
                    account: {
                        username: '',
                        password: '',
                        role: '',
                        id: ''
                    }
                }
            }
        },
        methods: {
            handleLogin() {
                axios.post('https://localhost:7071/api/Account/login', this.model.account).then(response => {
                    if(response.data.role == 'Customer' ) {
                        console.log(response.data);
                        alert('Login successfully');
                        this.$router.push('/');
                        localStorage.setItem('token', response.data.token);
                        localStorage.setItem('role', response.data.role);
                        localStorage.setItem('id', response.data.id);
                    }
                }).catch(error => {
                    console.log(error);
                })
            },
            freshForm() {
                this.model.account.username = '';
                this.model.account.password = '';
            }
        }
    }
</script>

<style lang="scss" scoped>

</style>