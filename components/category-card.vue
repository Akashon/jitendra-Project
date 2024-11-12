<template>
    <div class="col-lg-3 col-md-6 col-sm-12 mb-4">
        <a href="/product/" class="card ">
            <img height="300" :src="image" class="image__tag" alt="Card Image">
            <div class="card-body">
                <h5 class="categories-list__item-name">{{ title }}</h5>
                <p class="categories-list__item-products">{{ totalItem }}</p>
            </div>
        </a>
    </div>
</template>
<script>

export default {
    data() {
        return {

        }
    },
    props: {
        image: {
            default: "https://5.imimg.com/data5/QY/QH/MB/SELLER-15512204/stainless-steel-storage-cabinet-500x500.jpg"
        },
        title: {
            default: "Acrylic Polycarbonate"
        },
        totalItem: {
            default: "20000"
        },
        link: {
            default: "/product/"
        }
    }
}

</script>
