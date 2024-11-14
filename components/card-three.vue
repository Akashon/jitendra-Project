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
                    <a :href="`/product/${id}/`" class="image__body">
                        <img class="image__tag" :src="image" alt="">
                    </a>
                </div>
            </div>

        </div>
        <div class="product-card__info">
            <div class="product-card__meta"><span class="product-card__meta-title">SKU:</span> 573-23743-C</div>
            <div class="product-card__name">
                <div><a :href="`/product/${id}/`">{{ name }}</a>
                </div>
            </div>

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
        id: { default: '' },
        image: { default: '' },
        name: { default: "" },
        rDescription: { default: "" },
    }
}
</script>