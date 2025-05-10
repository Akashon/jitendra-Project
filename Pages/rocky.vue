<template>
    <div class="container py-4">
        <h2 class="mb-4">Home Page - Property Cards</h2>
        <div class="row">
            <div v-for="card in cards" :key="card.id" class="col-md-4 mb-4">
                <div class="card">
                    <img :src="card.image" class="card-img-top" alt="..." />
                    <div class="card-body">
                        <h5 class="card-title">{{ card.name }}</h5>
                        <p class="card-text">{{ card.description }}</p>
                        <!-- <button class="btn btn-outline-danger" @click="toggleWishlist(card.id)">
                            <i :class="['fa-heart', isWishlisted(card.id) ? 'fas' : 'far']"></i>
                        </button> -->
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
</script>