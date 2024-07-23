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
            <div class="mb-3 d-flex align-items-center">
              <input v-model="customer.email" type="email" class="border-0 border-bottom flex-grow-1 py-3 bg-transparent text-white" placeholder="Email" name="email" style="outline: none;" required>
              <button type="button" v-if="!isOtpSent && customer.email" class="otp-button ms-2" @click="sendOtp" >Send OTP</button>
              <span v-if="isOtpSent && !isOtpVerified" class="ms-2 text-light">{{ countdown }}s</span>
            </div>
            <div v-if="isOtpSent && !isOtpVerified" class="mb-3 d-flex align-items-center">
              <label for="otp" class="text-secondary me-2">Enter OTP:</label>
              <input type="text" v-model="otp" class="border-0 border-bottom flex-grow-1 py-3 bg-transparent text-white" style="outline: none;" required />
              <button type="button" class="otp-button ms-2" @click="verifyOtp">Verify OTP</button>
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
        rePassword: '',
        otp: '',
        StringEncrypted: '',
        isOtpSent: false,
        isOtpVerified: false,
        countdown: 0,
        countdownInterval: null
      };
    },
    methods: {
      validateEmail(email) {
        const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return re.test(email);
      },
      validatePhoneNumber(phoneNumber) {
        const re = /^\d{10,15}$/;
        return re.test(phoneNumber);
      },
      validatePassword(password) {
        const re = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[^\da-zA-Z]).{8,15}$/;
        return re.test(password);
      },
      sendOtp() {
        if (!this.validateEmail(this.customer.email)) {
          alert('Invalid email format');
          return;
        }
        axios.post('https://localhost:7071/api/Email/GenerateEmailOtp?to='+ this.customer.email )
          .then(response => {
            if (response.status === 200) {
              this.StringEncrypted = response.data;
              this.isOtpSent = true;
              this.countdown = 60;
              this.startCountdown();
              alert('OTP sent to your email');
            }
          })
          .catch(error => {
            console.error('Error sending OTP:', error.response.data);
            alert('Failed to send OTP');
          });
      },
      verifyOtp() {
        if (!this.otp) {
          alert('Please enter OTP');
          return;
        }
        axios.post('https://localhost:7071/api/Email/VerifyEmailOtp', { otp: this.otp, stringEncrypted: this.StringEncrypted })
          .then(response => {
            if (response.status === 200) {
              this.isOtpVerified = true;
              clearInterval(this.countdownInterval);
              alert('OTP verified successfully');
            }
          })
          .catch(error => {
            console.error('Error verifying OTP:', error.response.data);
            alert('Invalid OTP');
          });
        // if (this.otp === this.StringEncrypted) {
        //   this.isOtpVerified = true;
        //   alert('OTP verified successfully');
        // } else {
        //   alert('Invalid OTP');
        // }
      },
      handleRegister() {
        if (!this.customer.username || !this.customer.name || !this.customer.DOB || !this.customer.email || !this.customer.address || !this.customer.phoneNumber || !this.customer.passwordHash || !this.rePassword) {
          alert('All fields are required');
          return;
        }
        if (!this.validateEmail(this.customer.email)) {
          alert('Invalid email format');
          return;
        }
        if (!this.validatePhoneNumber(this.customer.phoneNumber)) {
          alert('Invalid phone number');
          return;
        }
        if (!this.validatePassword(this.customer.passwordHash)) {
          alert('Password must contain at least one lowercase letter, one uppercase letter, one digit, one special character, and be 8-15 characters long.');
          return;
        }
        if (this.customer.passwordHash !== this.rePassword) {
          alert('Passwords do not match');
          return;
        }
        if (!this.isOtpVerified) {
          alert('Please verify the OTP sent to your email');
          return;
        }
        console.log('Registering:', this.customer);
        axios.post('https://localhost:7071/api/Customers/registration', this.customer)
          .then(response => {
            if (response.status === 200) {
              alert('Registration successful');
              this.$router.push('/login'); 
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
      },
      startCountdown() {
        this.countdownInterval = setInterval(() => {
          if (this.countdown > 0) {
            this.countdown--;
          } else {
            clearInterval(this.countdownInterval);
            this.isOtpSent = false;
          }
        }, 1000);
      }
    },
    beforeDestroy() {
      clearInterval(this.countdownInterval);
    }
  };
  </script>
  
  <style scoped>
.otp-button {
  background-color: transparent;
  color: white;
  border: 1px solid white;
  padding: 10px 20px;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s;
}

/* .otp-button:disabled {
  background-color: #6c757d;
  cursor: not-allowed;
}

.otp-button:hover:enabled {
  background-color: #0056b3;
} */

.otp-button:hover {
  background-color: #b30000;
}

.d-flex {
  display: flex;
}

.align-items-center {
  align-items: center;
}

.flex-grow-1 {
  flex-grow: 1;
}

.ms-2 {
  margin-left: 0.5rem;
}

.me-2 {
  margin-right: 0.5rem;
}

.countdown-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 12px;
}
</style>
  