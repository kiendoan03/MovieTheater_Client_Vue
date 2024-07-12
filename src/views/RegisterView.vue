<template>
    <div class="container-fluid">
      <div class="row mb-5" style="padding-top: 7em;">
        <div class="col-6 mx-auto">
          <h2 class="text-light text-center">Register</h2>
          <form @submit.prevent="handleRegister">
            <div class="mb-3">
              <input v-model="customer.username" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="User name" name="username" style="outline: none;" required>
            </div>
            <div class="mb-3">
              <input v-model="customer.name" type="text" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="Full name" name="name" style="outline: none;" required>
            </div>
            <div class="mb-3">
              <label for="dob" class="text-secondary">Date of birth</label>
              <input v-model="customer.DOB" type="date" class="border-0 border-bottom col-12 py-3 bg-transparent text-light" placeholder="Date of birth" name="dob" style="outline: none;" required>
            </div>
            <div class="mb-3">
              <input v-model="customer.email" type="email" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="Email" name="email" style="outline: none;" required>
            </div>
            <div class="mb-3">
              <input v-model="customer.address" type="text" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="Address" name="address" style="outline: none;" required>
            </div>
            <div class="mb-3">
              <input v-model="customer.phoneNumber" type="text" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="Phonenumber" name="phoneNumber" style="outline: none;" required>
            </div>
            <div class="mb-3">
              <input v-model="customer.passwordHash" type="password" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="Password" name="passwordHash" style="outline: none;" required>
            </div>
            <div class="mb-3">
              <input v-model="rePassword" type="password" class="border-0 border-bottom col-12 py-3 bg-transparent text-white" placeholder="Re-password" name="re_password" style="outline: none;" required>
            </div>
            <button type="submit" class="mb-2 text-dark py-3 mt-3 col-12 border-0 bg-transparent login__button position-relative">
              <div class="text-light fs-5">Register</div>
            </button>
            <router-link class="text-decoration-danger fs-6 text-danger fw-light fst-italic" to="/login">Already have an account?</router-link>
          </form>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import { useRouter } from 'vue-router';
  
  export default {
    name: 'RegisterView',
    data() {
      return {
        customer: {
          id: 0,
          name: '',
          username: '',
          image: '',
          role: '',
          token: '',
          DOB: '',
          email: '',
          address: '',
          phoneNumber: '',
          passwordHash: ''
        },
        rePassword: ''
      };
    },
    methods: {
      handleRegister() {
        if (this.customer.passwordHash !== this.rePassword) {
          alert('Passwords do not match');
          return;
        }
        console.log('Registering:', this.customer);
        // Gửi dữ liệu đăng ký lên server
        axios.post('https://localhost:7071/api/Customers/registration', this.customer)
          .then(response => {
            if (response.status === 200) {
              alert('Registration successful');
              this.$router.push('/login'); // Chuyển hướng đến trang đăng nhập sau khi đăng ký thành công
            }
          })
          .catch(error => {
            console.error('Error during registration:', error.response.data);
            if (error.response && error.response.data && error.response.data.errors) {
              alert('Registration failed: ' + JSON.stringify(error.response.data.errors));
            } else {
              alert('Registration failed');
            }
          });
      }
    }
  };
  </script>
  
  <style scoped>
  /* Thêm các style tùy chỉnh của bạn ở đây */
  </style>
  