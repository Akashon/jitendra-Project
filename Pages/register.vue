<!-- <template>
    <div style="background-color: #fafafa">
        <div class="container">
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
                            <h1 class="card-title mb-4">Register</h1>

                            <form class="py-3" @submit.prevent="doLogin">
                                <div class="form-group">
                                    <label for="signin-email" style="font-size: 16px">User Name</label>
                                    <input v-model="email" id="signin-email"
                                        style="background-color: #ebebeb; font-size: 16px" type="email"
                                        class="form-control py-3" placeholder="customer@example.com" />
                                </div>
                                <div class="form-group">
                                    <label for="signin-email" style="font-size: 16px">Email address</label>
                                    <input v-model="email" id="signin-email"
                                        style="background-color: #ebebeb; font-size: 16px" type="email"
                                        class="form-control py-3" placeholder="customer@example.com" />
                                </div>
                                <div class="form-group">
                                    <label for="signin-email" style="font-size: 16px">Company Name</label>
                                    <input v-model="email" id="signin-email"
                                        style="background-color: #ebebeb; font-size: 16px" type="email"
                                        class="form-control py-3" placeholder="customer@example.com" />
                                </div>
                                <div class="form-group">
                                    <label for="signin-password" style="font-size: 16px">Plant Name</label>
                                    <input v-model="password" id="signin-password"
                                        style="background-color: #ebebeb; font-size: 16px" type="password"
                                        class="form-control" placeholder="Secret word" />
                                </div>
                                <div class="form-group">
                                    <label for="signin-password" style="font-size: 16px">Password</label>
                                    <input v-model="password" id="signin-password"
                                        style="background-color: #ebebeb; font-size: 16px" type="password"
                                        class="form-control" placeholder="Secret word" />
                                </div>

                                <button type="submit" class="btn btn-danger mt-3 px-4">Register</button>
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
            <div class="row mt-lg-5 d-flex justify-content-center">
                <div class="py-0 col-md-8">
                    <div class="container">
                        <transition name="fade">
                            <div v-if="error.has" class="alert alert-danger alert-dismissible fade show"
                                style="color: white;" role="alert">
                                {{ error.message }}
                                <button type="button" class="close" @click="closeAlert">&times;</button>
                            </div>
                        </transition>

                        <transition name="fade">
                            <div v-if="success.has" class="alert alert-success alert-dismissible fade show"
                                role="alert">
                                {{ success.message }}
                                <button type="button" class="close" @click="closeAlert">&times;</button>
                            </div>
                        </transition>
                    </div>
                </div>
            </div>

            <div class="row my-lg-5 d-flex justify-content-center">
                <div class="col-md-8">
                    <div class="card">
                        <div class="card-body">
                            <h1 class="card-title mb-4">Register</h1>

                            <form class="py-3" @submit.prevent="doRegister">
                                <div class="form-group">
                                    <label style="font-size: 16px">User Name</label>
                                    <input style="background-color: #ebebeb; font-size: 16px" v-model="username"
                                        type="text" class="form-control py-3" placeholder="Your Name"
                                        :class="{ 'is-invalid': errors.username }" />
                                    <div class="invalid-feedback">{{ errors.username }}</div>
                                </div>

                                <div class="form-group">
                                    <label style="font-size: 16px">Email address</label>
                                    <input style="background-color: #ebebeb; font-size: 16px" v-model="email"
                                        type="email" class="form-control py-3" placeholder="customer@example.com"
                                        :class="{ 'is-invalid': errors.email }" />
                                    <div class="invalid-feedback">{{ errors.email }}</div>
                                </div>

                                <div class="form-group">
                                    <label style="font-size: 16px">Company Name</label>
                                    <input style="background-color: #ebebeb; font-size: 16px" v-model="company"
                                        type="text" class="form-control py-3" placeholder="Company"
                                        :class="{ 'is-invalid': errors.company }" />
                                    <div class="invalid-feedback">{{ errors.company }}</div>
                                </div>

                                <div class="form-group">
                                    <label style="font-size: 16px">Plant Name</label>
                                    <input style="background-color: #ebebeb; font-size: 16px" v-model="plant"
                                        type="text" class="form-control py-3" placeholder="Plant"
                                        :class="{ 'is-invalid': errors.plant }" />
                                    <div class="invalid-feedback">{{ errors.plant }}</div>
                                </div>

                                <div class="form-group">
                                    <label style="font-size: 16px">Password</label>
                                    <div class="input-group">
                                        <input :type="showPassword ? 'text' : 'password'"
                                            style="background-color: #ebebeb; font-size: 16px" v-model="password"
                                            class="form-control py-3" placeholder="Password"
                                            :class="{ 'is-invalid': errors.password }" />
                                        <div class="input-group-append">
                                            <button type="button" class="btn btn-outline-secondary"
                                                @click="togglePassword" tabindex="-1">
                                                <i :class="showPassword ? 'fas fa-eye-slash' : 'fas fa-eye'"></i>
                                            </button>
                                        </div>
                                    </div>
                                    <div class="invalid-feedback">{{ errors.password }}</div>
                                </div>


                                <button type="submit" class="btn btn-danger mt-4 px-4" :disabled="loading">
                                    <span v-if="loading" class="spinner-border spinner-border-sm mr-2"></span>
                                    {{ loading ? 'Register...' : 'Register' }}
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
            username: '',
            email: '',
            company: '',
            plant: '',
            password: '',
            errors: {},
            error: { has: false, message: '' },
            success: { has: false, message: '' },
            loading: false,
            showPassword: false,

        };
    },
    methods: {
        async doRegister() {
            this.clearMessages();

            if (!this.validateForm()) return;

            this.loading = true;

            try {
                const formData = new FormData();
                formData.append('username', this.username);
                formData.append('email', this.email);
                formData.append('company', this.company);
                formData.append('plant', this.plant);
                formData.append('password', this.password);

                const response = await axios.post(Url.userRegister, formData);

                if (response.data.status) {
                    this.success = { has: true, message: 'Registration successful!' };
                    localStorage.setItem("authToken", response.data.token);
                    localStorage.setItem("isLoggedIn", true);

                    setTimeout(this.closeAlert, 3000);
                    setTimeout(() => (window.location.href = "/"), 1500);
                } else {
                    this.showError(response.data.message || 'Registration failed.');
                }
            } catch (err) {
                this.showError(err.response?.data?.message || 'An error occurred.');
            } finally {
                this.loading = false; // ✅ Stop loading after API call
            }
        },


        validateForm() {
            this.errors = {};
            let valid = true;

            if (!this.username) {
                this.errors.username = "User name is required.";
                valid = false;
            }
            if (!this.email) {
                this.errors.email = "Email is required.";
                valid = false;
            }
            if (!this.company) {
                this.errors.company = "Company name is required.";
                valid = false;
            }
            if (!this.plant) {
                this.errors.plant = "Plant name is required.";
                valid = false;
            }
            if (!this.password) {
                this.errors.password = "Password is required.";
                valid = false;
            }

            return valid;
        },

        clearMessages() {
            this.success = { has: false, message: '' };
            this.error = { has: false, message: '' };
        },

        showError(message) {
            this.error = { has: true, message };
            this.success = { has: false, message: '' };
        },

        closeAlert() {
            this.error.has = false;
            this.success.has = false;
        },
        togglePassword() {
            this.showPassword = !this.showPassword;
        }

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

.invalid-feedback {
    display: block;
    font-size: 0.9rem;
}

input.is-invalid {
    border-color: #dc3545;
}
</style>