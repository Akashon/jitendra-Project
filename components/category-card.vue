<template>
    <div class="col-lg-4 col-md-6 col-sm-12 mb-4">
        <a href="/product/" class="card ">
            <img height="300" :src="image" class="image__tag" alt="Card Image">
            <div class="card-body">
                <h5 class="categories-list__item-name">{{ title }}</h5>
                <!-- <p class="categories-list__item-products">{{ totalItem }}</p> -->
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
        id: {
            default: "",
        },
        name: {
            default: "",
        },
        image: {
            default: "",
        },
    }
}

</script>
