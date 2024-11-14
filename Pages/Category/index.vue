<template>
    <div class="site__body py-5">
        <div class="block-header block-header--has-breadcrumb block-header--has-title">
            <div class="container">
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
                    <h1 class="block-header__title">All Categories</h1>

                    <div class="block block-brands">
                        <div class="container lpx-0 px-4">
                            <ul class="block-brands__list row justify-content-start " style="border: none;">
                                <li class="card col-6 col-md-4 col-lg-2" v-for="(category, index) in categories"
                                    :key="(category, index)">
                                    <HomeCategory :id="category.cat_id" :name="category.cat_name"
                                        :image="category.cat_image" />
                                </li>
                                <li class="block-brands__divider" role="presentation"></li>

                            </ul>
                        </div>
                    </div>
                    <h1 class="block-header__title">Categories (Name)</h1>
                </div>
            </div>
        </div>

        <div class="block block-split">
            <div class="container mt-5">
                <div class="row">
                    <div class="col-lg-8 col-md-6 col-sm-12 mb-4">
                        <CategoryCard />
                    </div>
                </div>
            </div>
        </div>
    </div>
    <!-- site__body / end -->

</template>

<script>
import { Url } from '~/config/url';
import axios from 'axios';
import CategoryCard from '~/components/category-card.vue';
export default {
    data() {
        return {

            categories: [],
            featureds: [],

        };
    },
    methods: {

        async fetchCategory() {
            const response = await axios.get(Url.fetchHomeCategory);
            console.log(48, response);
            this.categories = response.data.categoryArray;

            // this.categories = response.data.categoryArray;

            // console.log(458, response.data.productArray);
            // if (response.data.productArray) {

            // 	// console.log(485255, JSON.parse(response.data.productArray[0].p_media)[0]);
            // 	this.featureds = response.data.productArray;

            // 	console.log(this.featureds[0].p_image);

            // }
        },




    },
    mounted() {
        this.fetchCategory();
    },

}


</script>
