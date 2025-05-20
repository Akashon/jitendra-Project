<template>
    <div class="site">
        <div class="site__body">
            <div class="block-space block-space--layout--after-header"></div>
            <div class="block">
                <div class="container container--max--xl">
                    <div class="row">
                        <DasSideMenu />
                        <div class="col-12 col-lg-9 mt-4 mt-lg-0">
                            <div class="card">
                                <div class="card-header" style="background-color: white;">
                                    <h5>Edit Profile</h5>
                                </div>
                                <div class="card-divider"></div>
                                <div class="card-body card-body--padding--2">
                                    <div class="row no-gutters">
                                        <div class="col-12 col-lg-7 col-xl-6">
                                            <div class="form-group">
                                                <label for="profile-first-name">First Name</label>
                                                <input v-model="firstName" type="text" class="form-control"
                                                    id="profile-first-name" placeholder="First Name" />
                                            </div>
                                            <div class="form-group">
                                                <label for="profile-last-name">Last Name</label>
                                                <input v-model="lastName" type="text" class="form-control"
                                                    id="profile-last-name" placeholder="Last Name" />
                                            </div>
                                            <div class="form-group">
                                                <label for="profile-email">Email Address</label>
                                                <input v-model="email" type="email" class="form-control"
                                                    id="profile-email" placeholder="Email Address" />
                                            </div>
                                            <div class="form-group">
                                                <label for="profile-phone">Phone Number</label>
                                                <input v-model="phone" type="text" class="form-control"
                                                    id="profile-phone" placeholder="Phone Number" />
                                            </div>
                                            <div class="form-group mb-0">
                                                <button @click="updateProfile" class="btn btn-danger mt-3 px-4"
                                                    :disabled="isLoading">
                                                    {{ isLoading ? 'Saving...' : 'Save' }}
                                                </button>
                                            </div>
                                            <div v-if="message" class="mt-3 alert"
                                                :class="{ 'alert-success': isSuccess, 'alert-danger': !isSuccess }">
                                                {{ message }}
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="block-space block-space--layout--before-footer"></div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
import { Url } from '~/config/url';

export default {
    data() {
        return {
            firstName: '',
            lastName: '',
            email: '',
            phone: '',
            isLoading: false,
            message: '',
            isSuccess: false,
            // validationErrors: {
            //     firstName: '',
            //     lastName: '',
            //     email: '',
            //     phone: '',
            // },
        };
    },
    methods: {

        // validateForm() {
        //     let isValid = true;
        //     this.validationErrors = { firstName: '', lastName: '', email: '', phone: '' };

        //     if (!this.firstName) {
        //         this.validationErrors.firstName = 'First Name is required.';
        //         isValid = false;
        //     }

        //     if (!this.lastName) {
        //         this.validationErrors.lastName = 'Last Name is required.';
        //         isValid = false;
        //     }

        //     if (!this.email) {
        //         this.validationErrors.email = 'Email is required.';
        //         isValid = false;
        //     }

        //     if (!this.phone) {
        //         this.validationErrors.phone = 'Last Name is required.';
        //         isValid = false;
        //     }

        //     return isValid;
        // },

        async fetchProfile() {
            try {
                const token = localStorage.getItem("authToken");
                const response = await axios.get(Url.fetchCustomerDetails, {
                    headers: { Authorization: "Bearer " + token }
                });

                const data = response.data.data;
                const fullName = data.c_fullname || '';
                const nameParts = fullName.split(' ');
                this.firstName = nameParts[0] || '';
                this.lastName = nameParts.slice(1).join(' ') || '';
                this.email = data.c_email || '';
                this.phone = data.c_mobile || '';
            } catch (error) {
                console.error("Error fetching profile:", error);
                this.message = "Failed to load profile details.";
                this.isSuccess = false;
            }
        },
        async updateProfile() {
            try {
                this.isLoading = true;
                this.message = '';
                const token = localStorage.getItem("authToken");
                const payload = {
                    c_fullname: `${this.firstName} ${this.lastName}`.trim(),
                    c_email: this.email,
                    c_mobile: this.phone,
                };

                const response = await axios.put(Url.updateCustomerDetails, payload, {
                    headers: { Authorization: "Bearer " + token }
                });

                this.message = "Profile updated successfully!";
                this.isSuccess = true;
            } catch (error) {
                console.error("Update failed:", error);
                this.message = "Something went wrong while updating profile.";
                this.isSuccess = false;
            } finally {
                this.isLoading = false;
            }
        },
    },
    mounted() {
        this.fetchProfile();
    }
};
</script>

<style scoped>
input.form-control {
    background-color: #ebebeb;
    font-size: 16px;
}
</style>




<!-- <template>
    <div class="site">
        <div class="site__body">
            <div class="block-space block-space--layout--after-header"></div>
            <div class="block">
                <div class="container container--max--xl">
                    <div class="row">
                        <DasSideMenu />
                        <div class="col-12 col-lg-9 mt-4 mt-lg-0">
                            <div class="card">
                                <div class="card-header" style="background-color: white;">
                                    <h5>Edit Profile (Static Data)</h5>
                                </div>
                                <div class="card-divider"></div>
                                <div class="card-body card-body--padding--2">
                                    <div class="row no-gutters">
                                        <div class="col-12 col-lg-7 col-xl-6">
                                            <div class="form-group">
                                                <label for="profile-first-name">First Name</label>
                                                <input v-model="firstName" type="text" class="form-control"
                                                    id="profile-first-name" placeholder="First Name" />
                                            </div>
                                            <div class="form-group">
                                                <label for="profile-last-name">Last Name</label>
                                                <input v-model="lastName" type="text" class="form-control"
                                                    id="profile-last-name" placeholder="Last Name" />
                                            </div>
                                            <div class="form-group">
                                                <label for="profile-email">Email Address</label>
                                                <input v-model="email" type="email" class="form-control"
                                                    id="profile-email" placeholder="Email Address" />
                                            </div>
                                            <div class="form-group">
                                                <label for="profile-phone">Phone Number</label>
                                                <input v-model="phone" type="text" class="form-control"
                                                    id="profile-phone" placeholder="Phone Number" />
                                            </div>
                                            <div class="form-group mb-0">
                                                <button @click="updateProfile" class="btn btn-danger mt-3 px-4">
                                                    Save
                                                </button>
                                            </div>
                                            <div v-if="message" class="mt-3 alert"
                                                :class="{ 'alert-success': isSuccess, 'alert-danger': !isSuccess }">
                                                {{ message }}
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="block-space block-space--layout--before-footer"></div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            firstName: 'John',
            lastName: 'Doe',
            email: 'john.doe@example.com',
            phone: '9876543210',
            message: '',
            isSuccess: false,
        };
    },
    methods: {
        updateProfile() {
            // Simulate update
            this.message = "Profile updated successfully (simulated)!";
            this.isSuccess = true;

            console.log("Updated Profile Data:", {
                firstName: this.firstName,
                lastName: this.lastName,
                email: this.email,
                phone: this.phone,
            });
        },
    },
};
</script>

<style scoped>
input.form-control {
    background-color: #ebebeb;
    font-size: 16px;
}
</style> -->
