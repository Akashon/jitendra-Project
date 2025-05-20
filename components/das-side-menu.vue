<!-- <template>
    <div class="col-12 col-lg-3 d-flex">
        <div class="account-nav flex-grow-1">
            <h4 class="account-nav__title">Navigation</h4>
            <ul class="account-nav__list">
                <li class="account-nav__item account-nav__item--active"><a href="/dashboard">Dashboard</a>
                </li>
                <li class="account-nav__item"><a href="/dashboard/order">Order History</a></li>
                <li class="account-nav__item"><a href="/dashboard/order-detail">Order Details</a></li>
                <li class="account-nav__item"><a href="/dashboard/address">Addresses</a></li>
                <li class="account-nav__item"><a href="#">Edit Address</a></li>
                <li class="account-nav__item"><a href="/dashboard/edit-profile">Edit Profile</a></li>
                <li class="account-nav__divider" role="#"></li>
                <li class="account-nav__item"><a href="#">Logout</a></li>
            </ul>
        </div>
    </div>
</template> -->



<template>
    <div class="col-12 col-lg-3 d-flex">
        <div class="account-nav flex-grow-1">
            <h4 class="account-nav__title">Navigation</h4>
            <ul class="account-nav__list">
                <li v-for="item in navItems" :key="item.path"
                    :class="['account-nav__item', { 'account-nav__item--active': isActive(item.path) }]">
                    <router-link :to="item.path" class="text-decoration-none text-dark">
                        {{ item.label }}
                    </router-link>
                </li>
                <li class="account-nav__divider my-2" role="separator"></li>
                <li class="account-nav__item">
                    <a href="#" class="text-decoration-none text-dark" @click.prevent="logout">Logout</a>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
import { useRoute, useRouter } from 'vue-router'

export default {
    name: 'AccountSidebar',

    data() {
        return {
            navItems: [
                { label: 'Dashboard', path: '/dashboard' },
                { label: 'Order History', path: '/dashboard/order' },
                { label: 'Order Details', path: '/dashboard/order-detail' },
                { label: 'Edit Profile', path: '/dashboard/edit-profile' },
                { label: 'Password', path: '/dashboard/password' },
            ]
        }
    },

    computed: {
        currentPath() {
            return this.$route.path
        }
    },

    methods: {
        isActive(path) {
            return this.currentPath === path
        },
        logout() {
            console.log('Logging out...')
            this.$router.push('/')
        }
    },

    mounted() {
        console.log('Sidebar component mounted.')
    }
}
</script>


<style scoped>
.account-nav__item {
    padding: 0.2rem 0;
}

.account-nav__item--active {
    font-weight: bold;
    color: #DB2C1D;
    /* Bootstrap primary color */
}

.account-nav__item--active a {
    color: #DB2C1D !important;
}

.account-nav__divider {
    border-top: 1px solid #dee2e6;
}
</style>
