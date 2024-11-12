<template>
  <div style="background-color: #fafafa">
    <div class="container py-5">
      <div class="row mt-lg-5 d-flex justify-content-center">
        <div class="col-md-8">
          <transition name="slide-fade">
            <div v-if="alertMessage" class="alert" :class="alertClass" role="alert">
              <div class="d-flex justify-content-between align-items-center">
                <span>{{ alertMessage }}</span>
                <button @click="closeAlert" type="button" class="close">
                  <span aria-hidden="true">&times;</span>
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
              <form @submit.prevent="doLogin">
                <div class="form-group">
                  <label for="signin-email" style="font-size: 18px">Email address</label>
                  <input
                    v-model="email"
                    id="signin-email"
                    type="email"
                    class="form-control py-3"
                    placeholder="customer@example.com"
                    required
                  />
                </div>
                <div class="form-group">
                  <label for="signin-password" style="font-size: 18px">Password</label>
                  <input
                    v-model="password"
                    id="signin-password"
                    type="password"
                    class="form-control"
                    placeholder="Secret word"
                    required
                  />
                </div>
                <button type="submit" class="btn btn-primary mt-3">Login</button>
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

export default {
  data() {
    return {
      email: '',
      password: '',
      alertMessage: '',
      alertClass: ''
    };
  },
  methods: {
    async doLogin() {
      try {
        const response = await axios.post('https://advanceengineerings.com/web/customer/login', {
          email: this.email,
          password: this.password
        });
        console.log(487, response);
        if (response.data.success) {
          this.alertClass = 'alert-success';
          this.alertMessage = 'Login successful!';
          // Handle successful login (e.g., redirect, store token, etc.)
        } else {
          this.alertClass = 'alert-danger';
          this.alertMessage = response.data.message || 'Login failed!';
        }
      } catch (error) {
        this.alertClass = 'alert-danger';
        if (error.response && error.response.status === 404) {
          this.alertMessage = 'Error 404: API endpoint not found.';
        } else {
          this.alertMessage = 'An error occurred during login. Please try again.';
        }
      }
    },
    closeAlert() {
      this.alertMessage = '';
    }
  }
};
</script>

<style scoped>
.alert {
  margin-bottom: 1rem;
}
</style>
