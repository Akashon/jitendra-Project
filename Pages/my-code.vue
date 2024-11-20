<template>
  <div class="container mt-4">
    <div class="row">
      <!-- Product Images -->
      <div class="col-md-6">
        <div id="product-carousel" class="carousel slide" data-ride="carousel">
          <div class="carousel-inner">
            <div
              v-for="(image, index) in images"
              :key="index"
              :class="['carousel-item', { active: index === 0 }]"
            >
              <img :src="image.small" class="d-block w-100" :alt="image.alt" />
            </div>
          </div>
          <a
            class="carousel-control-prev"
            href="#product-carousel"
            role="button"
            data-slide="prev"
          >
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="sr-only">Previous</span>
          </a>
          <a
            class="carousel-control-next"
            href="#product-carousel"
            role="button"
            data-slide="next"
          >
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="sr-only">Next</span>
          </a>
        </div>
      </div>

      <!-- Product Details -->
      <div class="col-md-6">
        <h3>{{ name }}</h3>
        <p>{{ description }}</p>
        <div>
          <button @click="decrementQuantity" class="btn btn-secondary">-</button>
          <span class="mx-3">{{ quantity }}</span>
          <button @click="incrementQuantity" class="btn btn-secondary">+</button>
        </div>
        <button @click="addToCart" class="btn btn-primary mt-3">Add to Cart</button>
      </div>
    </div>
    <!-- Additional Information -->
    <div class="row mt-4">
      <div class="col-12">
        <ul class="nav nav-tabs">
          <li class="nav-item">
            <a
              class="nav-link"
              :class="{ active: activeTab === 'description' }"
              @click="activeTab = 'description'"
              href="#"
              >Description</a
            >
          </li>
          <li class="nav-item">
            <a
              class="nav-link"
              :class="{ active: activeTab === 'details' }"
              @click="activeTab = 'details'"
              href="#"
              >Details</a
            >
          </li>
        </ul>
        <div class="tab-content mt-3">
          <div v-if="activeTab === 'description'">
            <p>{{ description }}</p>
          </div>
          <div v-else>
            <ul>
              <li>Brand: {{ brand }}</li>
              <li>Material: {{ material }}</li>
              <li>Country: {{ country }}</li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { Url } from "~/config/url";

export default {
  props: {
    id: { default: "" },
    name: { default: "" },
    description: { default: "" },
    brand: { default: "" },
    material: { default: "" },
    country: { default: "" },
  },
  data() {
    return {
      quantity: 1,
      images: [
        {
          small:
            "https://png.pngtree.com/png-vector/20240203/ourmid/pngtree-steel-cabinet-furniture-wooden-with-separate-storage-drawers-on-a-white-png-image_11593718.png",
          alt: "Product Image 1",
        },
        {
          small:
            "https://png.pngtree.com/png-vector/20231006/ourmid/pngtree-versatile-steel-cabinet-ideal-for-factories-schools-gyms-png-image_10079349.png",
          alt: "Product Image 2",
        },
      ],
      activeTab: "description",
    };
  },
  methods: {
    incrementQuantity() {
      this.quantity++;
    },
    decrementQuantity() {
      if (this.quantity > 1) this.quantity--;
    },
    async addToCart() {
      const token = localStorage.getItem("authToken");
      const productId = this.$route.params.id || this.id;

      try {
        const response = await axios.get(
          `${Url.fetchCustomerAddToCart}?id=${productId}&proId=${productId}`,
          {
            headers: {
                    "Authorization": "Bearer " + token
                    },
          }
        );
        console.log("Add to Cart Response:", response);
      } catch (error) {
        console.error("Error adding to cart:", error.response?.data || error.message);
      }
    },
  },
};
</script>

<style>
.carousel-item img {
  height: 400px;
  object-fit: cover;
}
</style>
