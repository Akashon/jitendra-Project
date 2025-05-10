<!-- <template>
    <div class="site__body my-5">
        <div class="block-header block-header--has-breadcrumb block-header--has-title">
            <div class="container pt-4">
                <div class="block-header__body">
                    <nav class="" style="background-color: transparent;" aria-label="breadcrumb">
                        <ol class="breadcrumb__list">
                            <li class="breadcrumb__spaceship-safe-area" role="presentation"></li>
                            <li class="breadcrumb__item breadcrumb__item--parent breadcrumb__item--first">
                                <a href="/" class="breadcrumb__item-link">Home</a>
                            </li>
                            <li class="breadcrumb__item breadcrumb__item--current breadcrumb__item--last"
                                aria-current="page">
                                <span class="breadcrumb__item-link">Current Page</span>
                            </li>
                            <li class="breadcrumb__title-safe-area" role="presentation"></li>
                        </ol>
                    </nav>
                    <h1 class="block-header__title">Wishlist</h1>
                </div>
            </div>
        </div>
        <div class="block">
            <div class="container container--max--xl">
                <div class="wishlist">
                    <table class="wishlist__table">
                        <thead class="wishlist__head">
                            <tr class="wishlist__row wishlist__row--head">
                                <th class="wishlist__column wishlist__column--head wishlist__column--image">Image</th>
                                <th class="wishlist__column wishlist__column--head wishlist__column--product">Product
                                </th>
                                <th class="wishlist__column wishlist__column--head wishlist__column--stock">Stock status
                                </th>
                                <th class="wishlist__column wishlist__column--head wishlist__column--button"></th>
                                <th class="wishlist__column wishlist__column--head wishlist__column--remove"></th>
                            </tr>
                        </thead>
                        <tbody class="wishlist__body">
                            <tr class="wishlist__row wishlist__row--body">
                                <td class="wishlist__column wishlist__column--body wishlist__column--image">
                                    <div class="image image--type--product"><a href="#" class="image__body"><img
                                                class="image__tag"
                                                src="https://m.media-amazon.com/images/I/41lgbKWcxPL._AC_UF350,350_QL50_.jpg"
                                                alt=""></a></div>
                                </td>
                                <td class="wishlist__column wishlist__column--body wishlist__column--product">
                                    <div class="wishlist__product-name" style="font-size: 18px; font-weight: 500;"><a
                                            href="#">Acrylic Polycarbonate</a></div>
                                    <div class="wishlist__product-rating">
                                        <div class="wishlist__product-rating-stars">
                                            <div class="rating">
                                                <div class="rating__body">
                                                    <div class="rating__star rating__star--active"></div>
                                                    <div class="rating__star rating__star--active"></div>
                                                    <div class="rating__star rating__star--active"></div>
                                                    <div class="rating__star rating__star--active"></div>
                                                    <div class="rating__star"></div>
                                                </div>
                                            </div>
                                        </div>
                                        <div class="wishlist__product-rating-title"
                                            style="font-size: 14px; font-weight: 500;">3 reviews</div>
                                    </div>
                                </td>
                                <td class="wishlist__column wishlist__column--body wishlist__column--stock">
                                    <div class="status-badge status-badge--style--success status-badge--has-text">
                                        <div class="status-badge__body" style="padding: 4px 8px;">
                                            <div class="status-badge__text" style="font-size: 16px;">In Stock</div>
                                        </div>
                                    </div>
                                </td>

                                <td class="wishlist__column wishlist__column--body wishlist__column--button"><button
                                        type="button" class="btn btn-sm btn-primary">Add to cart</button></td>
                                <td class="wishlist__column wishlist__column--body wishlist__column--remove"><button
                                        type="button" class="wishlist__remove btn btn-sm btn-muted btn-icon">
                                        <i class="fa fa-xmark"></i>
                                    </button></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
        <div class="block-space block-space--layout--before-footer"></div>
    </div>
</template> -->


<template>



    <div class="site__body my-5">
        <div class="block-header block-header--has-breadcrumb block-header--has-title">
            <div class="container pt-4">
                <div class="block-header__body">
                    <nav class="" style="background-color: transparent;" aria-label="breadcrumb">
                        <ol class="breadcrumb__list">
                            <li class="breadcrumb__spaceship-safe-area" role="presentation"></li>
                            <li class="breadcrumb__item breadcrumb__item--parent breadcrumb__item--first">
                                <a href="/" class="breadcrumb__item-link">Home</a>
                            </li>
                            <li class="breadcrumb__item breadcrumb__item--current breadcrumb__item--last"
                                aria-current="page">
                                <span class="breadcrumb__item-link">Current Page</span>
                            </li>
                            <li class="breadcrumb__title-safe-area" role="presentation"></li>
                        </ol>
                    </nav>
                    <h1 class="block-header__title">Wishlist</h1>
                </div>
            </div>
        </div>
        <div class="block">
            <div class="container container--max--xl">
                <div class="wishlist">
                    <table class="wishlist__table">
                        <thead class="wishlist__head">
                            <tr class="wishlist__row wishlist__row--head">
                                <th class="wishlist__column wishlist__column--head wishlist__column--image">Image</th>
                                <th class="wishlist__column wishlist__column--head wishlist__column--product">Product
                                </th>
                                <th class="wishlist__column wishlist__column--head wishlist__column--stock">Stock status
                                </th>
                                <th class="wishlist__column wishlist__column--head wishlist__column--button"></th>
                                <th class="wishlist__column wishlist__column--head wishlist__column--remove"></th>
                            </tr>
                        </thead>
                        <tbody class="wishlist__body" v-for="card in wishlistedCards" :key="card.id">
                            <tr class="wishlist__row wishlist__row--body gap-2">
                                <td class="wishlist__column wishlist__column--body wishlist__column--image">
                                    <div class="image image--type--product"><a href="#" class="image__body"><img
                                                class="image__tag"
                                                src="https://m.media-amazon.com/images/I/41lgbKWcxPL._AC_UF350,350_QL50_.jpg"
                                                alt=""></a></div>
                                </td>
                                <td class="wishlist__column wishlist__column--body wishlist__column--product">
                                    <div class="wishlist__product-name" style="font-size: 18px; font-weight: 500;"><a
                                            href="#">Acrylic Polycarbonate</a></div>
                                    <div class="wishlist__product-rating">
                                        <div class="wishlist__product-rating-stars">
                                            <div class="rating">
                                                <div class="rating__body">
                                                    <div class="rating__star rating__star--active"></div>
                                                    <div class="rating__star rating__star--active"></div>
                                                    <div class="rating__star rating__star--active"></div>
                                                    <div class="rating__star rating__star--active"></div>
                                                    <div class="rating__star"></div>
                                                </div>
                                            </div>
                                        </div>
                                        <div class="wishlist__product-rating-title"
                                            style="font-size: 14px; font-weight: 500;">3 reviews</div>
                                    </div>
                                </td>
                                <td class="wishlist__column wishlist__column--body wishlist__column--stock">
                                    <div class="status-badge status-badge--style--success status-badge--has-text">
                                        <div class="status-badge__body" style="padding: 4px 8px;">
                                            <div class="status-badge__text" style="font-size: 16px;">In Stock</div>
                                        </div>
                                    </div>
                                </td>

                                <td class="wishlist__column wishlist__column--body wishlist__column--button"><button
                                        type="button" class="btn btn-sm btn-primary">Add to cart</button></td>
                                <td class="wishlist__column wishlist__column--body wishlist__column--remove"
                                    @click="removeFromWishlist(card.id)"><button type="button"
                                        class="wishlist__remove btn btn-sm btn-muted btn-icon">
                                        <i class="fa fa-xmark"></i>
                                    </button></td>
                                <td><button class="btn btn-danger" @click="removeFromWishlist(card.id)">
                                        <i class="fas fa-heart"></i>
                                    </button></td>

                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
        <div class="block-space block-space--layout--before-footer"></div>
    </div>











    <div class="container py-4">
        <h2 class="mb-4">Wishlist</h2>
        <div class="row">
            <div v-for="card in wishlistedCards" :key="card.id" class="col-md-4 mb-4">
                <div class="card">
                    <img :src="card.image" class="card-img-top" alt="..." />
                    <div class="card-body">
                        <h5 class="card-title">{{ card.name }}</h5>
                        <p class="card-text">{{ card.description }}</p>
                        <button class="btn btn-danger" @click="removeFromWishlist(card.id)">
                            <i class="fas fa-heart-broken"></i> Remove from Wishlist
                        </button>
                    </div>
                </div>
            </div>
            <div v-if="wishlistedCards.length === 0" class="col-12">
                <p>No items in wishlist.</p>
            </div>
        </div>
        <router-link to="/rocky" class="btn btn-secondary mt-3">Back to Home</router-link>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const allCards = [
    { id: 1, name: 'Villa Elite', description: 'Luxury villa in Goa', image: 'https://via.placeholder.com/400x250?text=Villa+1' },
    { id: 2, name: 'Urban House', description: 'City view apartment', image: 'https://via.placeholder.com/400x250?text=Villa+2' },
    { id: 3, name: 'Beachside Home', description: 'Beachfront property', image: 'https://via.placeholder.com/400x250?text=Villa+3' },
    { id: 4, name: 'Mountain Cabin', description: 'Peaceful mountain retreat', image: 'https://via.placeholder.com/400x250?text=Villa+4' },
    { id: 5, name: 'Lake House', description: 'Lakefront property', image: 'https://via.placeholder.com/400x250?text=Villa+5' },
]

const wishlistedCards = ref([])

onMounted(() => {
    const wishlist = JSON.parse(localStorage.getItem('wishlist') || '[]')
    wishlistedCards.value = allCards.filter(card => wishlist.includes(card.id))
})

const removeFromWishlist = (id) => {
    let wishlist = JSON.parse(localStorage.getItem('wishlist') || '[]')
    wishlist = wishlist.filter(wishId => wishId !== id)
    localStorage.setItem('wishlist', JSON.stringify(wishlist))
    wishlistedCards.value = wishlistedCards.value.filter(card => card.id !== id)
}
</script>