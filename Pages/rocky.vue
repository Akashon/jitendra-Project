<!-- <template>
    <div class="container py-4">
        <h2 class="mb-4">Home Page - Property Cards</h2>
        <div class="row">
            <div v-for="card in cards" :key="card.id" class="col-md-4 mb-4">
                <div class="card">
                    <img :src="card.image" class="card-img-top" alt="..." />
                    <div class="card-body">
                        <h5 class="card-title">{{ card.name }}</h5>
                        <p class="card-text">{{ card.description }}</p>
                        <button class="btn btn-outline-danger" @click="toggleWishlist(card.id)">
                            <i :class="['fa-heart', isWishlisted(card.id) ? 'fas' : 'far']"></i>
                        </button>
                    </div>
                </div>
            </div>
        </div>
        <router-link to="/wishlist" class="btn btn-primary mt-3">Go to Wishlist</router-link>
    </div>
    <div class="container ">
        <ProductDetails/>
    </div>

</template>

<script setup>
import { ref, onMounted } from 'vue'

const cards = ref([
    { id: 1, name: 'Villa Elite', description: 'Luxury villa in Goa', image: 'https://via.placeholder.com/400x250?text=Villa+1' },
    { id: 2, name: 'Urban House', description: 'City view apartment', image: 'https://via.placeholder.com/400x250?text=Villa+2' },
    { id: 3, name: 'Beachside Home', description: 'Beachfront property', image: 'https://via.placeholder.com/400x250?text=Villa+3' },
    { id: 4, name: 'Mountain Cabin', description: 'Peaceful mountain retreat', image: 'https://via.placeholder.com/400x250?text=Villa+4' },
    { id: 5, name: 'Lake House', description: 'Lakefront property', image: 'https://via.placeholder.com/400x250?text=Villa+5' },
])

const wishlist = ref([])

onMounted(() => {
    wishlist.value = JSON.parse(localStorage.getItem('wishlist') || '[]')
})

const toggleWishlist = (id) => {
    const index = wishlist.value.indexOf(id)
    if (index === -1) {
        wishlist.value.push(id)
    } else {
        wishlist.value.splice(index, 1)
    }
    localStorage.setItem('wishlist', JSON.stringify(wishlist.value))
}

const isWishlisted = (id) => wishlist.value.includes(id)
</script> -->



<!-- <template>
  <div style="background-color: #fafafa">
    <div class="container py-5">
      <transition name="fade">
        <div v-if="error.has" class="alert alert-danger alert-dismissible fade show" role="alert">
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

      <div class="row my-lg-5 d-flex justify-content-center">
        <div class="col-md-8">
          <div class="card">
            <div class="card-body">
              <h1 class="card-title mb-4">Login</h1>

              <form class="py-3" @submit.prevent="doLogin" v-if="!isLoginSuccess">
                <div class="form-group">
                  <label for="signin-email">Email address</label>
                  <input v-model="email" id="signin-email" type="email" class="form-control py-3" placeholder="customer@example.com"
                    :class="{ 'is-invalid': validationErrors.email }" style="background-color: #ebebeb;" />
                  <div v-if="validationErrors.email" class="invalid-feedback">
                    {{ validationErrors.email }}
                  </div>
                </div>

                <div class="form-group">
                  <label style="font-size: 16px">Password</label>
                  <div class="input-group">
                    <input :type="showPassword ? 'text' : 'password'" v-model="password" class="form-control py-3"
                      placeholder="Password" style="background-color: #ebebeb;" :class="{ 'is-invalid': validationErrors.password }" />
                    <div class="input-group-append">
                      <button type="button" class="btn btn-outline-secondary" @click="showPassword = !showPassword" tabindex="-1">
                        <i :class="showPassword ? 'fas fa-eye-slash' : 'fas fa-eye'"></i>
                      </button>
                    </div>
                  </div>
                  <div v-if="validationErrors.password" class="invalid-feedback">
                    {{ validationErrors.password }}
                  </div>
                </div>

                <button type="submit" class="btn btn-danger mt-4 px-4" :disabled="loading">
                  <span v-if="loading" class="spinner-border spinner-border-sm mr-2"></span>
                  {{ loading ? 'Logging in...' : 'Login' }}
                </button>
              </form>

              <form class="py-3" v-if="isLoginSuccess" @submit.prevent="verifySecretKey">
                <div class="form-group">
                  <label for="secret-key">Secret Key</label>
                  <input v-model="secretKey" id="secret-key" type="text" class="form-control py-3"
                    placeholder="Your Secret Key" style="background-color: #ebebeb;"
                    :class="{ 'is-invalid': validationErrors.secretKey }" />
                  <div v-if="validationErrors.secretKey" class="invalid-feedback">
                    {{ validationErrors.secretKey }}
                  </div>
                </div>
                <button type="submit" class="btn btn-danger px-4" :disabled="loading">
                  <span v-if="loading" class="spinner-border spinner-border-sm mr-2"></span>
                  {{ loading ? 'Verifying...' : 'Submit' }}
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
      secretKey: '',
      loading: false,
      error: { has: false, message: '' },
      success: { has: false, message: '' },
      validationErrors: {
        email: '',
        password: '',
        secretKey: ''
      },
      isLoginSuccess: false, // Controls visibility of secret key input
    };
  },
  methods: {
    validateForm() {
      let isValid = true;
      this.validationErrors = { email: '', password: '', secretKey: '' };

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
          this.success = { has: true, message: 'Login successful. Please enter your secret key.' };
          localStorage.setItem("authToken", response.data.token);
          this.isLoginSuccess = true;
        } else {
          this.showError(response.data.message || 'Login failed. Please check your credentials.');
        }
      } catch (error) {
        this.showError(error.response?.data?.message || 'An error occurred during login.');
      } finally {
        this.loading = false;
      }
    },
    async verifySecretKey() {
      if (!this.secretKey) {
        this.validationErrors.secretKey = 'Secret Key is required.';
        return;
      }

      this.loading = true;
      this.error = { has: false, message: '' };
      this.success = { has: false, message: '' };

      try {
        const formData = new FormData();
        formData.append('secret_key', this.secretKey);

        const response = await axios.post(Url.verifySecretKey, formData, {
          headers: {
            Authorization: `Bearer ${localStorage.getItem('authToken')}`
          }
        });

        if (response.data.status) {
          this.success = { has: true, message: 'Secret key verified. Redirecting...' };
          localStorage.setItem("isLoggedIn", true);
          setTimeout(() => {
            window.location.href = "/";
          }, 1500);
        } else {
          this.showError(response.data.message || 'Invalid secret key.');
        }
      } catch (error) {
        this.showError(error.response?.data?.message || 'Error verifying secret key.');
      } finally {
        this.loading = false;
      }
    },
    showError(message) {
      this.error = { has: true, message };
      this.success = { has: false, message: '' };
      setTimeout(this.closeAlert, 5000);
    },
    closeAlert() {
      this.error.has = false;
      this.success.has = false;
    }
  }
};
</script> -->




<template>

    <!-- ADD TO CARD WISHLIST CODE DON'T REMOVE THIS  -->
    <div>
        <div class="container py-4">
            <h2 class="mb-4">Home Page - Property Cards</h2>
            <div class="row">
                <div v-for="card in cards" :key="card.id" class="col-md-4 mb-4">
                    <div class="card">
                        <img :src="card.image" class="card-img-top" alt="..." />
                        <div class="card-body">
                            <h5 class="card-title">{{ card.name }}</h5>
                            <p class="card-text">{{ card.description }}</p>
                            <button class="btn btn-outline-danger" @click="toggleWishlist(card.id)">
                                <i :class="['fa-heart', isWishlisted(card.id) ? 'fas' : 'far']"></i>
                            </button>
                        </div>
                    </div>
                </div>
            </div>
            <router-link to="/wishlist" class="btn btn-primary mt-3">Go to Wishlist</router-link>
        </div>
        <div class="container ">
            <ProductDetails />
        </div>
    </div>
    <!-- ADD TO CARD WISHLIST CODE DON'T REMOVE THIS  -->


    <!-- LOGIN CODE DON'T REMOVE THIS  -->
    <div style="background-color: #fafafa">
        <div class="container py-5">
            <!-- Alerts -->
            <transition name="fade">
                <div v-if="error.has" class="alert alert-danger alert-dismissible fade show" role="alert">
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

            <!-- Login Form -->
            <div class="row my-lg-5 d-flex justify-content-center">
                <div class="col-md-8">
                    <div class="card">
                        <div class="card-body">
                            <h1 class="card-title mb-4">Login</h1>
                            <!-- EMAIL/PASSWORD LOGIN FORM START  -->
                            <form class="py-3" @submit.prevent="doLogin" v-if="!isLoginSuccess">
                                <div class="form-group">
                                    <label>Email address</label>
                                    <input v-model="email" type="email" class="form-control py-3"
                                        placeholder="test@example.com" style="background-color: #ebebeb;"
                                        :class="{ 'is-invalid': validationErrors.email }" />
                                    <div v-if="validationErrors.email" class="invalid-feedback">
                                        {{ validationErrors.email }}
                                    </div>
                                </div>

                                <div class="form-group">
                                    <label>Password</label>
                                    <div class="input-group">
                                        <input :type="showPassword ? 'text' : 'password'" v-model="password"
                                            class="form-control py-3" placeholder="password123"
                                            style="background-color: #ebebeb;"
                                            :class="{ 'is-invalid': validationErrors.password }" />
                                        <div class="input-group-append">
                                            <button type="button" class="btn btn-outline-secondary"
                                                @click="showPassword = !showPassword">
                                                <i :class="showPassword ? 'fas fa-eye-slash' : 'fas fa-eye'"></i>
                                            </button>
                                        </div>
                                    </div>
                                    <div v-if="validationErrors.password" class="invalid-feedback">
                                        {{ validationErrors.password }}
                                    </div>
                                </div>

                                <button type="submit" class="btn btn-danger mt-4 px-4">
                                    {{ loading ? 'Logging in...' : 'Login' }}
                                </button>
                            </form>
                            <!-- EMAIL/PASSWORD LOGIN FORM START  -->

                            <!-- SECRET KEY FORM START -->
                            <form class="py-3" @submit.prevent="verifySecretKey" v-if="isLoginSuccess">
                                <div class="form-group">
                                    <label>Secret Key</label>
                                    <input v-model="secretKey" type="text" class="form-control py-3"
                                        placeholder="mysecret123" style="background-color: #ebebeb;"
                                        :class="{ 'is-invalid': validationErrors.secretKey }" />
                                    <div v-if="validationErrors.secretKey" class="invalid-feedback">
                                        {{ validationErrors.secretKey }}
                                    </div>
                                </div>

                                <button type="submit" class="btn btn-danger px-4">
                                    {{ loading ? 'Verifying...' : 'Submit' }}
                                </button>
                            </form>
                            <!-- SECRET KEY FORM END-->
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- LOGIN CODE DON'T REMOVE THIS  -->
</template>

<!-- ADD TO CARD WISHLIST CODE DON'T REMOVE THIS  -->
<script setup>
import { ref, onMounted } from 'vue'

const cards = ref([
    { id: 1, name: 'Villa Elite', description: 'Luxury villa in Goa', image: 'https://picsum.photos/id/1/200/100' },
    { id: 2, name: 'Urban House', description: 'City view apartment', image: 'https://picsum.photos/id/2/200/100' },
    { id: 3, name: 'Beachside Home', description: 'Beachfront property', image: 'https://picsum.photos/id/3/200/100' },
    { id: 4, name: 'Mountain Cabin', description: 'Peaceful mountain retreat', image: 'https://picsum.photos/id/4/200/100' },
    { id: 5, name: 'Lake House', description: 'Lakefront property', image: 'https://picsum.photos/id/5/200/100' },
])

const wishlist = ref([])

onMounted(() => {
    wishlist.value = JSON.parse(localStorage.getItem('wishlist') || '[]')
})

const toggleWishlist = (id) => {
    const index = wishlist.value.indexOf(id)
    if (index === -1) {
        wishlist.value.push(id)
    } else {
        wishlist.value.splice(index, 1)
    }
    localStorage.setItem('wishlist', JSON.stringify(wishlist.value))
}

const isWishlisted = (id) => wishlist.value.includes(id)
</script>
<!-- ADD TO CARD WISHLIST CODE DON'T REMOVE THIS  -->




<!-- THIS IS LOGIN CODE FOR A TESTING DON'T REMOVE THIS  -->
<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            secretKey: '',
            showPassword: false,
            loading: false,
            isLoginSuccess: false,
            error: { has: false, message: '' },
            success: { has: false, message: '' },
            validationErrors: {
                email: '',
                password: '',
                secretKey: ''
            }
        };
    },
    methods: {
        resetValidation() {
            this.validationErrors = { email: '', password: '', secretKey: '' };
        },
        closeAlert() {
            this.error.has = false;
            this.success.has = false;
        },
        doLogin() {
            this.resetValidation();
            this.loading = true;
            this.error.has = false;

            if (!this.email) this.validationErrors.email = 'Email is required.';
            if (!this.password) this.validationErrors.password = 'Password is required.';
            if (this.validationErrors.email || this.validationErrors.password) {
                this.loading = false;
                return;
            }

            if (this.email === 'test@example.com' && this.password === '123456') {
                this.success = { has: true, message: 'Login successful! Please enter your secret key.' };
                this.isLoginSuccess = true;
            } else {
                this.showError('Invalid email or password.');
            }

            this.loading = false;
        },
        verifySecretKey() {
            this.resetValidation();
            this.loading = true;

            if (!this.secretKey) {
                this.validationErrors.secretKey = 'Secret key is required.';
                this.loading = false;
                return;
            }

            if (this.secretKey === 'my1234') {
                this.success = { has: true, message: 'Login complete. Redirecting to home...' };
                setTimeout(() => {
                    window.location.href = '/';
                }, 1500);
            } else {
                this.showError('Invalid secret key.');
            }

            this.loading = false;
        },
        showError(message) {
            this.error = { has: true, message };
            this.success = { has: false, message: '' };
            setTimeout(this.closeAlert, 5000);
        }
    }
};
</script>
<!-- THIS IS LOGIN CODE FOR A TESTING DON'T REMOVE THIS  -->
