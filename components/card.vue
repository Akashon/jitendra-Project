<template>
    <div class="product-card product-card--layout--grid pb-2" style="width:18rem;">
        <!-- <div class="product-card__actions-list">
            <button class="product-card__action product-card__action--quickview" type="button" aria-label="Quick view">
                <i class="fa-solid fa-expand"></i>
            </button>

            <button class="product-card__action product-card__action--compare" type="button"
                aria-label="Add to compare">
                <i class="fa-solid fa-chart-simple" style="width: 16px ; height: 16px;"></i>
            </button>

        </div> -->
        <div class="product-card__image">
            <div class="product-card__image">
                <div class="image image--type--product">
                    <a :href="`/product/`" class="image__body">
                        <!-- <img class="image__tag" src="https://png.pngtree.com/png-vector/20230915/ourmid/pngtree-modern-white-chair-object-png-image_10076592.png" alt=""> -->
                        <img class="image__tag" :src="image" alt="Hello">
                    </a>
                </div>
            </div>

        </div>
        <div class="product-card__info">
            <div class="product-card__meta"><span class="product-card__meta-title">SKU:</span> 573-23743-C</div>
            <div class="product-card__name">
                <div><a href="product-full.html">{{ name }}</a></div>
            </div>
        </div>
        <div class="product-card__footer" style="display: flex; justify-content: center">
            <button class="product-card__addtocart-icon" type="button" aria-label="Add to cart">
                <i class="fa-solid fa-cart-shopping" style="width: 20px; height: 20px;"></i></button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    props: {
        id: {
            default: ''
        },
        image: {
            default: ''
        },
        name: {
            default: ""
        },
        rDescription: {
            default: ""
        },
    }
}
</script>
