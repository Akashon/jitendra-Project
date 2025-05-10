<!-- <template>
  <div style="background-color: #fafafa">
    <div class="container py-5">
      <div class="row mt-lg-5 d-flex justify-content-center">
        <div class="py-0 col-md-8">
          <transition name="slide-fade">
            <div v-if="error.has || success.has" class="px-4 py-2 z-50">
              <div :class="{
                'alert alert-danger': error.has,
                'alert alert-success': success.has,
              }"
                class="max-w-screen-md mx-auto shadow-lg rounded-lg py-3 px-6 d-flex justify-content-between align-items-center">
                <div class="d-flex align-items-center">
                  <i :class="{
                    'fa fa-times-circle text-white': error.has,
                    'fa fa-check-circle text-white': success.has,
                  }" aria-hidden="true"></i>
                  <span class="ml-3 text-white">
                    {{ error.has ? error.message : success.message }}
                  </span>
                </div>
                <button @click="closeAlert" class="text-danger btn-close">
                  <i class="fa fa-times" aria-hidden="true"></i>
                </button>
              </div>
            </div>
          </transition>
        </div>
      </div>

      <div class="row my-lg-5 d-flex justify-content-center">
        <div class="col-md-8">
          <div class="card">
            <div class="card-body">
              <h1 class="card-title mb-4">Login</h1>

              <form class="py-3" @submit.prevent="doLogin">
                <div class="form-group">
                  <label for="signin-email" style="font-size: 16px">Email address</label>
                  <input v-model="email" id="signin-email" style="background-color: #ebebeb; font-size: 16px"
                    type="email" class="form-control py-3" placeholder="customer@example.com" />
                </div>
                <div class="form-group">
                  <label for="signin-password" style="font-size: 16px">Password</label>
                  <input v-model="password" id="signin-password" style="background-color: #ebebeb; font-size: 16px"
                    type="password" class="form-control" placeholder="Secret word" />
                </div>

                <button type="submit" class="btn btn-danger mt-3 px-4">Login</button>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import { Url } from '~/config/url'; // Assuming you have this in your project setup

export default {
  data() {
    return {
      email: '',
      password: '',
      error: { has: false, message: '', },
      success: { has: false, message: '', },
    };
  },
  methods: {
    async doLogin() {
      try {
        const formData = new FormData();
        formData.append('username', this.email);
        formData.append('password', this.password);
        const response = await axios.post(Url.userLogin, formData);
        console.log(458, response)
        if (response.data.status) {

          this.success = { has: true, message: response.data.message };
          this.error.has = false; // Clear error message
          localStorage.setItem("authToken", response.data.token);
          localStorage.setItem("isLoggedIn", true);

          window.location.href = "/";
        } else {
          this.showError(response.data.message || 'Login failed. Please check your credentials.');
        }

      } catch (error) {
        this.showError(error.response?.data?.message || 'An error occurred during login. Please try again.');
        this.error = true;
      }
    },
    showError(message) {
      this.error = { has: true, message };
      this.success.has = false; // Clear success message
    },
    showSuccess(message) {
      this.success = { has: true, message };
      this.error.has = false; // Clear error message
      this.autoCloseAlert();
    },
  },
  mounted() {
    // this.doLogin();
  }
};
</script>

<style scoped>
.container {
  max-width: 1000px;
}

.card {
  border: none;
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
  padding: 16px;
}

.card-title {
  font-weight: 500;
  font-size: 28px;
}

.alert-danger {
  background-color: rgb(255, 56, 56);
}

.alert-success {
  background-color: rgb(23, 124, 23);
}

.form-check-input {
  width: 16px;
  height: 16px;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style> -->




<template>
  <div style="background-color: #fafafa">
    <div class="container py-5">
      <!-- Alert Popup -->
      <!-- Alert Popup -->
      <div class="container">
        <transition name="fade">
          <div v-if="error.has" class="alert alert-danger alert-dismissible fade show" style="color: white;"
            role="alert">
            {{ error.message }}
            <button type="button" class="close" @click="closeAlert">&times;</button>
          </div>
        </transition>

        <transition name="fade">
          <div v-if="success.has" class="alert alert-success alert-dismissible fade show" role="alert">
            {{ success.message }}
            <button type="button" class="close" @click="closeAlert">&times;</button>
          </div>
        </transition>
      </div>


      <!-- Login Form -->
      <div class="row my-lg-5 d-flex justify-content-center">
        <div class="col-md-8">
          <div class="card">
            <div class="card-body">
              <h1 class="card-title mb-4">Login</h1>

              <form class="py-3" @submit.prevent="doLogin">
                <div class="form-group">
                  <label for="signin-email">Email address</label>
                  <input v-model="email" id="signin-email" type="email" style="background-color: #ebebeb;"
                    class="form-control py-3" placeholder="customer@example.com"
                    :class="{ 'is-invalid': validationErrors.email }" />
                  <div v-if="validationErrors.email" class="invalid-feedback">
                    {{ validationErrors.email }}
                  </div>
                </div>

                <div class="form-group">
                  <label style="font-size: 16px">Password</label>
                  <div class="input-group">
                    <input :type="showPassword ? 'text' : 'password'" style="background-color: #ebebeb; font-size: 16px"
                      v-model="password" class="form-control py-3" placeholder="Password"
                      :class="{ 'is-invalid': validationErrors.password }" />
                    <div class="input-group-append">
                      <button type="button" class="btn btn-outline-secondary" @click="showPassword = !showPassword"
                        tabindex="-1">
                        <i :class="showPassword ? 'fas fa-eye-slash' : 'fas fa-eye'"></i>
                      </button>
                    </div>
                  </div>
                  <div style=" right: 2px; " v-if="validationErrors.password" class="invalid-feedback"> {{
                    validationErrors.password }}</div>
                </div>
                <button type="submit" class="btn btn-danger mt-4 px-4" :disabled="loading">
                  <span v-if="loading" class="spinner-border spinner-border-sm mr-2"></span>
                  {{ loading ? 'Logging in...' : 'Login' }}
                </button>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import { Url } from '~/config/url';

export default {
  data() {
    return {
      email: '',
      password: '',
      showPassword: false,
      loading: false,
      error: { has: false, message: '' },
      success: { has: false, message: '' },
      validationErrors: {
        email: '',
        password: ''
      }

    };
  },
  methods: {
    validateForm() {
      let isValid = true;
      this.validationErrors = { email: '', password: '' };

      if (!this.email) {
        this.validationErrors.email = 'Email is required.';
        isValid = false;
      }

      if (!this.password) {
        this.validationErrors.password = 'Password is required.';
        isValid = false;
      }

      return isValid;
    },
    async doLogin() {
      if (!this.validateForm()) return;

      this.loading = true;
      this.error = { has: false, message: '' };
      this.success = { has: false, message: '' };

      try {
        const formData = new FormData();
        formData.append('username', this.email);
        formData.append('password', this.password);

        const response = await axios.post(Url.userLogin, formData);

        if (response.data.status) {
          this.success = { has: true, message: response.data.message };
          localStorage.setItem("authToken", response.data.token);
          localStorage.setItem("isLoggedIn", true);

          setTimeout(this.closeAlert, 3000);

          setTimeout(() => {
            window.location.href = "/";
          }, 1500);
        } else {
          this.showError(response.data.message || 'Login failed. Please check your credentials.');
        }
      } catch (error) {
        this.showError(error.response?.data?.message || 'An error occurred during login.');
      } finally {
        this.loading = false;
      }
    },
    showError(message) {
      this.error = { has: true, message };
      this.success = { has: false, message: '' };

      // Auto hide error message after 5s
      setTimeout(this.closeAlert, 5000);
    },
    closeAlert() {
      this.error.has = false;
      this.success.has = false;
    }
  }

};
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}


.container {
  max-width: 1000px;
}

.card {
  border: none;
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.1);
  padding: 16px;
}

.card-title {
  font-weight: 500;
  font-size: 28px;
}

.alert-danger {
  color: white;
  background-color: rgb(255, 56, 56);
}

.alert-success {
  color: white;
  background-color: rgb(23, 124, 23);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}

.is-invalid {
  border-color: #dc3545;
}

/* .invalid-feedback {
  display: block;
  font-size: 14px;
} */

.invalid-feedback {
  display: block;
  font-size: 0.9rem;
}
</style>
