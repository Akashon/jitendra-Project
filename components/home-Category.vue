<template>
    <!-- <li class="card col-6 col-md-4 col-lg-2"> -->
        <a href="#" class=" text-center card-item " style="position: relative; display: block; padding: 12px 28px; 
					 display: block;text-decoration: none; color: #333;">
            <img width="60" :src="image" alt="" class="img-fluid gray-image">
            <span class="item-name">{{ name }}</span>
        </a>
    <!-- </li> -->
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
        image: {
            default: ""
        },
        name: {
            default: ""
        },
    }
}
</script>