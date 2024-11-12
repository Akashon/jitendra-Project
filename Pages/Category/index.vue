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
                    <h1 class="block-header__title">Product Categories</h1>
                </div>
            </div>
        </div>
        <div class="block block-split">
            <div class="container mt-5">
                <div class="row">
                    <CategoryCard/>

                </div>
            </div>
        </div>
    </div>
    <!-- site__body / end -->
</template>

<script>
import CategoryCard from '~/components/category-card.vue';
</script>
